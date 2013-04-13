{"title": "More Fun with JavaScript","date": 1293140535000}
++++++++++
I was doing some work with numbers in JavaScript and stumbled upon this most interesting property.

    isNaN()
        => true

    isNaN(null)
        => false

    parseFloat(null)
        => NaN

It would appear that the interpreter can't make up it's mind about what `null` actually *is*, never mind whether or not it's a number. Combine this with the [in]famous [JavaScript truth table](http://stackoverflow.com/questions/1995113/strangest-language-feature/1998224#1998224) and you have for a *very* loosely typed language.