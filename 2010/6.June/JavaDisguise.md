{"title":"Java in Disguise", "date" : 1275619413000}
++++++++++
After my [previous post][jk appceletrator] about [Appcelerator](http://www.appcelerator.com/) I've decided to post some code to mull over, specifically the wide similarities between this and Java Swing.

    Win.title_lb = Titanium.UI.createLabel
    ({
        color: '#eee',
        text: Ti.App.Properties.getString('title'),
        font:{fontSize: 40, fontFamily: 'Verdana'},
        top: -200,
        left: 100,
        textAlign: 'left',
    });

What does that remind you of? If you said [Labels in Java](http://java.sun.com/docs/books/tutorial/uiswing/components/label.html) you might be right. I find a *surprising* amount of similarity between the pseudo-javascript that Appcelerator claims to be and the Java it undoubtedly tries to be.

Either way I finished the app, no need to worry about that until they have a design change.

[jk appceletrator]: /2010/6/1/Appcelerator-and-the-iPad.html