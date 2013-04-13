{"title": "A Curse on IDE's","date": 1278907694000}
++++++++++
IDE's make you lazy. What is the number one thing programers do? Type. What do IDE's do? They take your fingers off the keyboard and tie it to the mouse. This is a waste of movement! Wasted movement is wasted time. Not only that, but IDE's frequently make people forget basic command line operations, depending on a GUI layer of abstraction to handle everything from file renames, version control, automated builds, deployment, configuration, making coffee. Maybe they don't make coffee out of the box, but I heard there's a plugin for [IntelliJ][1].

I advocate plain text editors as much as possible. I also advocate command line usage as much as possible. Where do I spend the majority of my time? Terminal. I have Finder, why do I user Terminal? *I don't have to take my fingers off the keyboard.*

[VIM](http://en.wikipedia.org/wiki/Vim_%28text_editor%29) is one of the more popular text editors. Favorite among system admins and older programmers, VIM is fast and efficient for text manipulation. However, most people still have trouble understanding VIM for the same reason they have problems with combining bash commands. *Stop thinking over everything as a command*. Instead think about creating sentences that describe what you want to accomplish.

> **Your problem with Vim is that you don't grok vi.**
> 
> You mention cutting with yy and
> complain that you almost never want to
> cut whole lines. In fact programmers,
> editing source code, very often want
> to work on whole lines, ranges of
> lines and blocks of code. However, yy
> is only one of many way to yank text
> into the anonymous copy buffer (or
> "register" as it's called in vi).
> 
> The "Zen" of vi is that you're
> speaking a language. The initial y is
> a verb. The statement yy is a simple
> statement which is, essentially, an
> abbreviation for 0 y$.

<cite>[Jim Dennis](http://stackoverflow.com/users/149076/jim-dennis) from his [StackOverflow](http://stackoverflow.com) [answer](http://stackoverflow.com/questions/1218390/what-is-your-most-productive-shortcut-with-vim/1220118#1220118)</cite>

Even an IDE isn't that bad once you commit the majority of commands to memory. Ther other disadvantages include a *huge* memory footprint, clunky interface, poor speed, and a horrid need to invade every part of your system. Imagine taking in a roommate who insists all the walls be repainted, the locks changes, the carpet replaced with wood, and a dial up modem instead of cable.

*Aside from this* everyone seems to think IDE's are common place. What is with the insane dependencies on IDE's like [IntelliJ](http://www.jetbrains.com/idea/), [Eclipse](http://www.eclipse.org/), [NetBeans](http://netbeans.org/), and other such platforms? Are they really necessary?

I'm a hard core text editor user. I *never* found a use in heavy weight applications like Dreamweaver for web development. Now I'm starting to use [Tomcat](http://tomcat.apache.org/) (along with [JSP](http://java.sun.com/products/jsp/) and [Java Servlets](http://java.sun.com/products/servlet/)) to run Java based, web deployed, applications and I find every single tutorial is a walk through of how to make your IDE generate code for you. Everything from the XML file to the WAR deployment is contained in the IDE.

**Oh, and there is no simple way to do this by hand.**

The directory structure alone requires a complex layout complete with several extraneous files simply to *build the deployment package* for Tomcat. I find myself writing scripts to handle compiling, jaring, and deploying into Tomcat. 

[1]: http://www.jetbrains.com/idea/