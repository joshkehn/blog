{"title": "Alternate Printing in Python","date": 1297182084000}
++++++++++
I'm always forgetting how to write to the stdout in Python without the newlines at the end. Why is this useful? Progress
indicators, counters, specifically sending data with a `\r` return feed but not a `\n` newline. 

Python has a build in language construct called [`print`](http://docs.python.org/tutorial/inputoutput.html). As
mentioned there are many different things you can do with this, including advanced formatting and string replacements.
All well and good unless you want more control over how things are actually getting sent out. For that you need to go
directly to `sys.stdout`. You can create a writer with the following:

    import sys
    writer = sys.stdout.write
    for i in range(0, 1000):
    writer("\r Doing " + str(i))

This will rotate through numbers while staying on the same line.
Tagged: python, tidbits, writing

You can also do:

    print "blah", "blah",

The trailing comma prevents newlines.  The output is (without quotes):

    "blah blah"