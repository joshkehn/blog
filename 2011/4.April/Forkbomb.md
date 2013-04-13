{"title": ":() { :|: &amp; };:","date": 1302629249000}
++++++++++
**Don't run that command.**  It's a [fork bomb](http://en.wikipedia.org/wiki/Fork_bomb).

> In computing, the fork bomb is a form of denial-of-service attack against a computer system which makes use of the fork operation (or equivalent functionality) whereby a running process can create another running process. Fork bombs typically do not spread as worms or viruses; to incapacitate a system, they rely on the (generally valid) assumption that the number of programs and processes which may execute simultaneously on a computer has a limit. This type of self-replicating program is sometimes called a wabbit.

<cite>Wikipedia: [Fork Bomb](http://en.wikipedia.org/wiki/Fork_bomb)</cite>

Borrowing a better explanation in [a StackOverflow question](http://stackoverflow.com/q/991142/185657)'s [answer](http://stackoverflow.com/questions/991142/how-does-this-bash-fork-bomb-work/991148#991148):

> Breaking it down, there are three big
> pieces:
>
> <script src="https://gist.github.com/4973f0645f2f945620ea.js"></script>
> 
> Inside the body, the function is
> invoked twice and the pipeline is
> backgrounded; each successive
> invocation on the processes spawns
> even more calls to ":". This leads
> rapidly to an explosive consumption in
> system resources, grinding things to a
> halt. 
> 
> Note that invoking it once, infinitely
> recursing, wouldn't be good enough,
> since that would just lead to a stack
> overflow on the original process,
> which is messy but can be dealt with.
> 
> A more human-friendly version looks
> like this:
> 
> <script src="https://gist.github.com/90eda2f012908e1f116f.js"></script>

<cite>[John Feminella](http://stackoverflow.com/users/75170/john-feminella)'s [answer](http://stackoverflow.com/questions/991142/how-does-this-bash-fork-bomb-work/991148#991148) on [Fork Bombs](http://stackoverflow.com/q/991142/185657)</cite>


Other legal variants include:

 * `:(){ :|: & };:`
 * `:() { :|: & };:`
 * `:(){:|:&};:`
 * `:() { :|:& };:`