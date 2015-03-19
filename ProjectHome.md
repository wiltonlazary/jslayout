JSLayout is an implementation of flexible properties and element orientation which can make JavaScript applications look like native desktop applications. JSLayout is a standalone library, is optimized and _fast_, and can easily be integrated with other libraries and widgets.

# Examples #

  * [Horizontal orientation](http://jslayout.googlecode.com/svn/trunk/examples/orientation.html) (requires only `jslayout-orientation.js`)
  * Full-page examples: [Three rows](http://jslayout.googlecode.com/svn/trunk/examples/rows.html), [three columns](http://jslayout.googlecode.com/svn/trunk/examples/columns.html), [3x3 grid (columns)](http://jslayout.googlecode.com/svn/trunk/examples/columns-grid.html), [3x3 grid (rows)](http://jslayout.googlecode.com/svn/trunk/examples/rows-grid.html)
  * [Resizable, flexible frame](http://jslayout.googlecode.com/svn/trunk/examples/resizeable.html)
  * [Two dynamic splitters](http://jslayout.googlecode.com/svn/trunk/examples/splitters.html)
  * Using with other plugins: [jQuery/jWYSIWYG](http://jslayout.googlecode.com/svn/trunk/examples/jwysiwyg.html)

# Download #

The latest version of JSLayout can be found in SVN:

  * [Layout Manager (jslayout.js)](http://jslayout.googlecode.com/svn/trunk/jslayout.js): Supports orientation and flexible box properties, full page layouts, and resize support (~30 kb)
  * [Orientation Manager (jslayout-orientation.js)](http://jslayout.googlecode.com/svn/trunk/jslayout-orientation.js) Supports vertical and horizontal box orientation (~18 kb)

# Usage #

Include `jslayout.js` on your page.

In your content ready script, create a `new LayoutManager([root element])`, where root element is the root of your flexible content, or `new FullLayoutManager([document])`, where `document` is the DOM document object for your full-page content.

You can change an element's orientation between vertical (by default) or horizontal by using the `.setOrientation(element, axis)` method, where `axis` is either `"horizontal"` or `"vertical"`. A horizontally-oriented element has its children laid out from left to right in a row; a vertically-oriented element has its children laid out from top to bottom, like normal page flow.

You can set "flexible" properties by using the `.setFlexibleProperty(element, property[, flex])` where `property` is the name of the CSS box-model property (margin, border, padding, width/height) you want to expand to fill any free space in the element. The optional parameter, `flex`, is an integer which is weighed against other flex values in determining free space.

When you're done setting flexible properties/orientation, call the `.calculate()` method to initialize the element.

At any point during the script (when content changes size, etc.) you can call `recalculate()` to reflow flexible content, or after significant DOM changes, you can call `calculate()` again.

The root element passed to a `LayoutManager` automatically checks for when the element is resized and calls `recalculate()` automatically. A `FullLayoutManager` will recalculate flexible content whenever the window is resized, allowing full-page layouts.