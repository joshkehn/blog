{"title":"One-shot Getters & Setters", "date":1314668689000}
++++++++++  
The last hour was spent [exhaust coding](http://twitter.com/#!/joshkehn/status/108343700886786048) some broadcast message bits with [socket.io](http://socket.io/). In the middle of this I wrote a small function that reassignes itself after it is called; a one-shot setter.

Expanding slightly on this a little bit I wrote two generic [gists](https://gist.github.com/) demonstrating this in getter and setter fashion.

### Getter Example

Here we simply replace the function with another function that returns the initially given value.

<script src="https://gist.github.com/1179929.js"></script>

### Setter Example

The setter example is a bit more complex. In order to correctly scope the passed function we create a copy of it, substituting the current context.

This context can even be altered externally by binding `this`, ala `error.bind(context)(handler);`. 

<script src="https://gist.github.com/1179927.js"></script>