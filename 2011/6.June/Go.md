{"title": "Google's Go and seq","date": 1308535696000}
++++++++++
I was browsing some bash posts on `xargs` and wanted to try one of them out.

    $ seq 15 | xargs --max-procs=4 -n 1 echo
    -bash: seq: command not found

What the heck?!? Turns out OS X does *not* have the `seq` command installed. Rather then use [someone else's implementation](http://scruss.com/blog/2008/02/08/seq-for-os-x/) I decided that this would be an excellent time to break out some Go code.

What is Go? [Go](http://golang.org/) is a new programming language, designed in 2009 at Google by [Robert Griesemer](http://research.google.com/pubs/author96.html), [Rob Pike](http://en.wikipedia.org/wiki/Rob_Pike), and [Ken Thompson](http://en.wikipedia.org/wiki/Ken_Thompson). It was designed to be an evolved form of C, with many similar constructs but headaches. Garbage collection is automatic, no need for memory management. It's quite fast too, both to compile and run. Compilation produces native code and there are three architectures with compiler support; AMD64, x86, and ARM are supported respectively by the 6g, 8g, and 5g compilers. 

#### Do we really need *another* programming language?

That's a pretty big question for a quick post about something I'm dabbling with. Suffice it to say, I believe **yes**. While it needs some changes (don't get me started on [K&R bracing, my feelings are known](http://joshuakehn.com/blog/view/13/Brace-Face)), a modern compiled and natively executed language will fill a niche currently squatted on by C and bash programs. 

I have a repository of my Go snippets and projects [available on GitHub under joshuakehn/go-code](https://github.com/joshkehn/go-code). Currently the only program I think well enough to distribute would be my `seq` implementation. The binary is included in that.