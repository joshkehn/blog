{"title": "WebSocket Tutorial with Node.js","date": 1285163303000}
++++++++++
> *Note this is a re-write of an earlier post that got lost due to data corruption.*

[WebSockets](http://en.wikipedia.org/wiki/WebSockets) *were* part of the HTML5 [draft specifications](http://dev.w3.org/html5/spec/Overview.html) but have since been moved into their own section. Currently supported by Google [Chrome][1], Apple [Safari][2], and [Firefox 4.0][3] (beta). Support for IE is not forthcoming, which leaves about 70% of the browsers in the dark. WebSockets provide some amazing opportunities for development, especially when working with live / streaming data. What do we do?

<!--moar-->

Introduce the [Flash Socket][4]. Flash Sockets are native socket connections. They have a few limitations (must have flash, flash policy file) but they are well worth it to ensure that the majority of people have access to your application. Currently this is supported in IE 8+, FF 3+, and Chrome, as well as any browser that supports native WebSockets. I've also had good success with Safari, but the goal here was IE support, which we now have. 

### What you will need

Starting from the client side and progressing to the server:

 * Node.js (more below)
 * [web-socket-js](http://github.com/gimite/web-socket-js/) (client side Flash Sockets)
 * [node-websocket-server](http://github.com/miksago/node-websocket-server) (Node WebSocket implementation)
 * Flash policy file server (I will explain how to make this)
 * Something to server the HTML page, as you can't use a `file:///` URI with Flash Sockets.

### Node.js

[Node.js](http://nodejs.org/) is a evented I/O framework built around Google's [V8 JavaScript Engine](http://code.google.com/p/v8/). You can download it from the [ry / node git repository](http://github.com/ry/node). Installing is pretty simple on most Linux / Unix systems. I've tested this under Ubuntu 10.04 and Mac OS X 10.6.x;

<script src="https://gist.github.com/cdec8b6134869355f1cd.js"></script>

Expect the configure to go quickly, and the install to take upwards of six to eight minutes. After this you would be able to run `node --version` and receive the version string. If not, I refer you to Node's [Google Group](http://groups.google.com/group/nodejs) for help installing Node. **Do not proceed until you have Node installed.**

### Build

We will be building a very basic application that sends messages spaced one second apart containing the current date to the web page. While the practical applications for this are limited, it is a simple, yet effective, introduction and proof-of-concept. The concept here being that WebSockets are available cross browser and easy to develop.

### Client

The client side is particularly easy. There are three files you need to include, `swfobject.js`, `FABridge.js`, and `web`_`socket.js`. Then you need to write a short `script` section that will set the swf location.

<script src="https://gist.github.com/8871f9791dd58c233256.js"></script>

After that is done we can setup our WebSocket code and handlers. 

<script src="https://gist.github.com/1127715.js"></script>

Define the output function.

<script src="https://gist.github.com/1127718.js"></script>

And the rest of the HTML page.

<script src="https://gist.github.com/1127720.js"></script>

### Server
    
Now we move on to the server side of things. I use Node.js and a really good [websocket implementation](http://github.com/miksago/node-websocket-server), however there are implementations for [Ruby](http://github.com/gimite/web-socket-ruby), [Python](http://popdevelop.com/2010/03/a-minimal-python-websocket-server/), and even [PHP](http://code.google.com/p/phpwebsocket/). 

#### Flash Policy

Remember that [Flash Policy File](http://www.lightsphere.com/dev/articles/flash_socket_policy.html) I mentioned earlier? Yep, have to implement it. Flash attempts to ensure security by checking two places, port 843 and the destination port. It's always good to run a separate Flash Policy Server because Flash player will *by default* attempt for three seconds on port 843 before moving on. This **will** delay your WebSocket by three seconds.

The Flash Policy Server (also node) is pretty basic. 

<script src="https://gist.github.com/1127722.js"></script>

`domains` is a paired array of domains and ports. The above will allow any connecting domain to connect to any port as a socket. If you desire more security, you can limit to your own domain and a specific port.

<script src="https://gist.github.com/1127725.js"></script>

The Flash Policy server binds to a low port (843) so you will have run it under [`sudo`](http://en.wikipedia.org/wiki/Sudo) or root.

<script src="https://gist.github.com/1127726.js"></script>

Ensure that you have a "Flash server listening" log line before continuing. After you have that setup you can work on the actual server side code.

#### Node.js

Server side isn't much more difficult, in fact it could be easier to understand then the client. 

<script src="https://gist.github.com/1127728.js"></script>

Then how we handle WebSocket connections

<script src="https://gist.github.com/1127730.js"></script>

We are going to add a message listener even though we aren't using that here.

<script src="https://gist.github.com/1127734.js"></script>

Setup an interval (1000 msec = 1 second) to send the date.

<script src="https://gist.github.com/1127737.js"></script>

Closing clears the interval and broadcasts a message saying so.

<script src="https://gist.github.com/1127739.js"></script>

Finally, listen to port 40132. Port number was pulled out of a hat.

    server.listen(40132);
    
That wraps this up, if anything is confusing drop me a comment and I'll see what I can do to clear it up.

I have this "live" under [joshuakehn.com/socketexample](http://joshuakehn.com/socketexample/) if you want to see it. You can also access this "shell style" with the following handshake:

    GET /echo HTTP/1.1
    Host: localhost
    Connection: Upgrade
    Upgrade: WebSocket

This will be answered with 

    HTTP/1.1 101 Web Socket Protocol Handshake
    Upgrade: WebSocket
    Connection: Upgrade
    WebSocket-Origin: undefined
    WebSocket-Location: ws://joshuakehn.com/echo
    WebSocket-Protocol: *

And follow with a list of times. Terminal output isn't pretty, but you get the gist of it. 

  [1]: http://www.google.com/chrome "Chrome is Google's build of Chromium (open source)"
  [2]: http://www.apple.com/safari/ "Apple's WebKit based browser."
  [3]: http://www.mozilla.com/en-US/firefox/all-beta.html "Yep, still in beta"
  [4]: http://www.adobe.com/livedocs/flex/2/langref/flash/net/Socket.html