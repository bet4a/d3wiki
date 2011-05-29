# Selections

A selection is an array of elements pulled from the current document. D3 uses [[CSS3|http://www.w3.org/TR/css3-selectors/]] to select elements. For example, you can select by tag ("div"), class (".awesome"), unique identifier ("#foo"), attribute ("[color=red]"), or containment ("parent child"). Selectors can also be intersected (".this.that" for logical AND) or unioned (".this, .that" for logical OR). If your browser doesn't support the [[W3C Selectors API|http://www.w3.org/TR/selectors-api/]], you can include [[Sizzle|http://sizzlejs.com/]] before D3 for backwards-compatibility.

After selecting elements, you apply operators to them to do stuff. These operators wrap the [[W3C DOM API|http://www.w3.org/TR/DOM-Level-3-Core/]], setting attributes (`attr`), styles (`style`), properties (`property`), HTML (`html`) and text (`text`) content. Attribute values and such are specified as either constants or functions; the latter are evaluated for each element. You can also join selections to data; this data is available to operators for data-driven transformations. In addition, joining to data produces *enter* and *exit* subselections, so that you may add or remove elements in response to changes in data.

You won't generally need to use for loops or recursive functions to modify the document with D3. That's because you operate on entire selections at once, rather than looping over individual elements. However, you can still loop over elements manually if you want to: there's an `each` operator which invokes an arbitrary function, and each selection is just an array, so elements can be accessed directly (e.g., `[0]`). D3 supports method chaining for brevity when applying multiple operators: the operator return value is the selection.

## Generating Selections

D3 provides two top-level methods for selecting elements: `select` and `selectAll`. These methods accept selector strings; the former selects only the first matching element, while the latter selects *all* matching elements in document traversal order. These methods can also accept nodes, which is useful for integration with third-party libraries (such as jQuery) or developer tools (`$0`).

> d3.<b>select</b>(<i>selector</i>) <a name="d3_select"></a>

Selects the first element that matches the specified selector string, returning a single-element selection. If no elements in the current document match the specified selector, returns the empty selection. If multiple elements match the selector, only the first matching element in document traversal order will be selected.

> d3.<b>select</b>(<i>node</i>)

Selects the specified node. This is useful if you already have a reference to a node, such as `d3.select(this)` within an event listener. Or maybe you selected something previously with jQuery, or want to select a global such as `document.body`.

> d3.<b>selectAll</b>(<i>selector</i>) <a name="d3_selectAll"></a>

Selects all elements that match the specified selector. The elements will be selected in document traversal order (top-to-bottom). If no elements in the current document match the specified selector, returns the empty selection.

> d3.<b>selectAll</b>(<i>nodes</i>)

Selects the specified array of elements. This is useful if you already have a reference to nodes, such as `d3.select(this.childNodes)` within an event listener. Or maybe you selected something previously with jQuery, or want to select a global such as `document.links`. The *nodes* argument doesn't have to be an array exactly; really any psuedo-array that can be coerced into an array, such as a `NodeList` or an `arguments`.

## Working with Selections

Selections are arrays of elements—literally. D3 binds additional methods to the array so that you can apply operators to the selected elements, such as setting an attribute on all the selected elements. In this way, D3 is similar to jQuery. One nuance is that D3 selections are grouped: rather than a one-dimensional array, each selection is an *array of arrays* of elements. This preserves the hierarchical structure of subselections. Most of the time, you can ignore this detail, but that's why a single-element selection looks like `[ [node] ]` rather than `[node]`.

If you want to learn how selections work, try selecting elements interactively using your browser's developer console. You can inspect the returned array to see which elements were selected, and how they are grouped. You can also then apply operators to the selected elements and see how the page content changes.

### Content

D3 has a variety of operators which affect the document content. These are what you'll use the most to display data!

> selection.<b>attr</b>(<i>name</i>[, <i>value</i>]) <a name="attr"></a>

If *value* is specified, sets the attribute with the specified name to the specified value on all selected elements. If *value* is a constant, then all elements are given the same attribute value; otherwise, if *value* is a function, then the function is evaluated for each selected element (in order), being passed the current datum `d` and the current index `i`. The function's return value is then used to set each element's attribute. A null value will remove the specified attribute.

If *value* is not specified, returns the value of the specified attribute for the first non-null element in the selection. This is generally useful only if you know the element contains exactly one element.

The attribute *name* may be specified using a namespace prefix, such as "xlink:href" to specify an "href" attribute the XLink namespace. By default, D3 supports the following namespace prefixes: svg, xhtml, xlink, xml and xmlns. Additional namespaces can be registered by adding to `d3.ns.prefix`.

> selection.<b>classed</b>(<i>name</i>[, <i>value</i>]) <a name="classed"></a>

This operator is a convenience routine for setting the "class" attribute. It understands that the "class" attribute is a set of tokens separated by spaces; under the hood, it will use the [[classList|https://developer.mozilla.org/en/DOM/element.classList]] if available, for convenient adding, removing and toggling of CSS classes.

If *value* is specified, sets whether or not the class with the specified name is associated with the selected elements. If *value* is a constant and truthy, then all elements are given the specified class; if falsey, then the class is removed from all selected elements. If *value* is a function, then the function is evaluated for each selected element (in order), being passed the current datum `d` and the current index `i`. The function's return value is then used to add or remove the specified class on each element.

If *value* is not specified, returns true if and only if the first non-null element in this selection has the class with the specified name. This is generally useful only if you know the element contains exactly one element.

> selection.<b>style</b>(<i>name</i>[, <i>value</i>[, <i>priority</i>]]) <a name="style"></a>

If *value* is specified, sets the CSS style property with the specified name to the specified value on all selected elements. If *value* is a constant, then all elements are given the same style value; otherwise, if *value* is a function, then the function is evaluated for each selected element (in order), being passed the current datum `d` and the current index `i`. The function's return value is then used to set each element's style property. A null value will remove the specified style property. An optional *priority* may also be specified, either as the constant null or the string "important" (without the exclamation point).

If *value* is not specified, returns the current *computed* value of the specified style property for the first non-null element in the selection. This is generally useful only if you know the element contains exactly one element. Note that the computed value may be different than the value that was previously set, particularly if the style property was set using shorthand (such as the "font" style, which is shorthand for "font-size", "font-face", etc.).

> selection.<b>property</b>(<i>name</i>[, <i>value</i>]) <a name="property"></a>

Some HTML elements have special properties that are not easily addressed using standard attributes or styles. For example, form text fields have a `value` property, and checkboxes have a `checked` boolean. You can use the `property` operator to get or set these properties, or any other addressable attribute on the underlying element, such as `className`.

If *value* is specified, sets the property with the specified name to the specified value on all selected elements. If *value* is a constant, then all elements are given the same property value; otherwise, if *value* is a function, then the function is evaluated for each selected element (in order), being passed the current datum `d` and the current index `i`. The function's return value is then used to set each element's property. A null value will delete the specified attribute.

If *value* is not specified, returns the value of the specified property for the first non-null element in the selection. This is generally useful only if you know the element contains exactly one element.

> selection.<b>text</b>([<i>value</i>]) <a name="text"></a>

The `text` operator is based on the [[textContent|http://www.w3.org/TR/DOM-Level-3-Core/core.html#Node3-textContent]] attribute of DOM Level 3 Core. Note that setting the text content will replace any existing child elements!

If *value* is specified, sets the text content to the specified value on all selected elements. If *value* is a constant, then all elements are given the same text content; otherwise, if *value* is a function, then the function is evaluated for each selected element (in order), being passed the current datum `d` and the current index `i`. The function's return value is then used to set each element's text content. A null value will clear the content.

If *value* is not specified, returns the text content for the first non-null element in the selection. This is generally useful only if you know the element contains exactly one element.

> selection.<b>html</b>([<i>value</i>]) <a name="html"></a>

The `html` operator is based on the [[innerHTML|http://www.w3.org/TR/html5/apis-in-html-documents.html#innerhtml]] attribute of HTML5. Note that setting the HTML content will replace any existing child elements! Also, most of the time you'll want to use the `append` or `insert` operators to create HTML content in a data-driven way. This operator is intended more for the edge-cases where you want a little bit of static HTML for rich formatting.

If *value* is specified, sets the inner HTML content to the specified value on all selected elements. If *value* is a constant, then all elements are given the same inner HTML content; otherwise, if *value* is a function, then the function is evaluated for each selected element (in order), being passed the current datum `d` and the current index `i`. The function's return value is then used to set each element's inner HTML content. A null value will clear the content.

If *value* is not specified, returns the inner HTML content for the first non-null element in the selection. This is generally useful only if you know the element contains exactly one element.

> selection.<b>append</b>(<i>name</i>) <a name="append"></a>

Appends a new element with the specified *name* as the last child of each element in the current selection. Returns a new selection containing the appended elements. Each new element inherits the data of the current elements (if any), in the same manner as the `select` operator for generating a subselection. The name must be specified as a constant, though in the future we might allow appending of existing (off-screen) elements or a function to generate the name dynamically.

The element's tag *name* may be specified using a namespace prefix, such as "svg:text" to create a "text" element in the SVG namespace. By default, D3 supports the following namespace prefixes: svg, xhtml, xlink, xml and xmlns. Additional namespaces can be registered by adding to `d3.ns.prefix`.

> selection.<b>insert</b>(<i>name</i>, <i>before</i>) <a name="insert"></a>

Inserts a new element with the specified *name* before the element matching the specified *before* selector, for each element in the current selection. Returns a new selection containing the inserted elements. Each new element inherits the data of the current elements (if any), in the same manner as the `select` operator for generating a subselection. The name and before selector must be specified as constants, though in the future we might allow inserting of existing (off-screen) elements or a function to generate the name or selector dynamically.

The element's tag *name* may be specified using a namespace prefix, such as "svg:text" to create a "text" element in the SVG namespace. By default, D3 supports the following namespace prefixes: svg, xhtml, xlink, xml and xmlns. Additional namespaces can be registered by adding to `d3.ns.prefix`.

> selection.<b>remove</b>() <a name="remove"></a>

Removes the elements in the current selection from the current document. Generally speaking, you should stop using selections once you've removed them, because there's not currently a way to add them back to the document. (See the append and insert operators above for details.)

### Data

> selection.<b>data</b>(<i>data</i>[, <i>join</i>]) <a name="data"></a>

> selection.<b>enter()</b> <a name="enter"></a>

> selection.<b>exit()</b> <a name="exit"></a>

> selection.<b>filter</b>(<i>function</i>) <a name="filter"></a>

> selection.<b>map</b>(<i>function</i>) <a name="map"></a>

> selection.<b>sort</b>(<i>comparator</i>) <a name="sort"></a>

Sorts the elements in the current selection according to the specified comparator function. The comparator function is passed two data elements *a* and *b* to compare, returning either a negative, positive, or zero value. If negative, then *a* should be before *b*; if positive, then *a* should be after *b*; otherwise, *a* and *b* are considered equal and the order is arbitrary. Note that the sort is not guaranteed to be stable; however, it is guaranteed to have the same behavior as your browser's built-in `sort` method on arrays.

### Animation & Interaction

> selection.<b>on</b>(<i>type</i>, <i>listener</i>) <a name="on"></a>

> selection.<b>transition</b>() <a name="transition"></a>

### Control

> selection.<b>each</b>(<i>function</i>) <a name="each"></a>

> selection.<b>call</b>(<i>function</i>[, <i>arguments…</i>]) <a name="call"></a>

> selection.<b>empty</b>() <a name="empty"></a>

> selection.<b>node</b>() <a name="node"></a>

### Subselections

Whereas the top-level select methods query the entire document, a selection's `select` and `selectAll` methods restrict queries to descendants of each selected element; we call this subselection. For example, `d3.selectAll("p").select("b")` returns the first bold ("b") elements in every paragraph ("p") element.

> selection.<b>select</b>(<i>selector</i>) <a name="select"></a>

…

> selection.<b>selectAll</b>(<i>selector</i>) <a name="selectAll"></a>

Subselecting via `selectAll` groups elements by ancestor. Thus, `d3.selectAll("p").selectAll("b")` groups by paragraph, while `d3.selectAll("p b")` returns a flat selection. Subselecting via `select` is similar, but preserves groups and propagates data. Grouping plays an important role in the data join, and functional operators may depend on the numeric index of the current element within its group.
