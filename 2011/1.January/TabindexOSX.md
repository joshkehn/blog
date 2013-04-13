{"title": "Tabindex on Mac OS X","date": 1295374746000}
++++++++++
Mac OS X has an odd way of exposing preferences. To change the default browser you open Safari, and to enable standard form tabindexes (no matter what browser) you open up Accessibility settings.

![Accessibility Settings OS X][1]

  [1]: http://img810.imageshack.us/img810/5355/screenshot20100701at107.png

I [beat my head over on SO](http://stackoverflow.com/questions/3159782/from-tabindex-include-selects/3160046#3160046) looking for an answer before I discovered the above. The one major peculiarity is that this restriction is globally applied across all browsers. The user interface is limited on the operating system level to restrict keyboard based access to theses elements. I recommend turning on "All Controls" for heavy keyboard users because it opens up accessibility to a lot of options that are normally restricted.