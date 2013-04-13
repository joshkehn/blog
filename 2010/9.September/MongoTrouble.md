{"title": "Things to never do again","date": 1285123815000}
++++++++++
Sorry folks, all data is lost. Working on adding back posts in. <em>Update: I managed to recover (though a previous export) a good majority of the posts before moving to MongoDB.</em>

I'm not switching storage engines though, data was lost because *I* was stupid enough to run `mongod --repair` on a perfectly good database, then mess with it. I will be adding posts that I can remember back shortly, expect to see at *least* the WebSocket tutorial back up by tomorrow.

Several people have commented over the last few months that they liked what I was writing about, so I'm sorry that *that* is gone. However I can also equate this to a needed fresh start. I'm also adding a cron job to dump the database into JSON for backup. While this doesn't seem like enough, hopefully I can set up replicate sets, some minor sharding, and gain enough confidence to not need single server durability. My fault for assuming what was never promised. Won't happen again.