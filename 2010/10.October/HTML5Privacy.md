{"title": "HTML 5: Privacy Concerns?","date": 1286803467000}
++++++++++
The [New York Times](http://www.nytimes.com/) ran a front page article on new web standards and privacy concerns they may pose to users. 

> In the next few years, a powerful new suite of capabilities
> will become available to Web developers that could give 
> marketers and advertisers access to many more details about 
> computer users' online activities. Nearly everyone who uses
> the Internet will face the privacy risks that come with 
> those capabilities, which are an integral part of the Web 
> language that will soon power the Internet: HTML5.

<cite>Vega, Tanzina. "[Web Code Offers New Ways To See What Users Do Online.](http://www.nytimes.com/2010/10/11/business/media/11privacy.html?_r=1&hp)" New York Times 11 Oct. 2010: A1</cite>

That lack of technical voice in the article raises a point of concern. While HTML5 does contain several new features that will open up doors for many user tuned applications, it is by no means the death blow to privacy this article suggests. HTML5 is also still a working draft according to the W3C.[^1] HTML5 is also a generic umbrella term that has been cast over the wide range of emerging technology. 

> It will make it easier for users to view multimedia content 
> without downloading extra software; check e-mail offline; 
> or find a favorite restaurant or shop on a smartphone.

Last I checked you can't check email off line. You *could* use [local storage](http://dev.w3.org/html5/webstorage/) to simulate a browser session, but you wouldn't be able to view new mail or send messages. Multimedia content is almost wholly flash based, as over 95% of online users have the Flash Plugin.[^2] While HTML5 does bring new standards for in-browser viewing of multimedia content it is far from standardized and lacks the content control Flash currently offers. I can find a restaurant on my smartphone with any one of a dozen apps, no need to use HTML5 for that.

The article also refers to local storage, a local key / value database that sites can use to store information. For example I might wish to store unfinished blog entries, comments, or even web site notes locally. One thing to remember is that local storage is nothing new, while you have to guard against cross domain requests (domain.com requesting example.com's local storage container) everything that is stored is stored by the corresponding web application. Long term storage can be done by submitting information back to the server for remote storage. Many advertisers will track users browsing patterns by remotely storing pages that are visited with that advertisers content. 

> That could include a user's location, time zone, photographs, 
> text from blogs, shopping cart contents, email's and history 
> of the Web pages visited. 

Time zone? Identified by IP address. Location? Narrowed down to city with a free database, closer if you purchase. Text from blogs? I'm not sure. Photographs? Is the site going to scrape my hard drive? No! This is impossible unless you are using local storage for photos, which you shouldn't be doing. Shopping cart contents? Should be secured by reputable sites and cross domain information requests should be denied by the browser. Lack of secure browser could lead to far more damage then a new suite of web technologies. Email and browsing history falls under the same principals of shopping cart contents. Securely encrypting storage and effective cross domain denial will deal with 99% of the privacy concerns with local storage. 

Following up with a brief piece about the [Evercookie](http://samy.pl/evercookie/) and browser privacy controls the article leaves you with the sickening feeling that every move you make is being watched and there is little you can do about it.

### This Is Already True

Google itself is probably the biggest privacy concern out there today. How many of you have a GMail account? Don't block the [google-analytics.com](http://google-analytics.com) domain? Here is a theoretical way in which Google could uniquely track people (not computers) across the web.

 1. User visits a Google Analytics or AdSense enabled website.
 2. Google checks to see if they already have a cookie.
 3. If so, log the hit from this user, otherwise generate a unique user id.
 4. When this user visits other Analytics or AdSense enabled websites, continue to track the user across these sites.
 5. Should a user have a Google Account (for Docs, GMail, or any other purpose) then the unique user id is really just a unique id used to identify the user. This tracking information then gets assigned to your account. 

Google Checkout is just one service the requires a credit card. Now browsing patterns and traffic can be linked physically to *you*. 

Now Google has this large reserves of personal information available, what should they do about it? For one the can give it to the government on demand. Another would be to power their vast and ever expanding advertising network. 

Root cause of privacy is not new web technology, it's existing web technology that has been creatively re-purposed to obtain information. 

 [^1]: http://dev.w3.org/html5/spec/Overview.html
  
 [^2]: http://www.statowl.com/plugin_overview.php  