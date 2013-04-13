{"title": "Mobile Stylesheets","date": 1287106523000}
++++++++++
I have been frequently going to work without my laptop. While I like the mobility it provides, I don't use it often enough. The train is a great place to sleep, and I never miss the several pounds it adds.

This leaves me with iPod Touch for anything I need to do while afoot and out of the office. Normally this works fine, however today I wanted to double check something I had previously said on [HTML5: Privacy Concerns?](http://joshuakehn.com/blog/view/21/HTML-5-Privacy-Concerns). After pulling up the page I realized that while the site didn't look *bad* by any stretch, it definitely didn't look *good*. The navigation was a bit hard to see, the `<h1>` at the top was a large block of waste, the text wasn't sized right, and of course browsing the home page meant having to skip large blocks of summary text.

Mobile stylesheets aren't anything new. A List Apart has two excellent as always articles, [Put Your Content In My Pocket](http://www.alistapart.com/articles/putyourcontentinmypocket/) (2007) and the  more recent [Return of the Mobile Stylesheet](http://www.alistapart.com/articles/return-of-the-mobile-stylesheet) (2010). I recommend giving both a read. In summary, there are some wonderfully hacky ways to tell if someone is on a device smaller then originally intended. I choose to be a snob and shun everyone but the Mobile Safari crowd. I know, [I'm a bad person](http://joshuakehn.com/blog/view/10/I-put-bacon-on-veggie-burgers), but this gives me 80% effect for 20% effort. [^1] If someone knows a decent way to implement basic Android support I would be happy to, however I can't guarantee perfect rendering because I don't have a device to test and debug on. 

The styles are pretty simple, and it's only 50 lines (uncondensed, I'm condensing it for brevity below) so I'll break it down for you.

    .container { width: 95%; -webkit-text-size-adjust: 325%; }

I was at a time very enamored with Blueprint. This left some good and bad habits. One of the (hopefully) good ones is using an inner wrapper class to center things. This rule will turn the width fluid and readjust the sizing for a better view. [^2]

    #content { margin: 0; }
    #tags, #download, .mobilehide, .commentbar, form 
        { display: none; }

First we strip the margin of `#content`, and then we hide junk that mobile users shouldn't use. Commenting is disabled because reCAPTCHA looks and acts like junk, post summaries are removed because it clutters, you can't download, and you don't need to see tags. Reduced functionality for cleanliness. If I get complaints I'll put it back in.

    h1 {font-size:1em; }
    .title { font-size:1.1em; }
    #navigation ul li a { font-size:1.2em; margin-right:1em; }
    .prev, .next { font-size:0.8em; }

Adjust font sizes for the newly adjusted text. Navigation should be larger, headers should be smaller.

    .comment { width:100%; margin:0 auto; }

Adjust comment width, probably should do this on the main site too but I dislike long strings of text.

    .comment img { height:150px;width:150px; }

Comment [gravatars](http://en.gravatar.com/) should be bigger.

    pre,code{width:45ex;overflow:scroll;}

Code blocks shouldn't limit the rest of the screen, truncate the size. You can still scroll in them but scroll bars won't appear readily due to how Mobile Safari renders `overflow: scroll` properties. Two fingers will allow you to scroll.

That's the complete change. Compressed it's only *nine lines long* and in my opinion makes it that much more readable. Any feedback on the mobile version would be appreciated!


[^1]: This is known as the 80/20 rule, or the [Pareto Principle](http://en.wikipedia.org/wiki/Pareto_principle). You could also say it's similar to the [law of diminishing returns](http://en.wikipedia.org/wiki/Diminishing_returns) as you will end up spending 80% of the time and effort fixing or accommodating the last 20%. 
    
    Just like people with comments in their CSS saying "For those IE 5.5 Mac users, may you rot in hell."

[^2]: A bit hard to explain why this is needed without additional bulk, however Mobile Safari is a *true browser* in the sense that it renders the page like a desktop instead of mangling it. This gives you the impression of a fully functional page. When you design a specific mobile version you will then need to adjust the font size via `-webkit-text-size-adjust` to fix the sizing. Otherwise I would have fonts `25em`'s tall.