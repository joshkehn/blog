{"title":"MongoDB 2.0 Notes", "date":1316194949000}
++++++++++
September is the month of releases so it seems. First [Riak announces a 1.0 release](http://joshuakehn.com/2011/9/9/Riak-10-Preview.html) and now [MongoDB announces their 2.0 release](http://blog.mongodb.org/post/10126837729/mongodb-2-0-released).

[Eliot Horowitz](http://www.10gen.com/team) from 10gen hosted a [What's New in MongoDB 2.0](http://www.meetup.com/New-York-MongoDB-User-Group/events/33265152/) talk which I attended. I took some notes, which you can find in the standard [OmniOutliner 3](http://joshuakehn.com/static/mongodb_2.0.oo3), and [plain text](http://joshuakehn.com/static/mongodb_2.0.txt) versions. I had a dynamic HTML version, but cannot remember how I did that.

The big deal with 2.0—and all of the MongoDB releases—is that they are drop in replacements. There isn't an upgrade path or reconfiguration. No major breaking changes. Shut the database down, drop the new binaries in, and watch it work. With 2.0 there were onyl two potential problem points.

1. Indexes are reconfigured in 2.0. If you would like to take advantage of the new 2.0 indexes you will have to reindex.
2. Journaling is enabled by default. To keep it off, start `mongod` with the `--nojournal` flag.

After the painless upgrade we can proceed to the exciting new features found in 2.0. First let's delve a little bit into how 10gen is structuring these releases.

MongoDB 2.0 was an iteration. Not a major milestone release like sharding with 1.6 was.[^1] This release comprised of over four months development time and 417 resolved JIRA tickets. 10gen is trying to structure stable releases in a steady 3-4 month pattern, and so far is doing very well. This 2.0 release is not oriented around a single feature but is instead focusing on stability and small-to-medium sized improvements over 1.8. You can see the [2.0 release notes](http://www.mongodb.org/display/DOCS/2.0+Release+Notes) for a full breakdown of the features implemented.

Now that we have that, on to the features.

Journaling was added in 1.8 and is on by default in 2.0. The journal is also compressed and a new `{j:true}` option has been added to wait until the journal has been written before returning on `getLastError`.

A new compact command has been written that improves on the previous repair database command. The new compact system doesn't require double disk space as it performs the compaction in place. It also processes index building in parallel and only requires a single read of the database.

Priorities for replica sets (originally added in 1.6) have been expanded. You can now use any floating point number 0-1000. You can [read more on priorities](http://www.mongodb.org/display/DOCS/Replica+Sets+-+Priority).

Indexes are 25% smaller on average. 1.8 indexes are forward compatible with 2.0, but 2.0 indexes due to the new format are *not* backwards compatible with previous MongoDB releases. In order to upgrade your indexes you have to rebuild them. Spatial indexing has been improved to allow multiple locations per document and spatial polygon searching has been added. There is no ability to define polygons as a type at this time.

2.0 also added the `$and` operator. This is great when used in conjunction with other operators. This functions exactly how you would expect and further enhances the MongoDB query language. See [Advanced Queries#$and](http://www.mongodb.org/display/DOCS/Advanced+Queries#AdvancedQueries-%24and) for more information.

There were also a few concurrency improvements which deals with yielding the write lock if the data isn't in memory at the time. You can see more about how this works on [JIRA ticket #2563](https://jira.mongodb.org/browse/SERVER-2563).

Eliot also talked a little bit about tasks for the 2.2 and 2.4 releases. They are clearly on the ball with a good vision for the future in mind. I would recommend looking MongoDB if you haven't already.

[^1]: Unless you can call remaining profitable and continuing steady development for over two years a milestone. I certainly would.