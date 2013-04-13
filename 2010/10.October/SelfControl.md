{"title": "Defeating SelfControl","date": 1287975754000}
++++++++++
[Steve Lambert](http://visitsteve.com/) released an interesting application called [SelfControl](http://visitsteve.com/made/selfcontrol/). If falls into the vein of a productivity boost if you need a matron to spank you for visiting *bad* sites like [Facebook](# "Meet friends!"), [Twitter](# "Mind vomit on them!"), or [Email](# "Talk to them!"). Here is how to defeat it's relatively simplistic blocking techniques.

SelfControl uses two techniques in tandem to thwart your attempts at fun and leisure. First (and most obvious) is a rule in the your `/etc/hosts` file. Looks something like this:

    # BEGIN SELFCONTROL BLOCK
    127.0.0.1\tfacebook.com
    127.0.0.1\twww.facebook.com
    # END SELFCONTROL BLOCK

Working up some simple [sed](http://en.wikipedia.org/wiki/Sed) magic we use


    sed "/# BEGIN SELF/,/# END SELF/d"

to cut out that block. Poof gone, should work right?

Nope. One more thing. It turns on [ipfw](http://en.wikipedia.org/wiki/Ipfirewall) and adds a few rules. Find your specific ones by running `ipfw list`. Remove those and you're golden.

Finalized "SelfControl Killer":

    #!/bin/bash

    echo "Removing IPFW rules 01500 - 01506";

    ipfw delete 01500;
    ipfw delete 01501;
    ipfw delete 01502;
    ipfw delete 01503;
    ipfw delete 01504;
    ipfw delete 01505;
    ipfw delete 01506;

    echo "Reversing /etc/hosts";
    HOSTS=/etc/hosts;
    TMP=tmpsedscrp;
    sed "/# BEGIN SELF/,/# END SELF/d" $HOSTS > $TMP;
    mv $TMP $HOSTS;

I saved it as *"ipfwrm"* for *"ipfw remove"* before I noticed the regenerating host file manipulations.

Remember that you have to do a `sudo -s` prior to sticking this into a loop. After you do, run `while true; do ./ipfwrm && sleep 10; done` to set this up to continually remove the block. The program is smart enough to recreate it if removed.

Overall it is tricky but simple. There really isn't much you can't do as root. At least it's not a paid application. You could probably duplicate this exact functionality without the GUI in a dozen or so lines.