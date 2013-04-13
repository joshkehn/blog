{"title":"Diagnosis: No Cancer", "date":1317606210000}
++++++++++

Ted Dziuba wrote a piece yesterday entitled [Node.js is Cancer][node cancer].

He contests that because a shitty Fibonacci number generator performs poorly Node.js is worthless. I contend that shitty Fibonacci generators are shitty in whatever language or framework.

For shits and giggles I decided to compare his JavaScript implementation with an exact PHP replica and as close as I could get with a Python implementation. If I find myself with a spot of free time later in the week I'll dummy up some C code.

**Note:** The Fibonacci number generator is incorrect. It should be `n <= 2` rather then `n < 2`. I left it as Ted implemented to keep any comparison equivalent.

### JavaScript Code:
An exact copy of Ted's original JavaScript code, with the minor change of actually working. You cannot call `res.end` with a number, it must be a String, Array, or Buffer.

<script src="https://gist.github.com/1258318.js"> </script>

### PHP Code:
Exact port of the JavaScript Fibonacci number generator paired with a simple echo. Because PHP is run under Apache it doesn't need any HTTP serving libs.

<script src="https://gist.github.com/1258315.js"> </script>

### Python Code:
Exact port of the Fibonacci number generator paired with SocketServer and SimpleHTTPServer. I'm not as knowledgeable about Python's HTTP libraries so if there is a better one let me know.

<script src="https://gist.github.com/1258347.js"> </script>

### Results:

The results really speak for themselves. It hardly matters that the implementation is inefficient. The close to the wire Node implementation soundly trounces the PHP and Python versions.

Node.js performed the best at 3.942 seconds.

    josh$ time curl http://localhost:1337/
    165580141
    real    0m3.942s
    user    0m0.004s
    sys     0m0.004s

PHP was the worst, taking almost a minute and a half to complete.

    josh$ time curl http://localhost:8888/fibserver.php
    Number is: 165580141
    real    1m22.709s
    user    0m0.004s
    sys     0m0.005s

The Python implementation was in the middle, but far closer in time at 49.223 seconds to the PHP implementation then the Node.js one.

    josh$ time curl http://localhost:1339/
    165580141
    real    0m49.223s
    user    0m0.002s
    sys     0m0.003s

The ab results for [JavaScript][ab js] implementation is available as well. I couldn't run against the PHP or Python implementations, coming up with the following error instead:

    apr_poll: The timeout specified has expired (70007)

I would love to hear from Ted what the "correct" way to write a web server to reply with on-the-fly generated Fibonacci numbers is.

[node cancer]: http://teddziuba.com/2011/10/node-js-is-cancer.html
[ab js]: https://gist.github.com/1258324