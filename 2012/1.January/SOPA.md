{"title":"Why No Blackout?", "date":1327074552466}
++++++++++
On Wednesday dozens of site owners [blacked out their websites][la sopa] in protest of the [Stop Online Piracy Act][wiki sopa] (SOPA) and [Protect IP Act][wiki pipa] (PIPA). Entire ecosystems like [Wordpress][wp], [Tumblr][tumblr], and [Flickr][flickr] offered blackout options for individual's content allowing thousands more to join the protests against the pending legislation. Legislation that could fundamentally change how we use the internet. Some of the really scary stuff like root level DNS blocking is already removed, but plenty still remains to be scared of.

Sounds grand, why not join in?

First, I'm not a dedicated resource like Wikipedia or a well known ecosystem like Reddit or Tumblr. The impact would have been small and hindered more than helped raise awareness for the issues at hand. The small amount of traffic I do get is highly focused towards technology-aware people. They already know about SOPA and don't need additional encouragement from me to contact their representatives and raise an issue.

Second, I believe that something needs to change the net. Be it SOPA, PIPA, or some new unknown that comes out of a government. I was secretly hoping that the [Great Firewall of China][wiki china] would bring about some redundancy and distributed nature to the web but it hasn't. The same [root name server][wiki dns] system administered by the same ICANN committee structured according to the same [1987 RFC specification (1035)][rfc 1035] is in place and well-oiled. The machine is still running vulnerably and no one **gets it**.

Lets look at a case study of two companies both built around the same idea of peer-to-peer file sharing. Napster used a centralized system to manage all the peers and connections between peers. BitTorrent used a distributed protocol that employed decentralized trackers to manage peers and allowed the peers to make connections between themselves. The tracker never sees one byte of content and the torrent information itself can be shared between trackers to gain more users.

The story of Napster's rise and fall is well documented. It is responsible for spawning networks like Gnutella, eDonkey, and clients such as LimeWire[^1]. These networks still exist, but their quality is dubious at best and a criminal honeypot at worst.

BitTorrent has gone on to prosper with advances like [distributed hash tables][wiki dht] and [encryption][wiki btenc]. [In]famous trackers like [ThePirateBay.org][tpb] still live on in safe harbor countries having loose IP laws. The protocol itself has even found value outside of piracy as a method to deliver high-volume files easily using methods like [HTTP Seeding][wiki bt.http] to augment the peer sharing aspect.

Taking charge of your own environment is not a crime. It's like creating your own postal system. It will take some work to get a common language but the end result is a stable system that is virtually immune to attacks on the system as a whole because you have many flexible pieces working together. There are no weak links.

The future is distributed. It is not built on global awareness of all systems at all times. It accounts for failures and downtime. It allows people to remix and distribute not according to who came first but *who is the best*. This system is not easily susceptible to external fuckary. It's a network that peers with reluctance rather than openly to everyone.

[^1]: The LimeWire client has been [shut down since October 2010][jk limewire].

[la sopa]: http://latimesblogs.latimes.com/technology/2012/01/sopa-blackout-who-is-joining-the-protest.html
[wiki sopa]: http://en.wikipedia.org/wiki/SOPA
[wiki pipa]: http://en.wikipedia.org/wiki/PROTECT_IP_Act
[wiki china]: http://en.wikipedia.org/wiki/Golden_Shield_Project
[wiki dns]: http://en.wikipedia.org/wiki/Root_name_server
[wiki dht]: http://en.wikipedia.org/wiki/Distributed_hash_table
[wiki btenc]: http://en.wikipedia.org/wiki/BitTorrent_protocol_encryption
[wiki bt.http]: http://en.wikipedia.org/wiki/BitTorrent_(protocol)#Web_seeding
[rfc 1035]: http://tools.ietf.org/html/rfc1035
[wp]: http://wordpress.com/
[tumblr]: https://www.tumblr.com/
[flickr]: http://www.flickr.com/
[tpb]: http://thepiratebay.se/
[jk limewire]: http://joshuakehn.com/2010/10/27/LimeWire-Closes-Shop.html
