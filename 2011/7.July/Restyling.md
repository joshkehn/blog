{"title":"Restyle, part 1", "date":1311583202000}
++++++++++
I'm going to break this into two parts. Part 1 will cover CSS in general and what Blueprint tries to do. Part 2 will cover the actual new design and what I'm aiming for with it. 

My old style was based on something called [Blueprint](http://www.blueprintcss.org/); Blueprint is a [CSS framework](http://en.wikipedia.org/wiki/Cascading_Style_Sheets#CSS_frameworks). Never heard of a "CSS framework?" *Neither had I*. 

### Initial Skepticism 

> **frame&bull;work**
> 
> 1. An essential supporting structure of a building, vehicle, or object.
> 2. A set of classes or libraries the embody an abstract design for solutions to a number of related problems. 

<cite>Source: [Dictionary.com](http://dictionary.reference.com/browse/framework)</cite>

How can you have a CSS framework? There are no imports, classes, or any ability to remix existing rules without selectively overriding them. Unlike [CodeIgniter](http://codeigniter.com/) or [Struts](http://struts.apache.org/) there is no language level method of reuse or selective application. CSS is a basic language designed to mark up HTML documents. Support for variables or expression statements are undefined. How can we call something a "framework" with that kind of handicap?

To answer that we need to delve further into "proper" HTML and CSS. There are three major selectors used for CSS rules.

 * An element might be a `p` tag or a `h1` tag. 
 * Selection by `id` attribute `<div id="footer">`.
 * Selection by class groups `<div id="footer" class="border">`.

In order to create the best markup you will need to utilize all three of these and understand why they are offered for use.

**Element** selectors should be used for basic but globally-applied styles. Margins, borders, colors, and fonts all fall under this category. We might want to give all `p`'s `margin-bottom: 1em;` and `color: #222;` rules. Element styles should form the base of your style rules. 

**Id** selectors are for one-off selections. Any `id` *must* be [unique to the document](http://www.w3.org/TR/html4/struct/global.html#h-7.5.2). Having multiple `id`'s is considered invalid HTML for these purposes. Use `id` selectors to pull parts of the page that need to be styled independently from the element styles. You may have an `h4` used in the footer, but you don't want it to be bold and block-level. 

**Class** selectors are for grouping a ruleset to many elements. There can be as many `class` elements per-element as needed. You can also have many elements share the same class. Class styles should be used for small portions of rulesets that will can apply to elements regardless of `id` or element. Good examples are font colors, borders, icon placement, and text decorations.

Blueprint uses a heavy class based approach to pull and push your elements around into what it believes are some best ideas for layout. Here is the feature list:

 * CSS reset
 * Solid grid layout
 * Typography module
 * Form styles
 * Print styles
 * Plugins
 * Tools, editors, templates to use with Blueprint
 
What Blueprint does is provide a lot (>100) of classes that you have access to. The idea is that you sprinkle these classes around in your HTML and then override anything that you like with a specific ID.

### Great in Theory

In theory this is great. The grid especially helps a lot of people come up with clean layouts with minimal fuss. The typography module stops everyone from being a scab about adjusting your font sizes and selecting proper margins, spacing, padding, and of course fonts. 

In practice sticking to Blueprint becomes very hard once you want to do some of your own stuff. Resetting Blueprint's many rules can be tedious, and often leads to even *more* markup. Fetching all the associated cruft that you may never use tends to increase the overall markup size on the wire instead of decreasing it. Some of the default styling plain *sucks*.

### Rolling Your Own

I'm likely to start off with my own special little reset.

    * { margin: 0; padding: 0}

This old school reset will strip the funky margins and paddings off of everything. Now you are free to re-draw the `p` and `ul` elements as those will need help the most. Other things to hit off are `h[1-6]` and `a` styles. Fixing these should be a priority. After you've done that (~5 LOC) you can start editing your other element level rules such as color and typeface. Do a comparison afterward and see how much you've saved by tailoring your CSS directly to the page. 