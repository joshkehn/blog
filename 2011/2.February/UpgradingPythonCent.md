{"title": "Upgrading Python on CentOS","date": 1296840832000}
++++++++++
First off, I'm biased against old, slow, antiquated package management systems. Yes [`yum`](http://en.wikipedia.org/wiki/Yellowdog_Updater,_Modified), I'm talking about **you**. Not only is `yum` horrible, but the default repositories are completely filled with out of date packages. `yum` itself depends on Python 2.4, which was released [way back in November 2004](http://www.python.org/ftp/python/). What version would I like to use? Avoiding my [love of the bleeding edge](/2010/10/7/W3C-Holding-off-on-HTML5.html) I would say 2.7 would be an adequate version, especially for our [Django](http://www.djangoproject.com/)[^1] / [MongoDB](http://www.mongodb.org/)[^2] backed API. Here we will list the steps required to create a fully functional installation of Python 2.7, latest Django (development), and PyMongo.

***

### Installing Python 2.7 on CentOS

First off you need to recognize `yum`'s dependency on Python 2.4. Simply replacing this will break your passing semblance of a package manager. We will be using this later so not breaking is the preferred path. Python versions can live in relative harmony together. [Download the Python source](http://www.python.org/download/) and untar it to some directory. I use `/opt` or `~/source` for all of my non-native additions. You can choose whatever you want.

    [root@server]$ tar -xf Python-2.7.1.tgz
    [root@server]$ yum install gcc
    [root@server]$ ./configure
    [root@server]$ make
    [root@server]$ make altinstall

The `altinstall` part is key, as it will resist installing the binary to the default `/usr/bin/python` path, overriding the needed 2.4 version of Python. On my CentOS installation it put it in `/usr/local/bin/python2.7`. Now you have a fully functional installation of Python residing happily on your system. It should be accessible by using `python2.7` wherever you use `python`.

    [root@server]$ python
    Python 2.4.3 (#1, Nov 11 2010, 13:30:19)
    [GCC 4.1.2 20080704 (Red Hat 4.1.2-48)] on linux2
    Type "help", "copyright", "credits" or "license" for more information.
    >>>

***

### Installing Django 1.3 beta 1 on CentOS with Python 2.7

Installing Django is a trivial step after that. Simply [grab your desired version](http://www.djangoproject.com/download/), unpack the tar, and run `setup.py` with your alternate `python2.7` binary.

    [root@server]$ tar -xf Django-1.3-beta-1.tar.gz
    [root@server]$ cd Django-1.3-beta-1/
    [root@server]$ python2.7 setup.py install

You can check your Django installation as well:

    [root@server]$ python2.7
    Python 2.7.1 (r271:86832, Feb  4 2011, 11:30:52)
    [GCC 4.1.2 20080704 (Red Hat 4.1.2-48)] on linux2
    Type "help", "copyright", "credits" or "license" for more information.
    >>> import django
    >>> django.get_version
    <function get_version at 0x2ae6ecd82c80>
    >>> django.get_version()
    '1.3 beta 1'
    >>>

Easy parts are now out of the way

***

### Installing PyMongo on CentOS under Python 2.7

There is a `pymongo` package for CentOS available under `yum`. The only downside is it will by default install to the `/usr/lib64/python2.4/site-packages` location instead of our new Python 2.7 location. That's okay though, we can deal with that after the fact.

    [root@server]$ yum install pymongo.x86_64
    [root@server]$ cp -R /usr/lib64/python2.4/site-packages/pymongo /usr/local/lib/python2.7/site-packages/
    [root@server]$ cp -R /usr/lib64/python2.4/site-packages/bson /usr/local/lib/python2.7/site-packages/

You have to copy both the `pymongo` and `bson` folder to your new Python installation.

That's it, you should now have a better version of Python (2.7), Django, and PyMongo all living happily on your shitty CentOS box. Want to not waste time with this? Use Ubuntu 10.04 LTS and do everything with aptitude.

 [^1]: Note I'm not particularly fond of Django as a framework, but more on that [later](http://en.wikipedia.org/wiki/Future).

 [^2]: I love MongoDB.