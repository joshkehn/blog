{"title":"Deferring Events in JavaScript", "date":1316540725000}
++++++++++
Deferring events in JavaScript is a common practice. Due to the event-driven nature of many client side applications and the asynchronous nature of many server side applications with [Node.js][node] you often will queue events up to be executed at a later time. Most start with a similar pattern.

    var deferred = [];
    page.on('load', function () {
      deferred.forEach(function (fn) {
        fn();
      });
    });

    deferred.push(function create_html () {
      page.append('<div id="login_box"></div>');
    });

    deferred.push(function delay_login() {
      setTimeout(function () {
        $('#loginbox').fadeIn(250);
      }, 1200);
    });
    
    deferred.push(function say_ready () {
      alert('Ready!');
    });

This works in a pinch, but the there are a few problems.

1. Deferred functions are called synchronously. This will block execution.
2. Functions are not given any context and any original context is lost.
3. Deferred functions are not executed if the event is already thrown.
4. This pattern must be repeated for any case where functions need to be deferred.

Solving problem #1 is relatively easy. Wrap the function execution in a block that is asynchronous. 

    deferred.forEach(function (fn) {
      setTimeout(fn, 0);
    });

Note that you can substitute `setTimeout` for `process.nextTick` when working server side in Node.js.

Problem #2 is a bit trickier. It requires the use of [`.bind()`][mdc: bind] and saving the initial context. To save the initial context create another variable and set it to `this` once the event has been thrown;

    var deferred = [], context;
    page.on('load', function () {
      context = this;
      // ...

The `.bind` call creates a new function that when called executes the original function in the context provided. This behavior can be seen with a quick demo.

    function context_check () { console.log(this); }
    context_check();
      // => window
    context_check.bind({name : 'Josh'})();
      // => { name : 'Josh' }
    context_check.bind(function () { return 'Kehn'; })();
      // => [Function]

A slight adjustment to the `setTimeout` call includes the `.bind(context)`.

	setTimeout(fn.bind(context), 0);

Next is #3. Only when an event is called do the deferred functions execute. If an event that only occurs once, like a `window.onload` event, only functions deferred up to that point will be run. Any functions deferred after the event is emitted are lost. Checking if the event has been thrown and short circuiting to the deferred function if it has means the `deferred.push` needs to be abstracted away.

    _defer = function (fn) {
      if (context) {
        fn.bind(context)();
      } else {
        deferred.push(fn);
      }
    });

All `deferred.push` calls now become `_defer` calls. 

    _defer(function say_ready () {
      alert('Ready');
    });

Having resolved the first three issues #4 is the only one left. Making this a repeatable pattern and generalizing the implementation for general use. The full piece is too long to put here, so I put everything into a GitHub repository called [Defer.js][defer github].

[node]: http://nodejs.org/
[mdc: bind]: https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Function/bind
[defer github]: https://github.com/joshkehn/defer.js