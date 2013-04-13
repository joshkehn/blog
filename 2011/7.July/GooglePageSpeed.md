{"title":"Google Page Speed", "date":1311845520000}
++++++++++
Google just rolled out [Page Speed Service](http://code.google.com/speed/pss/docs/overview.html).

> Google's new Page Speed Service is one part optimization tool and one part content distribution network (CDN). Google essentially grabs your website, caches it and serves it from the company's extensive network of servers around the world. The best part about Page Speed is its simplicity - all you need to do is point your DNS to Google's servers. After that Google handles the rest and you don't need to worry about minifying your JavaScript, compressing images, caching, gzipping, or any other web performance best practices.

<cite>Source: [webmonkey](http://www.webmonkey.com/2011/07/googles-new-page-speed-service-promises-to-speed-up-your-website/)</cite>

Sounds great, right? **Wrong.**

In addition to the [many limitations](https://code.google.com/speed/pss/faq.html#limitations) of this service, why should we trust Google with our data? I have talked about [Google and privacy](http://joshuakehn.com/blog/new/perm/21.HTML-5-Privacy-Concerns.html#thisisalreadytrue) before, what about Google and data security? Advertising was [97% of Google's revenue](http://www.wordstream.com/blog/ws/2011/07/18/most-expensive-google-adwords-keywords) for Q3 2010 - Q2 2011. 

In the doubtful case that Google is really just trying to benefit the web as a whole, I ran my site through the comparison. The results weren't surprising. Both of my test pages *increased* in load time. [joshuakehn.com](http://www.webpagetest.org/result/110728_XJ_e1b09ccd8a07bb18b49356c7f8d3489b/ "Page Speed Service comparison for joshuakehn.com") increased 59% when "optimized" while my [websocket tutorial page](http://www.webpagetest.org/result/110728_N3_6c289737b4adac6f604d28723c847e8d/ "Page Speed Service comparison for Joshua Kehn's WebSocket Tutorial") went up 48%. 

[Ben Brooks](http://brooksreview.net/2011/07/page-speed-service/) has seen similar results:

> An interesting project from Google to try and speed up the web for the entire world – for free. There are some real concerns with allowing Google to do that, but as any nerd I was more interested in how much faster they could make TBR.
> 
> [Here are the results](http://brooksreview.s3.amazonaws.com/pagespeedservice.png).&nbsp;<sup>1</sup>
>
> <small>1. Don't see myself using it any time soon.</small>

<cite>Source: [TBR](http://brooksreview.net/2011/07/page-speed-service/)</cite>