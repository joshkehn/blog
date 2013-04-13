{"title": "Writing Better JavaScript","date": 1291990322000}
++++++++++
[JavaScript](http://en.wikipedia.org/wiki/JavaScript) has exploded as a programming language in recent times. From using it in [Appcelerator](http://joshuakehn.com/blog/view/7/Appcelerator-and-the-iPad) to build platform independent applications to fully dependable services like [MongoDB and Node.js](http://joshuakehn.com/blog/view/12/MongoDB-Node-js), JavaScript is seeing a large increase in more then [just the browser](http://joshuakehn.com/blog/view/2/WebSocket-Tutorial-with-Node-js).

How do you write better JavaScript code? Several things come to mind.

### Keep It Local

JavaScript has something called *implicit global scope*. Failure to prefix variable declarations with `var` will lead to a globally available variable. How does this impact your code? Polluting the global scope can cause many issues, chief among them is interference with other JavaScript libraries, specifically those that are poorly written and have scope issues. If you roll all your own JavaScript then it is doubtful you will see immediate issues, however, the errors and unexpected behavior that can arise from this is difficult to debug. It is much easier to simply keep in the current scope in mind and use `var`.

### Use A Library

Web browsers use different JavaScript engines. Firefox uses [SpiderMonkey](http://en.wikipedia.org/wiki/SpiderMonkey_%28JavaScript_engine%29) (with the improvements of TraceMonkey in 3.5 and JägerMonkey in the 4 betas), Safari uses [Nitro](http://www.apple.com/safari/features.html), Google's Chrome and open source varient Chromium both use [V8](http://en.wikipedia.org/wiki/V8_%28JavaScript_engine%29). Internet Explorer is due out with a dedicated JavaScript engine in IE9. These different engines have different sets of standard browser implementations. Using a JavaScript library like [jQuery](http://jquery.com/) can often improve development time and lessen the amount of cross browser issues you encounter. 

### Be Consistent

It's better to be consistently wrong then haphazardly right. There are nuances of JavaScript that are often either unknown or overlooked that can lead to issues. Use a quality checker (I recommend [JSLint](http://www.jslint.com/)) to ensure that all your code is consistent with the framing "good practices" of JavaScript.

### Namespace

Java developers will often write company or library specific packages for easy import and use in other applications. `com.itzik.utils` and the like. The *exact same thing* can be done in JavaScript and it highly recommended. If you're writing a library or designing a reusable set of objects, put them into a namespace object. This way everything is centralized and the global scope is polluted as little as possible. [Unobtrusive JavaScript](http://en.wikipedia.org/wiki/Unobtrusive_JavaScript) is the approach you are aiming for.