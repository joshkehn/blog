{"title":"IFTTT - Internet Goodness", "date" : 1326142325580}
++++++++++

I've known about [ifttt][ifttt] for a few months, but never really thought it could be useful. Most of my daily work is already automated through various [bin scripts][github --bin] and some server side cron jobs. What I didn't immediately see is how incredibly *polished* ifttt is.

The service starts off with a simple concept. If **this** then **that**. It's simplicity is rivaled only by something like [iA Writer][writer]. There are no other configurable options outside what is offered in **this** and **that**. 

### Channels

The **this** and **that** concepts are implemented by way of [channels][ifttt channels]. Here is what I've connected to so far:

* Date & Time
* Email
* Feed
* Flickr
* Foursquare
* Instagram
* Phone Call
* SMS
* Tumblr
* Twitter
* Weather

Every channel offers unique **triggers** and **actions**. **Triggers** are **this**. They are monitored when you create a **task**. **Actions** are **that**. They are executed with a specific trigger. You can create multiple tasks to emulate multiple actions performed on a trigger.

### Tasks

![IFTTT Task List][task list]

Tasks simply combine a trigger and an action to perform when that trigger happens. You can enable or disable tasks with a simple click. All tasks are created through the same *if **this** then **that** fashion*. First you select the channel you would like to pick a trigger from. Then you define a channel you would like to pick an action from. The simple user flow is great. 

### Recipes
Recipes are tasks that can be setup and shared with friends or found publicly. The service simply substitutes your channel information in and starts you off with the recipe for a task. All of this is customizable as well. I started with the [Archive my tweets to Google Calendar][ifttt archive] recipe and switched the Google Calendar channel to email so I can back them up all my tweets through email.

### Feature Wishlist

1. Allow multiple accounts per channel. Currently you can only have a single account on any channel at any time. This means that to connect two Twitter accounts I need to create another ifttt account. Not a huge hassle, but switching is annoying especially if you want to make use of separate accounts on other services like Gmail.

2. Expand **this** to include multiple channel filters. Something like if **8:00AM EST** and **Rain predicted** then **SMS alert**. It's often ambiguous about **when** the action will trigger and more importantly **how often**. Say I create a trigger to tweet something when the forecast for tomorrow dips below freezing[^1]. What if the forecast fluctuates during the day? Will 30F to 35F to 28F produce two tweets at 30F and 28F? Allow things like this to be time constrained would be great, but chaining the triggers together would be the ideal solution.

3. The corollary of #2 is to expand **that** to include multiple actions. This would create more of a rule style setup. If **[conditions]** then **[actions]**. 

4. Add more custom channels. Allow developers to make HTTP calls or call a trigger remotely. I would love to link my server's to ifttt so I get custom SMS or email alerts. 

I've only been using ifttt for a few hours and already I've created five tasks. The service is simple. It's easy for anyone to go in and create their own ifttt's. I can't wait to see what they do next.

[^1]: This task is already in place.

[ifttt]: http://ifttt.com/
[ifttt channels]: http://ifttt.com/channels
[ifttt archive]: http://ifttt.com/recipes/12708
[github --bin]: https://github.com/joshkehn/--bin
[writer]: http://www.iawriter.com/
[task list]: http://i.imgur.com/CZC6u.png