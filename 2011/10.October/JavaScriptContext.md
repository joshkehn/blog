{"title":"Understanding JavaScript Context", "date":1319144091000}
++++++++++
<noscript>
    <p class="info">
        This post contains various [gist's][gist link] in order to show code content in an easy to use manner. Your browser appears incapable of rendering these.
    </p>
</noscript>
JavaScript's [functional scoping][fn scope] makes the language incredibly fun and flexible. You can seamlessly adopt almost any paradigm with ease. It does come with one caveat: confusion over `this`. Because only functions create scope, and because the context in which functions execute is mutable, what `this` actually points to is confusing at first.

Let's take a simple Java class.

<script src="https://gist.github.com/1302383.js"> </script>

Using this template we can create a new student and print out the relevant information.

    Student me = new Student("Joshua", 26);
    System.out.println(me);

In these methods, `this` refers to the instance of `Student` that we created. `this.name` is `"Joshua"` and `this.age` is `26`. The function is always executed against the current object. `this` is a predictable known quantity. Coming from this background JavaScript's flexibility in regard to `this` and function context comes as a shock.

Let's take a quick example.

<script src="https://gist.github.com/1302384.js"> </script>

Looks standard enough, right? The prototype is extended to add a function that interacts with the base object, and existing variables are used to add functionality. Straight forward non-async JavaScript will rarely have an issue with scope. Asynchronous code will *often* have scope issues.

Extending this example to add an asynchronous call to a hypothetical remote service checking a minimum drinking age.

<script src="https://gist.github.com/1302387.js"> </script>

The potential issue is on `fn(this.age`. Here `this` will not be pointing to the `Student` object like many expect. Instead it points to the global context. Here is a slightly different method that allows us to specify the context.

<script src="https://gist.github.com/1302393.js"> </script>

Here's what's happening. First the `drinking_age` function has lost the `age` parameter and been modified to look in the current context for it instead (`this.age`). Then when invoking `Laws.drinking_age` we are using `.call`, one of the three scope-changing functions inherent in all [Function][fn mdn] objects.

* `.bind(this, [, arg1, arg2, ...argN])`
* `.apply(this[, arguments])`
* `.call(this[, arg1, arg2, ...argN])`

Each of these has a distinct role in adjusting the function context. `.bind` returns a new function with new context. `.apply` will execute a function in a context with an optional array to expand into arguments. `.call` executes a function in a context with individual arguments.

Using this structure, we can even manipulate the contexts of anonymous functions on the fly to persist current scope without messy `var self = this;` statements.

    jQuery('.messages').hide(250, messages.cleared.bind(this));

Understanding scope is fundamental to an enjoyable experience writing JavaScript.

[gist link]: https://gist.github.com/
[fn scope]: https://developer.mozilla.org/en/JavaScript/Reference/Functions_and_function_scope
[fn mdn]: https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Function