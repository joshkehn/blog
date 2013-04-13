{"title": "Download Posts","date": 1285442394000}
++++++++++
Ability to download posts has been added. You have the choice of two formats:

 * [Markdown](http://en.wikipedia.org/wiki/Markdown): Lightweight as-is-original source for the post. I use markdown mostly due to my exposer to it from [stackoverflow](http://stackoverflow.com) and it quickly won me over. I rarely, if ever, use anything else. 
 * [PDF](http://en.wikipedia.org/wiki/Portable_Document_Format): Portable Document Format (PDF) from Adobe is one of the leading document formats due to it's extremely "correct" display on every platform. I added this in case a more print ready version was needed, or if zipping up and emailing to someone else. 

Some key differences:

Feature  |  Markdown  |  PDF
---------|------------|------
Date     | No         | Yes 
Author   | No         | Yes
Title    | Yes        | Yes 
Styling  | None       | Yes
Colors   | No         | Yes
Images   | Linked     | Embedded
Links    | [source]   | Hyperlinked


Essentially the PDF version is a properly formatted print version while the markdown source is "raw" in the sense that you could paste it into any Markdown editor and get the formatting back. 

Implementing the Markdown was easy as expected.[^1] PDF's from HTML source was a bit tricky. After taking a look at [Zend_PDF](http://framework.zend.com/manual/en/zend.pdf.html) and realizing I didn't want to write my own library, I checked the usual suspects, SO was mildly helpful with some expensive (but good) commercial software. The CodeIgniter wiki was much better with a [PDF generation using dompdf](http://codeigniter.com/wiki/PDF_generation_using_dompdf/) write up. That only major issue I noticed was that it didn't accept linked stylesheets, and for some reason saying `line-height: 1.5;` made it go a bit nuts, leaving all the text squished on a few random lines. I wrote up a specific `printhead` view with all the proper style embedded and then tweaked it slightly. Doesn't look amazing, but much better then standard fair. 

[^1]: I expect everything to be easy until it isn't.