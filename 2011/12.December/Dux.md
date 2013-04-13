{"title":"Dux Released", "date":1324321506649}
++++++++++

I decided that [dux][joshkehn/dux] was good enough to publish. Go check it out.

### Basic Usage

At it's core dux is a flexible container that accepts drop in functionality that can be executed from a common command line interface. Adding new commands or extending others is straight forward and simple. This is a very different mindset from build oriented tools like [jake][jcoglan/jake] or [ant][ant]. These tools focus on files, directories, and processing. dux is a simple command line utility that wraps logging and option parsing so it can be extended by other commands. 

Let's start off with a very simple example of how to use dux. 

    var dux = require('dux');

    dux.commands.add('say', function () {
        dux.logger.info('Saying ' + this.args.join(' '));
    });

    dux.start();

Executing this command is as simple as throwing it at as an argument.

    $ node example.js say Hello World!
    info:     Welcome to Dux
    info:     It works if it ends with Dux ok
    info:     Executing command path say Hello World!
    info:     Saying Hello World!
    info:     Dux ok

You can add a [shebang][wiki/shebang] to the top of the file and give it executable permissions to clean up the execution.

    $ ./example.js say Hello World!
    info:     Welcome to Dux
    info:     It works if it ends with Dux ok
    info:     Executing command path say Hello World!
    info:     Saying Hello World!
    info:     Dux ok

### Influence

I took a lot of influence from [jitsu][nodejitsu/jitsu] and [npm][npmjs]. The stylized cli logging and exit conditions are especially useful when writing an application. This repackaging allows anyone to build their own npm or jitsu style tool, without the overhead of logging and command usage.

[joshkehn/dux]: https://github.com/joshkehn/dux
[jcoglan/jake]: https://github.com/jcoglan/jake
[ant]: http://ant.apache.org/
[nodejitsu/jitsu]: https://github.com/nodejitsu/jitsu
[npmjs]: http://npmjs.org/
[wiki/shebang]: http://en.wikipedia.org/wiki/Shebang_(Unix)