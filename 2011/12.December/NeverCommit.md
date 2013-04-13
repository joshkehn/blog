{"title":"10 Things You Should Never Commit", "date":1323201944652}
++++++++++

A few [mishaps][twitter link] I've been on the receiving end of prompted me to write this list. It is by no means definitive.

***

1. Large binary files. Take a step back and facepalm yourself. Media (images, video, audio) doesn't belong in your **code** repository.[^1]
2. CSV databases. Import it into a database and be done with it. Better yet, go over to [nodejitsu][nj] and build a service you can query.
3. Dependency modules. Mix them in as part of a build step, but keeping revisions of dependencies is retarded especially considering they are often managed in their own repository.
4. Other revision management software. Once I tried to use git to version a svn working copy. Those were dark days.
5. Puppies. No matter how cute they are, putting living mammals in your code repository is not a good idea.
6. Platform specific code. Don't build something for FreeBSD and commit it when you're deploying to a Linux server.
7. Build folders. Rip that out. `rm -rf` is the only suitable hook when you have a build folder. This is *source control* management. Not *binary files I generated with my `make` script* management.
8. Configuration files. Configuration *templates* sure, but don't commit every single platform and deployments config file to your repo. It reeks of juvenile developer.
9. Sensitive information. If I had a nickel for every time I saw MySQL root passwords committed I would have over $450.00. Put that in a config file and then see point #8.
10. Data. Data goes into a database. Something specifically designed to *handle your data*. Doesn't matter if it's sample data, production data, or whatever data. It doesn't belong.


[^1]: The only possible exception to this is if you're building a web page / site and you're too lazy to externalize your images.

[twitter link]: https://twitter.com/#!/joshkehn/status/142759026340540416
[nj]: http://nodejitsu.com/
