{"title":"Static File Blogging", "date":1311281672122}
++++++++++  
I [previously mentioned](http://joshuakehn.com/2011/2/7/Redesigning-again.html) that I am working on redesigning the
[root landing page](http://joshuakehn.com). What I may have not mentioned is that I am also working on revamping my
blogging platform.

Taking influence from other static content generators (like [Jekyll](http://jekyllrb.com/)) I'm writing my own
simplistic version. There are a few key points I want to hit:

 * Takes JSON files and parses them. This allows me to include specific date information, time
 * Fast. I mean *fast*. The `rsync` up should be the longest part of the op.
 * 100% static files. Nothing dynamic apart from a few Apache rewrites.
 * Built from scratch. I understand the principals behind reinventing the wheel, but there are things I believe take
time to do yourself and there is immeasurable satisfaction in doing so.

### Flexible Writing Style

One of the main goals in this conversion was to make writing more flexible. Here is the "stack" I've selected for
writing a new blog post:

 * `vi` / [TextMate](http://macromates.com/) / [Sublime Text 2](http://www.sublimetext.com/2)
 * [iA Writer](http://itunes.apple.com/us/app/ia-writer/id392502056?mt=8)
 * [Marked](http://markedapp.com/)
 
Very simple stuff. Writing *should* be simple. I no longer need to fuss with [wmd](http://code.google.com/p/wmd/)
because I'm able to write on any computer at my leisure. I can outline something in OmniOutliner, sketch notes in iA
Writer, then dump it onto Dropbox to sync with my computer before I do fine tuning in TM or Sublime. This kind of
flexibility should not involve *more* work the necessary. Maintaining and adding features to a web interface is not my
idea of a fun time when I would rather jot a note here, a few sentences here, and then push it together. 

### Remove the Database

Databases are really good at two things. Searching for large amounts of information and storing disjointed bits of
information. They are *not* good at serving web pages. 

Let us take a look at a request for a particular blog post *with* a database in the mix. 

> First the *Client* has to send a request. Then it goes over the wire (*Sea of Network Latency*) before hitting my
server. On the server it locates the Apache process and spins up a PHP instance to parse and handle the request. It
checks to see if we have a primed cache (*Disk I/O*). If it finds a valid cache file then it returns that. If there is
no cache then it sends a request to the database server, again going over the wire (*Sea of Network Latency*). The
database munches on the request before regurgitating a sticky blob of data to return. The PHP process (still all PHP
here!) examines this gooey data before deciding that it can manage parsing it. It rolls it through a few processes to
template and format everything before caching it and send it back to the client.

Now if we remove the dynamic portions (PHP) and the slow portions (Database) we get something cleaner and more
manageable.

> First the *Client* has to send a request. Then it goes over the wire (*Sea of Network Latency*) before hitting my
server. On the server it locates the Apache process and (*Disk I/O*)[,] finds a file and send[s] it back to the client.

<cite>Some formatting in []'s added for clarity.</cite>

A database has no place in serving static content except as a convenience. If you can't map out a workflow to refresh
that static content when changes are made then the next best thing is to roll into a purpose built language that will
roll those changes for you at the additional CPU cycle expense.

### Features

Typical blog features:

 * Posts
 * Pages
 * Tags
 * Comments
 * Feeds
 * Trackbacks
 
Features I want:

 * Posts
 * <span style="font-size: 70%">Feeds</span>
 
Comments are a headache. With the amazing amount of spam I *still* get using reCaptcha I don't think it's worth the
headache anymore. Like it enough and you will hit me on Twitter or by email. Pages are just more pieces of static
content. Tags are next to useless and maintaining them is a nightmare.

### So, how is it?

Frankly? Horrible right now. I am using Apache to generate all the indexes, but the HTML is there and the posts are
being reshuffled nicely into directories. I will be making incremental improvements over the next few weeks. Hopefully
something production-ready will be good to go before the Fall. 

<strike>While still extremely bare-bones, you can take a look at the generated site over at
[joshuakehn.com/new](http://joshuakehn.com/new).</strike> Site is now live!