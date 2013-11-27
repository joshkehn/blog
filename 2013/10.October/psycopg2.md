{"title":"Postgres.app and psycopg2 on OS X", "date":1381702652087}
++++++++++

I had a lot of fun today after upgrading [psycopg2][psycopg] to 2.5.1. I was
playing around with [SQLAlchemy][sqlalchemy] so I ran the normal commands for
getting a Postgres database up and running.


    $ virtualenv venv
    $ source venv/bin/activate
    $ pip install psycopg2
    $ python
    >>> from models.py import get_engine
    >>> e = get_engine()
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
      File "models.py", line 11, in get_engine
        engine = create_engine("postgres://localhost/leadgen", echo=True)
      File "/Users/josh/Dropbox/Projects/sqla/venv/lib/python2.7/site-packages/sqlalchemy/engine/__init__.py", line 332, in create_engine
        return strategy.create(*args, **kwargs)
      File "/Users/josh/Dropbox/Projects/sqla/venv/lib/python2.7/site-packages/sqlalchemy/engine/strategies.py", line 64, in create
        dbapi = dialect_cls.dbapi(**dbapi_args)
      File "/Users/josh/Dropbox/Projects/sqla/venv/lib/python2.7/site-packages/sqlalchemy/dialects/postgresql/psycopg2.py", line 368, in dbapi
        import psycopg2
      File "/Users/josh/Dropbox/Projects/sqla/venv/lib/python2.7/site-packages/psycopg2/__init__.py", line 67, in <module>
        from psycopg2._psycopg import BINARY, NUMBER, STRING, DATETIME, ROWID
    ImportError: dlopen(/Users/josh/Dropbox/Projects/sqla/venv/lib/python2.7/site-packages/psycopg2/_psycopg.so, 2): Library not loaded: @loader_path/../lib/libssl.1.0.0.dylib
      Referenced from: /Users/josh/Dropbox/Projects/sqla/venv/lib/python2.7/site-packages/psycopg2/_psycopg.so
      Reason: image not found

**What the hell is that?!?**

First thing I did is jump into some [Google searches][google1]. Ironically the
first result hit was a [StackOverflow question][so] that ultimately solved my
issue but I wasn't settling at the time for an easy solution. This had worked
*seconds* before on another application. Why wasn't it working now?

I jumped over to another Django (1.4) application I had running and tried
upgrading psycopg2. Upgrade and build worked fine, but now I had the same error
as with the SQLAlchemy application. Looked like psycopg2 version was the culprit
here. I tried downgrading to the previous version of psycopg2 (2.4.5). Now the
**same damn error** with the previous version. This can't be good.

Another project I had (running Django 1.5) had the same (old, 2.4.5) version of
psycopg2. Directly copying it to the existing (Django 1.4) project worked fine.
It looks like psycopg2==2.4.5 had been updated at some point and this is why
fresh installs were failing out with this `Reason: image not found` error.

Finally I was at the point where I thought soft linking libraries on my system
was a decent way to solve the problem. [Postgres.app][postgresapp] by the nice
guys at [Heroku][heroku] is where all my PostgreSQL related stuff lives. The
path for the two required dylibs is `/Applications/Postgres.app/Contents/MacOS/lib/libssl.1.0.0.dylib` and `/Applications/Postgres.app/Contents/MacOS/lib/libcrypto.1.0.0.dylib`. Both of these need to be linked into `/usr/local`. There is already
a linked file (`libssl.dylib` and `libcrypto.dylib`) in that folder on my system
that point to `libssl.0.9.8.dylib` and `libcrypto.0.9.8.dylib` respectively. I
wouldn't recommend changing these so I simply softlinked the new 1.0.0 versions
into that folder. These commands require `sudo` for obvious reasons.

    cd /usr/lib
    sudo ln -s /Applications/Postgres.app/Contents/MacOS/lib/libssl.1.0.0.dylib libssl.1.0.0.dylib
    sudo ln -s /Applications/Postgres.app/Contents/MacOS/lib/libcrypto.1.0.0.dylib libcrypto.1.0.0.dylib

Flipping back to my Django 1.4 app I can confirm it works as expected. My
SQLAlchemy application works too now.

### Other points for troubleshooting

The error here is pretty explicit. Something was expected that could not be
found. Google is your friend, and often some of the first results are OK. No
need to feel that a spontaneous problem shouldn't be resolved by a little
softlinking.

That said, it's important to realize that when you push a package at a version
number it should be **frozen**. I should be able to bring down the exact same
code by specifying what version number of a package. Have you changed or
improved something? Great! Time to increment that minor version number.

[psycopg]: http://initd.org/psycopg/
[sqlalchemy]: http://www.sqlalchemy.org
[google1]: https://www.google.com/search?client=safari&rls=en&q=psycopg2+reason+image+not+found&ie=UTF-8&oe=UTF-8
[so]: http://stackoverflow.com/questions/16407995/psycopg2-image-not-found
[postgresapp]: http://postgresapp.com
[heroku]: https://www.heroku.com