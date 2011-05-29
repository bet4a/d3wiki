# Selections

A selection is an array of elements pulled from the current document. D3 uses [[CSS3|http://www.w3.org/TR/css3-selectors/]] to select elements. For example, you can select by tag ("div"), class (".awesome"), unique identifier ("#foo"), attribute ("[color=red]"), or containment ("parent child"). Selectors can also be intersected (".this.that" for logical AND) or unioned (".this, .that" for logical OR). If your browser doesn't support the [[W3C Selectors API|http://www.w3.org/TR/selectors-api/]], you can include [[Sizzle|http://sizzlejs.com/]] before D3 for backwards-compatibility.

After selecting elements, you apply operators to them to do stuff. These operators wrap the [[W3C DOM API|http://www.w3.org/TR/DOM-Level-3-Core/]], setting attributes (`attr`), styles (`style`), properties (`property`), HTML (`html`) and text (`text`) content. Attribute values and such are specified as either constants or functions; the latter are evaluated for each element. You can also join selections to data; this data is available to operators for data-driven transformations. In addition, joining to data produces *enter* and *exit* subselections, so that you may add or remove elements in response to changes in data.

You won't generally need to use for loops or recursive functions to modify the document with D3. That's because you operate on entire selections at once, rather than looping over individual elements. However, you can still loop over elements manually if you want to: there's an `each` operator which invokes an arbitrary function, and each selection is just an array, so elements can be accessed directly (e.g., `[0]`). D3 supports method chaining for brevity when applying multiple operators: the operator return value is the selection.

## Generating Selections

D3 provides two top-level methods for selecting elements: `select` and `selectAll`. These methods accept selector strings; the former selects only the first matching element, while the latter selects *all* matching elements in document traversal order. These methods can also accept nodes, which is useful for integration with third-party libraries (such as jQuery) or developer tools (`$0`).

> d3.<b>select</b>(<i>selector</i>) <a name="d3_select"></a><br>

Selects the first element that matches the specified selector string, returning a single-element selection. If no elements in the current document match the specified selector, returns the empty selection. If multiple elements match the selector, only the first matching element in document traversal order will be selected.

> d3.<b>select</b>(<i>node</i>)

Selects the specified node. This is useful if you already have a reference to a node, such as `d3.select(this)` within an event listener. Or maybe you selected something previously with jQuery, or want to select a global such as `document.body`.

> d3.<b>selectAll</b>(<i>selector</i>) <a name="d3_selectAll"></a><br>

Selects all elements that match the specified selector. The elements will be selected in document traversal order (top-to-bottom). If no elements in the current document match the specified selector, returns the empty selection.

> d3.<b>selectAll</b>(<i>nodes</i>)

Selects the specified array of elements. This is useful if you already have a reference to nodes, such as `d3.select(this.childNodes)` within an event listener. Or maybe you selected something previously with jQuery, or want to select a global such as `document.links`. The *nodes* argument doesn't have to be an array exactly; really any psuedo-array that can be coerced into an array, such as a `NodeList` or an `arguments`.

## Working with Selections

Selections are arrays of elements—literally. D3 binds additional methods to the array so that you can apply operators to the selected elements, such as setting an attribute on all the selected elements. In this way, D3 is similar to jQuery. One nuance is that D3 selecions are grouped: rather than a one-dimensional array, each selection is an *array of arrays* of elements. This preserves the hierarchical structure of subselections. Most of the time, you can ignore this detail, but that's why a single-element selection looks like `[ [node] ]` rather than `[node]`.

If you want to learn how selections work, try selecting elements interactively using your browser's developer console. You can inspect the returned array to see which elements were selected, and how they are grouped. You can also then apply operators to the selected elements and see how the page content changes.

### Content

D3 has a variety of operators which affect the document content. These are what you'll use the most to display data!

> selection.<b>attr</b>(<i>name</i>[, <i>value</i>])

If *value* is specified, sets the attribute with the specified name to the specified value on all selected elements. If *value* is a constant, then all elements are given the same attribute value; otherwise, if *value* is a function, then the function is evaluated for each selected element (in order), being passed the current datum `d` and the current index `i`. The function's return value is then used to set each element's attribute. A null value will remove the specified attribute.

If *value* is not specified, returns the value of the specified attribute for the first non-null element in the selection. This is generally useful only if you know the element contains exactly one element.

> selection.<b>classed</b>(<i>name</i>[, <i>value</i>])

This operator is a convenience routine for setting the "class" attribute. It understands that the "class" attribute is a set of tokens separated by spaces; under the hood, it will use the [[classList|https://developer.mozilla.org/en/DOM/element.classList]] if available, for convenient adding, removing and toggling of CSS classes.

If *value* is specified, sets whether or not the class with the specified name is associated with the selected elements. If *value* is a constant and truthy, then all elements are given the specified class; if falsey, then the class is removed from all selected elements. If *value* is a function, then the function is evaluated for each selected element (in order), being passed the current datum `d` and the current index `i`. The function's return value is then used to add or remove the specified class on each element.

If *value* is not specified, returns true if and only if the first non-null element in this selection has the class with the specified name. This is generally useful only if you know the element contains exactly one element.

> selection.<b>style</b>(<i>name</i>[, <i>value</i>])

> selection.<b>property</b>(<i>name</i>[, <i>value</i>])

> selection.<b>text</b>([<i>value</i>])

> selection.<b>html</b>([<i>value</i>])

> selection.<b>append</b>(<i>name</i>)

> selection.<b>insert</b>(<i>name</i>, <i>before</i>)

> selection.<b>remove</b>()

> selection.<b>sort</b>(<i>comparator</i>)

### Data

> selection.<b>data</b>(<i>data</i>[, <i>join</i>])

> selection.<b>enter()</b>

> selection.<b>exit()</b>

> selection.<b>filter</b>(<i>function</i>)

> selection.<b>map</b>(<i>function</i>)

### Animation & Interaction

> selection.<b>on</b>(<i>type</i>, <i>listener</i>)

> selection.<b>transition</b>()

### Control

> selection.<b>each</b>(<i>function</i>)

> selection.<b>call</b>(<i>function</i>[, <i>arguments…</i>])

> selection.<b>empty</b>()

> selection.<b>node</b>()

### Subselections

Whereas the top-level select methods query the entire document, a selection's `select` and `selectAll` methods restrict queries to descendants of each selected element; we call this subselection. For example, `d3.selectAll("p").select("b")` returns the first bold ("b") elements in every paragraph ("p") element.

> selection.<b>select</b>(<i>selector</i>)

…

> selection.<b>selectAll</b>(<i>selector</i>)

Subselecting via `selectAll` groups elements by ancestor. Thus, `d3.selectAll("p").selectAll("b")` groups by paragraph, while `d3.selectAll("p b")` returns a flat selection. Subselecting via `select` is similar, but preserves groups and propagates data. Grouping plays an important role in the data join, and functional operators may depend on the numeric index of the current element within its group.
