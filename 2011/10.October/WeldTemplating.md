{"title":"Weld, Don't Template", "date":1319816047000}
++++++++++
<noscript>
    <p class="info">
        This post contains various [gist's][gist link] in order to show code content in an easy to use manner. Your browser appears incapable of rendering these.
    </p>
</noscript>

Templating is generally a pain in the ass. Designers want to add all the fluffy bits, developers don't want their hard work rendered futile. When you entangle logic with markup a very stressful relationship is created between them. Logic and data changes should not adversely effect the markup, but since any change to the template involves butchering the existing markup that can't be helped.

This applies to any templating system, be it a [full blown integrated language][php], a [complete re-imagination of markup][haml][^1], or an implementation almost [completely devoid of logic][django]. Unwieldy is putting it nicely. Evolution of a system shouldn't be stuck in this rut of patched placeholders and snippets of logic. Templating should not be thought of as an extension of programming with some surrounding markup.

### How do we fix this?

[Weld][github weld] is the brainchild of [Paolo][hij1nx twitter]  (known for [Nodejitsu][nj] and [being awesome][hij1nx github]) and [Elijah][tmpvar twitter] (known for [jsdom][jsdom] and also [being awesome][tmpvar github]). It combines a working DOM model with data, merging them together to produce a coherent product — your data modeled over a DOM tree.

That's the whole point of templating, right? Why put placeholder stubs, arbitrary variable names, fragile code fragments, and control structures inline; that isn't even valid HTML! Weld makes use of existing DOM structures like ids and classes to scaffold the data over the markup chunk. Any existing content can be replaced, allowing example or default values to be stubbed in before merging with the data. This makes designers happy because any logic is removed from the template; developers are happy because they don't need to understand the markup or styling.[^2] Take a templating language without any real logic or manipulation (like [Django's][django]) and imagine it simplified past the point of templating. This is weld, intelligent merging of a DOM structure with some data. Write **valid** and **logical** HTML code, then weld some data in place while respecting the markup and the data.

Using weld makes me feel like a magician entertaining a group of kids. Watch this rabbit leap out of the hat.

Start with an HTML fragment (the hat) that exposes the structure but is littered with other presentation classes, shims, and structures (misdirection).

<script src="https://gist.github.com/1314516.js"> </script>

Notice how it can be pre-filled with placeholder text. This allows the design and HTML structure to be laid out in a semantic fashion without thinking about the data. Designs can be adjusted and refined independently because there is no data integration code littering the markup. Multiple designs can also be used with the same chunk of data. No need to rewrite code for a mobile version, just weld the data onto brand new markup.

Data (the rabbit) is just JavaScript objects (or parsed JSON). Fields are inferred from the keys and the content taken from the values. 

<script src="https://gist.github.com/1314528.js"> </script>

Here weld handles numbers, strings, and lists all as native components. No extraneous markup or object wrapping needed. For this trick, all the slight of hand happens at the `weld()` invocation. Take an element and the DOM structure it has, and weld data seamlessly into it. Out comes the rabbit. Here is the merge result that weld gives us.

<script src="https://gist.github.com/1315382.js"> </script>

Weld is fully capable in either a server environment (with jsdom) or on the client (using the DOM provided by the browser). Ajax calls for data can be seamlessly merged into existing on-page markup.

### Options

The `weld()` call can also take a configuration object as an optional third parameter. There are two main options, `alias` and `map`.

The `alias` option is useful for quickly remapping keys to other classes or ids that might be more semantically valid. The `map` option allows you to manipulate how weld handles a specific key / element match. One example is to alter where the value is placed. By default weld alters the default changeable value of the element. `innerHTML` is most common, `<input>`'s change the `value` attribute, `<img>`'s change the `src` attribute, etc. Let's say you want to insert a `data-*` attribute and custom build a link attribute. Using `map` we can do that.

<script src="https://gist.github.com/1315252.js"> </script>

First check if the key is correct, in this case we are looking for the `sources` key. If the key matches we continue on to modify the element. Set a `data-original` attribute with the correct value; set the `href` attribute to a custom built link; set the `innerHTML` to the original value.

### Use It

Weld uses the DOM knowledge advantage to overcoming traditional templating structure, which aren't a good thing to follow in the first place. Thinking about templating as an extension of the program is the wrong approach. Weld breaks the mold and gives the right amount of flexibility in how the data is applied while still forcing separation between the data and the presentation markup.

Server side feasibility of weld just isn't there *yet* because of [jsdom][jsdom]'s slower performance and Node's current adoption. Node's adoption is rapidly increasing and jsdom's performance is being constantly improved.

For a SPA/SPI I think weld is invaluable and any existing systems should be carefully considered for a replacement. Anyone *actually* using that jQuery Templating crap? Stop, wash your hands, and pick up weld.

[^1]: I think HAML and Jade both suck and shouldn't be bothered with. Increasing the amount of abstraction does not make anything better unless it fixes an existing problem.

[^2]: I love designers who show an interest in writing code, but forcing them to do so by integrating the markup and display logic can be painful. Developers can, but often don't want to mess with presentation styles. The point is tension can be easily created in this situation.

[gist link]: https://gist.github.com/
[github weld]: https://github.com/hij1nx/weld
[hij1nx twitter]: https://twitter.com/hij1nx
[hij1nx github]: https://github.com/hij1nx/
[tmpvar twitter]: http://www.twitter.com/tmpvar
[tmpvar github]: https://github.com/tmpvar/
[jsdom]: https://github.com/tmpvar/jsdom
[nj]: http://nodejitsu.com/
[django]: https://docs.djangoproject.com/en/dev/topics/templates/
[no template]: http://permalink.gmane.org/gmane.comp.lang.javascript.nodejs/30999
[php]: http://www.php.net/
[haml]: http://haml-lang.com/