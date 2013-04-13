{"title": "W3C: Holding off on HTML5?","date": 1286482272000}
++++++++++
"An official" within the [World Wide Web Consortium (W3C)](http://www.w3.org/) would like to make it clear that HTML5 is not ready for adoption.

> HTML5, which updates the HTML
> specification to accommodate modern
> Web applications, has gained a lot of
> adherents in vendors like Microsoft,
> Google, and Apple. But the
> specification is plain not ready yet
> for deployment to websites, an
> official with the World Wide Web
> Consortium (W3C), which oversees
> HTML5, stressed this week.
> 
> "The problem we're facing right now is
> there is already a lot of excitement
> for HTML5, but it's a little too early
> to deploy it because we're running
> into interoperability issues,"
> including differences between video on
> devices, said the official, Philippe
> Le Hegaret, W3C interaction domain
> leader. He is responsible for
> specifications like HTML and SVG
> (Scalable Vector Graphics).


<cite>Main article on InfoWorld, [W3C: Hold off on deploying HTML5](http://www.infoworld.com/d/developer-world/w3c-hold-html5-in-websites-041?page=0,0)

[HTML5](http://dev.w3.org/html5/spec/Overview.html) is the "next step" in the HTML specifications and arguably one of the most important after the failed attempted adoption of [XHTML](http://en.wikipedia.org/wiki/XHTML) which has been in the works for *10+ years*. HTML5 brings a lot to the table in terms of extended functionality on all fronts focused mainly JavaScript and tag specific changes. 

Disregarding the obvious advantages of HTML5 I would like to go over the arguments against as presented.

***

#### Browser Support

> "I don't think it's ready for production 
> yet," especially since W3C still will make 
> some changes on APIs, said Le Hegaret. "The
> real problem is can we make [HTML5] work 
> across browsers and at the moment, that is 
> not the case."

Just because you might add stuff doesn't mean it can't be used. Using [802.11n](http://en.wikipedia.org/wiki/IEEE_802.11) as an example.

> 802.11n is a recent amendment which improves upon the previous 802.11
> standards by adding multiple-input
> multiple-output antennas (MIMO) and
> many other newer features. The IEEE
> has approved the amendment and it was
> published in October 2009.[12][13]
> Prior to the final ratification,
> enterprises were already migrating to
> 802.11n networks based on the Wi-Fi Alliance's certification of products
> conforming to a 2007 draft of the
> 802.11n proposal.

<cite>Wikipedia's article on [802.11n](http://en.wikipedia.org/wiki/IEEE_802.11#802.11n)</cite>

Here we have adoption of *draft specifications* by major companies (Apple) prior to full ratification by the [IEEE (Institute of Electrical and Electronics Engineers)](http://www.ieee.org/index.html). 

> "The point of HTML5 is this has been
> an ongoing effort for a while now and
> many parts of HTML5 are already in the
> wild," such as Canvas 2D capabilities
> and WebSockets, for communicating
> between browsers, said John Fallows,
> CTO of Kaazing, which makes a
> WebSockets gateway.

In the second one, that's made by someone makes money selling a multi-headed system for emulating a WebSocket connection. Why should he say that WebSockets are decently supported enough to be implemented? 

I've previously written about [WebSockets](http://joshuakehn.com/blog/view/2/WebSocket-Tutorial-with-Node-js) and the uses they may have (full duplex connections mean responsive *fast* web based applications). I'm also currently using WebSockets in the middle of developing a rather large scale application which will be faced frontend to more then a few people. What do they need to work it? IE 8, Firefox 3, Safari 4, or Chrome. *Right there you have 65%+ of all internet traffic.* [^1]

> "IE6 is still being used on the Web today, and it is 10 years old."

<cite>Philippe Le Hegaret, W3C interaction domain leader.</cite>

If you are running IE 6 I do **not** care about you. It's a simply brutal fact that I am not catering to people running vintage systems. 10+ years is ancient when talking about computers. Are you still running Windows 2000 or ME? (XP was released August 2001). 

When was the last time your website was accessible to a braille reader? How about color blind people? *You're always going to have accessibility problems*, **deal with it**.

***

#### Everything else

Browser support covers about half the article. Which is disappointing considering the how little it matters.

The [rest of the article](http://www.infoworld.com/d/developer-world/w3c-hold-html5-in-websites-041?page=0,1) is mostly hits on the same points. No DRM, no standard codec (MPEG-4 is covered by patents, [Ogg Vorbis](http://en.wikipedia.org/wiki/Vorbis) is not.

The W3C does *not* have the final say. They recommend standards for use. The best way to get something pushed through is by large scale adoption and community support. Again referring to 802.11n, Apple incorporated it into Airport devices March 2009, right after [8.0 draft spec was passed](http://en.wikipedia.org/wiki/IEEE_802.11n-2009). Then it gets approved October 2009 after drafts had been in the works since March 2006. 

The more people use something the better it becomes. CodeIgniter is a great framework because lots of people use it. Apache is a great web server because *lots of people use it*. Software does not become worse with use (unless we're talking about [Microsoft Word](http://en.wikipedia.org/wiki/Software_bloat) that is). 

[^1]: Estimated market share by [browser type](http://marketshare.hitslink.com/browser-market-share.aspx?qprid=2).
