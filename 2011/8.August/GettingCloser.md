{"title":"Getting Closer to Switching", "date":1312571876239}
++++++++++
After an extensive re-write I'm just a few steps away from switching completely from the old blog to the new static file driven one. 

I had originally stored my posts as JSON files

    // AnotherPost.json
    {
        "title": "Another Post",
        "date" : 1292571876239,
        "body": "<!-- html code -->"
    }
    
The trouble this caused was a crazy workflow. Edit Markdown source -> Save -> Generate HTML -> Paste into JSON file -> Format correctly -> Save -> Regenerate -> Upload. If I caught a typo or wanted to tweak something I had to go through the entire flow again.

I only want to edit one file. Simplest way is to store some headers along with the markdown source for each post. [Jekyll](https://github.com/mojombo/jekyll/wiki) uses [YAML](http://en.wikipedia.org/wiki/YAML). I wanted to stay away from markup languages and decided to go with a simple JSON blob as a header seperated by a deliminator.

    {"title":"Switching", "date":1312571876239}  
    ++++++++++
    After an extensive re-write I'm...

I read the file, split it by `++++++++++`, and parse the header and markdown separately. Edit Markdown source -> Save -> Generate -> Upload. 

Other various improvements:

 * Added Next / Previous navigation to the bottom of every post. 
 * Updated style to better reflect [the home page](http://joshuakehn.com).
 * Rewrote generation script for more efficiency and to accomodate additional features.
 * Post path structure is now much more flexible.
 * Removed legacy `post_id` garbage.