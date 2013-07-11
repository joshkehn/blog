{"title":"Everything I Know About Bitcoins (BTC)", "date":1365897740000}
++++++++++

Last week Anthony wrote a [post on bitcoins](http://blog.byjakt.com/bitcoins.html). Then I get [hit with a tweet](https://twitter.com/AaronFancyPants/status/322089383144599553) asking for more information. This is my best-effort explination of bitcoins.

The best way to start about what a bitcoin _is_ exactly would be the [Wikipedia page on Bitcoins][wiki: bitcoin]. After that read through all the [references][wiki: bitcoin-ref].[^1]

What is a bitcoin? How are they spent? Should I invest in them?

## Bitcoin Basics

Let's say you dig a rock out of the ground. This rock looks nice and you figure on trading it to a friend for some milk. So you etch your name into the block and give it to your friend (Bob). In order to do this you sign both your names on it. Alice -> Bob.

Bob takes this rock and thinks he can get some eggs for it. He goes to Jane and transfers the rock to her, repeating the signing process. Alice -> Bob -> Jane.

This is essentially how bitcoins are transferred. There are some other intricacies like wallets and network verifications, but in a nutshell, Person A and Person B together sign a record saying the bitcoin (or part thereof) now belongs to Person B.

Now how do you find these valuable rocks?

Bitcoins are mined using computers. The network develops a problem and waits for someone to solve it. A simple example would be:

> Find a number that when multiplied by 7 ends with 12345.

[Here is a quick program in Python that solves it](https://gist.github.com/5359035).[^2]

For humans this is hard, but with a computer you can test every number possible until you find it. The generation of bitcoins is a more complex and involves using a [cryptographic hash function][wiki: hash-function][^3].

## I Don't Want To Mine, Gimme BTC

If you don't want to mine bitcoins yourself, you can buy them on an exchange like [Mt. Gox](https://mtgox.com/) (80% of bitcoin trading done here) or accept them as payment for a good or service using something like [Coinbase](https://coinbase.com/). Want to see something crazy? Check out this [graph of the market price (USD)][blockchain: market-price] by [blockchain.info][blockchain]. They also have a [ton of other bitcoin charts you might be interested in][blockchain: charts].

Now that you have some BTC let's see what you can do with them.

## Using BTC In Everyday Life

Are bitcoins as universal as US dollars? Nope. Are they as anonymous? Guess again. Why would bitcoins become a currency?

Let's pose another problem. How do you exchange cash? Physical money is often transacted in person, requiring close proximity to the merchant. It's not feasible for me to exchange cash with someone located far away from me. **This** is where bitcoins shine.

Let me explain in a little more detail. As a consumer I want to transact with someone far away with me. Electronic means (e.g., [Paypal](https://www.paypal.com)) make this possible, but at what cost? Credit card networks are happy to provide the service, but they charge fees on top of the actual cost to use their networks. They are also costly to implement, requiring merchant accounts or another system like [Stripe](https://stripe.com) in between. Bitcoins, on the other hand, have no fees associated with their transfer.

[This bitcoin.it wiki page](https://en.bitcoin.it/wiki/Trade#Internet_.26_Mobile_services) lists a variety of places that accept bitcoins

## Are they for real?

They certainly are real, but their use as a currency is under heavy debate.

> But the biggest difference between bitcoin and other virtual currencies is that bitcoins are the only ones that have speculative value. What’s more, because they’re not tied to a corporate parent, bitcoins appeal to the web’s anarcho-libertarians in the way that no other virtual currency can. Bitcoins hold exactly the same gleaming promise for techno-utopians as gold does for Glenn Beck. They’re a scarce resource, and there’s no government or corporation which can control that resource.

<cite>Source: [Felix Salmon][medium: bitcoins]</cite>

There is **no oversight** to bitcoins. What happens when the bitcoin market heaves into a downward spiral? [Exchanges stop.](https://twitter.com/MtGox/status/322355614414147588) [Prices plummet](http://l.kehn.io/image/0E3h170F2n1n)[^4].

This lack of oversight brings other benefits as well.

> Bitcoin is different. Because transactions are authenticated cryptographically and cannot be reversed, there’s no need to restrict access to the network. There’s no risk to accepting payments from complete strangers. That means people don’t need anyone’s permission or trust to go into business as a Bitcoin-based merchant or financial intermediary. Accepting Bitcoins also allows merchants to avoid much of the administrative overhead, like dealing with chargebacks, that come with a conventional merchant account.

<cite>Source: [Forbes][forbes: bitcoins]</cite>

What about current banks and governments? [Rick Falkvinge](http://falkvinge.net) points out an interesting fact.

> What bitcoin does is cut the banks out of the loop, and by extension, the government’s ability to operate.
> [&hellip;]
> Bitcoin is getting there. But it’s not there yet. When it gets there, expect governments to panic and society to be reshaped into something where governments cannot rely on taxing income nor wealth for running their operations.


<cite>Source: [Rick Falkvinge][falkvinge: bitcoins]</cite>

By removing the control of currency from a bank or government you reduce their ability to economically futz with the system. Is this for the best?

> Here’s where a state could easily step in by just … printing more money, so that economic activity is not choked off by scarcity or hoarding. This would be totally consistent with the C View, where money is created by states to facilitate economic activity. But since Bitcoins can only be produced at a predetermined rate, deflation is a constant possibility, or that Bitcoins turn more into a commodity people buy than a currency people use.

<cite>Source: [Bloomberg][bloomberg: bitcoins]</cite>

Another interesting fact is pointing out that bitcoins won't necessarily help you evade the law.

> Incidentally, all of this exposure which you take with Bitcoin is very unlike transacting a bag of pot for a $100 bill -- or a gold coin.  Unless you're caught pretty much "in the act" once the pot is smoked and the dealer spends the $100 the odds of an ex-post-facto investigation being able to disclose what happened and tie you to the event fades to near-zero.
>
> **This never happens with a Bitcoin transaction -- ever.**

<cite>Source: [Market Ticker][marketticker: bitcoins]</cite>

Because of how transactions are managed with bitcoins (remember signing the rock every time you pass it to the next person?) there is no way bitcoins can be called as anonymous as dollar bills. The only way to equate that would be to create digital wallets and pass those around physically. Wait, that gives me an idea.[^5]

***

Any remaining questions about bitcoins? I'm not an expert, but I do excel at finding answers and solving problems. [Ping me on twitter](https://twitter.com/joshkehn).

[^1]: [Instapaper](http://instapaper.com) is there to help you.

[^2]: The answer is 446208.

[^3]: The network also regulates the difficulty of this problem to ensure blocks of bitcoins are generated approximately every 10 minutes.

[^4]: Captured today from [blockchain.info](http://blockchain.info/charts/market-price)

[^5]: Going to discuss this with Anthony right now.


[wiki: bitcoin]: http://en.wikipedia.org/wiki/Bitcoin
[wiki: bitcoin-ref]: http://en.wikipedia.org/wiki/Bitcoin#References
[wiki: hash-function]: http://en.wikipedia.org/wiki/Cryptographic_hash_function
[preev]: http://preev.com
[blockchain]: http://blockchain.info
[blockchain: charts]: http://blockchain.info/charts/
[blockchain: market-price]: http://blockchain.info/charts/market-price
[medium: bitcoins]: https://medium.com/money-banking/2b5ef79482cb
[forbes: bitcoins]: http://www.forbes.com/sites/timothylee/2013/04/09/bitcoin-is-a-disruptive-technology/
[falkvinge: bitcoins]: http://falkvinge.net/2013/04/03/why-bitcoin-is-poised-to-change-society-much-more-than-the-internet-did/
[bloomberg: bitcoins]: http://www.bloomberg.com/news/2013-04-04/sorry-libertarians-history-shows-bitcoin-isn-t-the-future.html
[marketticker: bitcoins]: http://market-ticker.org/akcs-www?post=219284