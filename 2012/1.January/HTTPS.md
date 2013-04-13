{"title":"HTTPS Now Available","date":1328127916649}
++++++++++

I've enabled HTTPS on my server, and while it's not "real" (self-signed) certificate, my [domain registrar][gandi] is issuing a correct one soon. I've also updated the URL structures on my generator to point without specifying the protocol or domain. This means that when you visit [https://joshuakehn.com][jk https] all links pointing to other posts, the home page, etc, will point to the secured version. I can't vouch for any old self referring links as those are linked directly in the file, but I'll update those where necessary when I find them.

### Why HTTPS?

I believe in offering more options to users. HTTPS uses [Transport Layer Security][wiki tls] to provide end-to-end encryption for all content served from my server off of the domain. Anyone who wishes to practice web anonymity can do so. How much use this will be is questionable, as I don't have any personalized content, no cookies, no login, nothing persisted on my server unique to users. When (and if) I role out anything that requires a login HTTPS will always be an option. Privacy is not a liberty I believe should be denied, especially when it's so damn easy to set up a security certificate and add that to Apache.[^1]

[^1]: There will be an article about this later.

[gandi]: https://www.gandi.net/
[jk https]: https://joshuakehn.com/
[wiki tls]: http://en.wikipedia.org/wiki/Transport_Layer_Security