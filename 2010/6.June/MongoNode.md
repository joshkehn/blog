{"title":"MongoDB & Node.js", "date":1277175922000}
++++++++++
I've been playing with [MongoDB](http://www.mongodb.org/) and [node.js](http://nodejs.org/) recently. This is a brief summary of what they are / aim to be. I feel that MongoDB and Node.js have a bright future ahead in the realm of web based applications and real time colliding. Particularly of interest is the decision to use JavaScript engines at the core of both. MongoDB uses SpiderMonkey and Node.js uses Google's V8.

### Mongo
![Mongo Logo](http://img375.imageshack.us/img375/942/logomongodb.png)

Mongo is part of the large [NoSQL](http://en.wikipedia.org/wiki/NoSQL) movement sweeping the web community.

> NoSQL is a movement promoting a
> loosely defined class of
> non-relational data stores that break
> with a long history of relational
> databases. These data stores may not
> require fixed table schemas, usually
> avoid join  operations and typically
> scale horizontally. Academics and
> papers typically refer to these
> databases as structured storage.

<cite>From [NoSQL‚ Wikipedia](http://en.wikipedia.org/wiki/NoSQL)</cite>

MongoDB is a designed to be a scalable, high performance database. It is **not** designed for situations where strict formats need to be applied. It supports [atomic inserts](http://en.wikipedia.org/wiki/ACID) which makes it highly suited for real time data aggregates. It has support for standard [indexes](http://www.mongodb.org/display/DOCS/Indexes), [sharding](http://www.mongodb.org/display/DOCS/Sharding+Introduction), and even commercial support. It models itself after the idea that databases are specializing and you can't create something to please everyone. It uses the [JSON](http://www.json.org/) document data model to provide cross service support easily and *fast*. By removing transactional semantics from standard database design you strip most of the "fat" from traditional SQL processes. This comes at a cost however, you can't create foreign keys or constrain the data like you can in SQL. Systems modeled after transactional systems (think banking or corporate records) won't be efficient in Mongo as they are in other systems.

### node.js
![node.js logo](http://img444.imageshack.us/img444/4214/logodk.png)

[node.js](http://nodejs.org/) is described as an evented I/O for the [V8 JavaScript engine](http://code.google.com/p/v8/).

> Node's goal is to provide an easy way
> to build scalable network programs. In
> the "hello world" web server example
> above, many client connections can be
> handled concurrently. Node tells the
> operating system (through epoll,
> kqueue, /dev/poll, or select) that it
> should be notified when a new
> connection is made, and then it goes
> to sleep. If someone new connects,
> then it executes the callback. Each
> connection is only a small heap
> allocation.

Node has some really cool stuff going on under the hood. I haven't had enough of a chance to play with it, though I did create a small server for a project I'm working on. Requests dropped from ~40ms to <10ms consistently, no matter how many times I hit it up with requests.