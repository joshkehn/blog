{"title":"On npm and scalenpm.org", "date":1385570577736}
++++++++++

> The npm Registry recently got crashy, and it was incredibly painful.

The headline on [scalenpm.org][scalenpm] sounds terrible. It is terrible when
your packaging solution goes offline and it's difficult or impossible to
install new pieces of software. When *anything* goes off line[^1] it's a painful
experience to deal with. We should work as hard as possible to make distributed
systems that can resist failing infrastructure. This means backups, mirroring,
and adding fallback systems to the core product.

Building a distributed system is hard. I don't mean to trivialize it with so few
sentences. I think the flawed efforts of [nodejitsu][nodejitsu] are nobel. What
npm needs isn't a corporate backer, it needs a non-profit transparent
foundation.

Why do they need $200,000? How much does npm cost to actually run in terms of
time and hardware? Nodejitsu has taken a **$2,650,0000** in funding.[^2] They
are a for-profit company. They have given **zero** transparency other than some
fancy looking numbers.

![npm stats &mdash; what do they mean?][stats link]

The [Python Software Foundation][psf] is a 501(c)(3) corporation that has
[sponsor members][psf sponsor]. These sponsors allow it to run [pypi][pypi], the Python package index. This is a fully transparent operation. Why isn't npm
run the same way?

[^1]: Here's looking at you GitHub.

[^2]: http://www.crunchbase.com/company/nodejitsu

[scalenpm]: https://scalenpm.org
[nodejitsu]: https://www.nodejitsu.com
[stats link]: https://scalenpm.org/img/npm-stats.png
[psf]: http://www.python.org/psf/
[psf sponsor]: http://www.python.org/psf/sponsorship/
[pypi]: https://pypi.python.org/pypi