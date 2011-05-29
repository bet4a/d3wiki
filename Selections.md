# Selections

A selection is an array of elements pulled from the current document. D3 uses [[CSS3|http://www.w3.org/TR/css3-selectors/]] to select elements. For example, you can select by tag ("div"), class (".awesome"), unique identifier ("#foo"), attribute ("[color=red]"), or containment ("parent child"). Selectors can also be intersected (".this.that" for logical AND) or unioned (".this, .that" for logical OR). If your browser doesn't support the [[W3C Selectors API|http://www.w3.org/TR/selectors-api/]], you can include [[Sizzle|http://sizzlejs.com/]] before D3 for backwards-compatibility.

After selecting elements, you apply operators to them to do stuff. These operators wrap the [[W3C DOM API|http://www.w3.org/TR/DOM-Level-3-Core/]], setting attributes (`attr`), styles (`style`), properties (`property`), HTML (`html`) and text (`text`) content. Attribute values and such are specified as either constants or functions; the latter are evaluated for each element.

You won't generally need to use for loops or recursive functions to modify the document with D3. That's because you operate on entire selections at once, rather than looping over individual elements. This is true even for hierarchical structures, such as nested lists, because you can create subselections. However, if you want to loop over elements manually, you still can. There's an `each` operator which invokes an arbitrary function, and since each selection is simply an array, elements can also be accessed directly (e.g., `[0]`).

D3 supports method chaining for brevity when applying multiple operators: the operator return value is the selection. The `append` and `insert` operators add a new element for each element in the current selection, returning the added nodes, thus allowing the convenient creation of nested structures. The `remove` operator discards selected elements.

You can also join selections to data; this data is available to operators for data-driven transformations. In addition, joining to data produces *enter* and *exit* subselections, so that you may add or remove elements in response to changes in data.

## Generating Selections

D3 provides two top-level methods for selecting elements: `select` and `selectAll`. These methods accept selector strings; the former selects only the first matching element, while the latter selects *all* matching elements in document traversal order. These methods can also accept nodes, which is useful for integration with third-party libraries (such as jQuery) or developer tools (`$0`).

> <b>d3.select</b>(<i>selector</i>) <a name="d3_select"></a><br>

Selects the first element that matches the specified selector string, returning a single-element selection. If no elements in the current document match the specified selector, returns the empty selection. If multiple elements match the selector, only the first matching element in document traversal order will be selected.

> <b>d3.select</b>(<i>node</i>)

Selects the specified node. This is useful if you already have a reference to a node, such as `d3.select(this)` within an event listener. Or maybe you selected something previously with jQuery, or want to select a global such as `document.body`.

> <b>d3.selectAll</b>(<i>selector</i>) <a name="d3_selectAll"></a><br>

Selects all elements that match the specified selector. The elements will be selected in document traversal order (top-to-bottom). If no elements in the current document match the specified selector, returns the empty selection.

> <b>d3.selectAll</b>(<i>nodes</i>)

Selects the specified array of elements. This is useful if you already have a reference to nodes, such as `d3.select(this.childNodes)` within an event listener. Or maybe you selected something previously with jQuery, or want to select a global such as `document.links`. The specified *nodes* do not have to be an array exactly, but any psuedo-array that can be coerced into an array, such as a NodeList or arguments array.

## Working with Selections

Whereas the top-level select methods query the entire document, a selection's `select` and `selectAll` methods restrict queries to descendants of each selected element; we call this subselection. For example, `d3.selectAll("p").select("b")` returns the first bold ("b") elements in every paragraph ("p") element.

> selection.<b>select</b>(<i>selector</i>)

…

> selection.<b>selectAll</b>(<i>selector</i>)

Subselecting via `selectAll` groups elements by ancestor. Thus, `d3.selectAll("p").selectAll("b")` groups by paragraph, while `d3.selectAll("p b")` returns a flat selection. Subselecting via `select` is similar, but preserves groups and propagates data. Grouping plays an important role in the data join, and functional operators may depend on the numeric index of the current element within its group.
