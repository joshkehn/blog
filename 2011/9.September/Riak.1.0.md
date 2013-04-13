{"title":"Riak 1.0 Preview","date":1315589839000}
++++++++++
I went to [Riak](http://wiki.basho.com/An-Introduction-to-Riak.html)'s 1.0 preview meetup on Thursday, mostly out of curiosity. I had a general understanding of Riak, but never used it or had much intention of using it. Fault tolerance was never a feature I needed to support. SonarHQ sponsored the meetup, which was lead by [Sean Cribbs](http://twitter.com/#!/seancribbs).

The main discussion points were the new features and functionality coming in Riak's 1.0 release. On the features side we had secondary indexing, re-written MapReduce functionality using Riak Pipe, and a new datastore [LevelDB](http://code.google.com/p/leveldb/) among other points.[^1] With these additions Basho is focusing more on feature completeness rather then adding new features. For a 1.0 release I think trimming back your feature list and resolving existing issues is the right move.

During the talk I was surprised to find out that Riak was a lot less developed then I had thought. Some specifics would be helpful.

* Riak is only now supporting secondary indexing, and even then only for LevelDB datastores.
* `list-key` operations aren't as scalable as you would think, plus they are slow and still slow in 1.0.
* Still no multi-index queries. Queries can use a key, or a single index.
* There is no general query language support.
* There is no sorting for queries, there is sorting for searches.
* Index types are limited to strings and integers.

Some of this is a non-issue. General query language? Probably not needed for a standard KV store. Sorting? Really only good for searches anyways. The other things that **do** raise eyebrows are type limitations and lack of good secondary index implementation. They have benefits even within the limited scope Riak defines itself.

Riak is described as an eventually consistent, distributed, fault tolerant, key-value store heavily influenced by CAP Theorem and Amazon's Dynamo paper.[^2] CAP Theorem, or Brewer's Theorem states the following:

> It is impossible for a web service to provide the following three guarantees:
>
> * Consistency
> * Availability
> * Partition-tolerance

<cite>Source: [Brewer's Conjecture and Feasibility](http://lpd.epfl.ch/sgilbert/pubs/BrewersConjecture-SigAct.pdf) (PDF)</cite>

I can't wrap my head around what problem Riak is actively trying to solve, other then fault tolerance. Looking at other common NoSQL solutions they all target a specific problem and do it well. Riak appears to have issues with feature creep and stability. The good news is it looks like 1.0 is a step in the right direction.

[^1]: If you like you can [view the entire slide deck](http://riak-onedotoh-preview.heroku.com/).

[^2]: See [Riak Concepts](http://wiki.basho.com/Concepts.html#Basics).