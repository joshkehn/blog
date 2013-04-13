{"title": "Brace Face","date": 1280274549000}
++++++++++
What is this big deal about brace style?

Take the following for example.

    if(cond) {
        // Do something
    } else if(otherCond) {
        // Do Something else
    } else {
        // Otherwise
    }

Does that look right? I think it is hard to follow and confusing. [Allman style](http://en.wikipedia.org/wiki/Indent_style#Allman_style) bracing is much more straightforward. New lines for everything, glorify that whitespace.

I had someone comment:

> Why do you put your braces like that? You save a line by putting it together. It's so much more compact, *etc*.

Readability. If I cared about saving space I wouldn't comment my code.

    if(cond)
    {
        // Do something
    }
    else if(otherCond)
    {
        // About your
    }
    else
    {
        // Brace style
    }

It even makes logic swaps easier (something I picked up on before wikipedia did). See the following.

    //for(i = 0; i < someArr; i++)
    if(someArr.length() > 0)
    {
        // Do something
    }

Since when has code been something we want compact? If you want everything compact, [golf the shit out of it](http://stackoverflow.com/questions/tagged/code-golf). Otherwise, make it nice. Make it readable, put your braces on new lines.