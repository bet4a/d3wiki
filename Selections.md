> [[API Reference]] ▸ [[Core]]

A **selection** is an array of elements pulled from the current document. D3 uses [[CSS3|http://www.w3.org/TR/css3-selectors/]] to select elements. For example, you can select by tag ("div"), class (".awesome"), unique identifier ("#foo"), attribute ("[color=red]"), or containment ("parent child"). Selectors can also be intersected (".this.that" for logical AND) or unioned (".this, .that" for logical OR). If your browser doesn't support selectors natively, you can include [[Sizzle|http://sizzlejs.com/]] before D3 for backwards-compatibility.

After selecting elements, you apply **operators** to them to do stuff. These operators can get or set [attributes](Selections#wiki-attr), [styles](Selections#wiki-style), [properties](Selections#wiki-property), [HTML](Selections#wiki-html) and [text](Selections#wiki-text) content. Attribute values and such are specified as either constants or functions; the latter are evaluated for each element. You can also join selections to [data](Selections#wiki-data); this data is available to operators for data-driven transformations. In addition, joining to data produces [enter](Selections#wiki-enter) and [exit](Selections#wiki-enter) subselections, so that you may [add](Selections#wiki-append) or [remove](Selections#wiki-remove) elements in response to changes in data.

You won't generally need to use for loops or recursive functions to modify the document with D3. That's because you operate on entire selections at once, rather than looping over individual elements. However, you can still loop over elements manually if you wish: there's an [each](Selections#wiki-each) operator which invokes an arbitrary function, and selections are arrays, so elements can be accessed directly (e.g., `selection[0][0]`). D3 supports method chaining for brevity when applying multiple operators: the operator return value is the selection.

## Selecting Elements

D3 provides two top-level methods for selecting elements: [select](Selections#wiki-d3_select) and [selectAll](Selections#wiki-d3_selectAll). These methods accept selector strings; the former selects only the first matching element, while the latter selects *all* matching elements in document traversal order. These methods can also accept nodes, which is useful for integration with third-party libraries such as jQuery or developer tools (`$0`).

<a name="d3_select" href="Selections#wiki-d3_select">#</a> d3.<b>select</b>(<i>selector</i>)

Selects the first element that matches the specified selector string, returning a single-element selection. If no elements in the current document match the specified selector, returns the empty selection. If multiple elements match the selector, only the first matching element in document traversal order will be selected.

<a href="Selections#wiki-d3_select">#</a> d3.<b>select</b>(<i>node</i>)

Selects the specified node. This is useful if you already have a reference to a node, such as `d3.select(this)` within an event listener, or a global such as `document.body`.

<a name="d3_selectAll" href="Selections#wiki-d3_selectAll">#</a> d3.<b>selectAll</b>(<i>selector</i>)

Selects all elements that match the specified selector. The elements will be selected in document traversal order (top-to-bottom). If no elements in the current document match the specified selector, returns the empty selection.

<a href="Selections#wiki-d3_selectAll">#</a> d3.<b>selectAll</b>(<i>nodes</i>)

Selects the specified array of elements. This is useful if you already have a reference to nodes, such as `d3.select(this.childNodes)` within an event listener, or a global such as `document.links`. The *nodes* argument doesn't have to be an array exactly; any pseudo-array that can be coerced into an array will work, such as a `NodeList` or an `arguments`.

## Operating on Selections

Selections are arrays of elements—literally. D3 binds additional methods to the array so that you can apply operators to the selected elements, such as setting an attribute on all the selected elements. One nuance is that selections are *grouped*: rather than a one-dimensional array, each selection is an *array of arrays* of elements. This preserves the hierarchical structure of subselections. Most of the time, you can ignore this detail, but that's why a single-element selection looks like `[[node]]` rather than `[node]`.

If you want to learn how selections work, try selecting elements interactively using your browser's developer console. You can inspect the returned array to see which elements were selected, and how they are grouped. You can also then apply operators to the selected elements and see how the page content changes.

### Content

D3 has a variety of operators which affect the document content. These are what you'll use the most to display data! When used to set document content, the operators return the current selection, so you can chain multiple operators together in a concise statement.

<a name="attr" href="Selections#wiki-attr">#</a> selection.<b>attr</b>(<i>name</i>[, <i>value</i>])

If *value* is specified, sets the attribute with the specified name to the specified value on all selected elements. If *value* is a constant, then all elements are given the same attribute value; otherwise, if *value* is a function, then the function is evaluated for each selected element (in order), being passed the current datum `d` and the current index `i`, with the `this` context as the current DOM element. The function's return value is then used to set each element's attribute. A null value will remove the specified attribute.

If *value* is not specified, returns the value of the specified attribute for the first non-null element in the selection. This is generally useful only if you know the element contains exactly one element.

The specified *name* may have a namespace prefix, such as "xlink:href" to specify an "href" attribute in the XLink namespace. By default, D3 supports svg, xhtml, xlink, xml and xmlns namespaces. Additional namespaces can be registered by adding to d3.ns.**prefix**.

<a name="classed" href="Selections#wiki-classed">#</a> selection.<b>classed</b>(<i>name</i>[, <i>value</i>])

This operator is a convenience routine for setting the "class" attribute; it understands that the "class" attribute is a set of tokens separated by spaces. Under the hood, it will use the [[classList|https://developer.mozilla.org/en/DOM/element.classList]] if available, for convenient adding, removing and toggling of CSS classes.

If *value* is specified, sets whether or not the specified class is associated with the selected elements. If *value* is a constant and truthy, then all elements are assigned the specified class, if not already assigned; if falsey, then the class is removed from all selected elements, if assigned. If *value* is a function, then the function is evaluated for each selected element (in order), being passed the current datum `d` and the current index `i`, with the `this` context as the current DOM element. The function's return value is then used to assign or unassign the specified class on each element.

If *value* is not specified, returns true if and only if the first non-null element in this selection has the specified class. This is generally useful only if you know the element contains exactly one element.

<a name="style" href="Selections#wiki-style">#</a> selection.<b>style</b>(<i>name</i>[, <i>value</i>[, <i>priority</i>]])

If *value* is specified, sets the CSS style property with the specified name to the specified value on all selected elements. If *value* is a constant, then all elements are given the same style value; otherwise, if *value* is a function, then the function is evaluated for each selected element (in order), being passed the current datum `d` and the current index `i`, with the `this` context as the current DOM element. The function's return value is then used to set each element's style property. A null value will remove the style property. An optional *priority* may also be specified, either as null or the string "important" (without the exclamation point).

If *value* is not specified, returns the current *computed* value of the specified style property for the first non-null element in the selection. This is generally useful only if you know the element contains exactly one element. Note that the computed value may be *different* than the value that was previously set, particularly if the style property was set using a shorthand property (such as the "font" style, which is shorthand for "font-size", "font-face", etc.).

<a name="property" href="Selections#wiki-property">#</a> selection.<b>property</b>(<i>name</i>[, <i>value</i>])

Some HTML elements have special properties that are not addressable using standard attributes or styles. For example, form text fields have a `value` string property, and checkboxes have a `checked` boolean property. You can use the `property` operator to get or set these properties, or any other addressable field on the underlying element, such as `className`.

If *value* is specified, sets the property with the specified name to the specified value on all selected elements. If *value* is a constant, then all elements are given the same property value; otherwise, if *value* is a function, then the function is evaluated for each selected element (in order), being passed the current datum `d` and the current index `i`, with the `this` context as the current DOM element. The function's return value is then used to set each element's property. A null value will delete the specified attribute.

If *value* is not specified, returns the value of the specified property for the first non-null element in the selection. This is generally useful only if you know the element contains exactly one element.

<a name="text" href="Selections#wiki-text">#</a> selection.<b>text</b>([<i>value</i>])

The `text` operator is based on the [[textContent|http://www.w3.org/TR/DOM-Level-3-Core/core.html#Node3-textContent]] property; setting the text content will replace any existing child elements.

If *value* is specified, sets the text content to the specified value on all selected elements. If *value* is a constant, then all elements are given the same text content; otherwise, if *value* is a function, then the function is evaluated for each selected element (in order), being passed the current datum `d` and the current index `i`, with the `this` context as the current DOM element. The function's return value is then used to set each element's text content. A null value will clear the content.

If *value* is not specified, returns the text content for the first non-null element in the selection. This is generally useful only if you know the element contains exactly one element.

<a name="html" href="Selections#wiki-html">#</a> selection.<b>html</b>([<i>value</i>])

The `html` operator is based on the [[innerHTML|http://www.w3.org/TR/html5/apis-in-html-documents.html#innerhtml]] property; setting the inner HTML content will replace any existing child elements. Also, you may prefer to use the `append` or `insert` operators to create HTML content in a data-driven way; this operator is intended for when you want a little bit of HTML, say for rich formatting.

If *value* is specified, sets the inner HTML content to the specified value on all selected elements. If *value* is a constant, then all elements are given the same inner HTML content; otherwise, if *value* is a function, then the function is evaluated for each selected element (in order), being passed the current datum `d` and the current index `i`, with the `this` context as the current DOM element. The function's return value is then used to set each element's inner HTML content. A null value will clear the content.

If *value* is not specified, returns the inner HTML content for the first non-null element in the selection. This is generally useful only if you know the element contains exactly one element.

<a name="append" href="Selections#wiki-append">#</a> selection.<b>append</b>(<i>name</i>)

Appends a new element with the specified *name* as the last child of each element in the current selection. Returns a new selection containing the appended elements. Each new element inherits the data of the current elements, if any, in the same manner as [select](Selections#wiki-select) for subselections. The name must be specified as a constant, though in the future we might allow appending of existing elements or a function to generate the name dynamically.

The element's tag *name* may have a namespace prefix, such as "svg:text" to create a "text" element in the SVG namespace. By default, D3 supports svg, xhtml, xlink, xml and xmlns namespaces. Additional namespaces can be registered by adding to d3.ns.**prefix**.

<a name="insert" href="Selections#wiki-insert">#</a> selection.<b>insert</b>(<i>name</i>, <i>before</i>)

Inserts a new element with the specified *name* before the element matching the specified *before* selector, for each element in the current selection. Returns a new selection containing the inserted elements. If the before selector does not match any elements, then the new element will be the last child as with [append](Selections#wiki-append). Each new element inherits the data of the current elements (if any), in the same manner as [select](Selections#wiki-select) for subselections. The name and before selector must be specified as constants, though in the future we might allow inserting of existing elements or a function to generate the name or selector dynamically.

The element's tag *name* may have a namespace prefix, such as "svg:text" to create a "text" element in the SVG namespace. By default, D3 supports svg, xhtml, xlink, xml and xmlns namespaces. Additional namespaces can be registered by adding to d3.ns.**prefix**.

<a name="remove" href="Selections#wiki-remove">#</a> selection.<b>remove</b>()

Removes the elements in the current selection from the current document. Generally speaking, you should stop using selections once you've removed them, because there's not currently a way to add them back to the document. (See the append and insert operators above for details.)

### Data

<a name="data" href="Selections#wiki-data">#</a> selection.<b>data</b>(<i>data</i>[, <i>key</i>])

Joins the specified array of data with the current selection. The specified *data* is an array of data values, such as an array of numbers or objects. In the simplest case, the first datum in the specified array is assigned to the first element in the current selection, the second datum to the second selected element, and so on. When data is assigned to an element, it is stored in the property `__data__`, thus making the data "sticky" so that the data is available on re-selection.

The *data* array specifies the data for each group in the selection. Thus, if the selection has multiple groups (such as a selectAll followed by a selectAll), then *data* should be specified as a function that returns an array, assuming that you want different data for each group. One common scenario with subselections is that a two-dimensional array is bound to the outer selection, and then the contained one-element arrays are each bound to the inner selection. In this case, the *data* function can be the identity function: it is invoked for each group of child elements, being passed the data bound to the parent element, and simply returns this array of data.

```javascript
var matrix = [
  [11975,  5871, 8916, 2868],
  [ 1951, 10048, 2060, 6171],
  [ 8010, 16145, 8090, 8045],
  [ 1013,   990,  940, 6907]
];

var tr = d3.select("body").append("table").selectAll("tr")
    .data(matrix)
  .enter().append("tr");

var td = tr.selectAll("td")
    .data(function(d) { return d; })
  .enter().append("td")
    .text(function(d) { return d; });
```

To control how data is joined to elements, an optional *key* function may be specified. This replaces the default behavior which assigns by index. The key function is invoked once for each element in the new data array, and once again for each existing element in the selection. In both cases the key function is passed the datum `d` and the index `i`. When the key function is evaluated on new data elements, the `this` context is the data array; when the key function is evaluated on the existing selection, the `this` context is the associated DOM element. The key function returns a string which is used to join a datum with its corresponding element, based on the previously-bound data. For example, if each datum has a unique field `name`, the join might be specified as:

```javascript
.data(data, function(d) { return d.name; })
```

For a more detailed example of how the key function affects the data join, see the tutorial [[A Bar Chart, Part 2|http://mbostock.github.com/d3/tutorial/bar-2.html]].

The result of the `data` operator is the *update* selection; this represents the selected DOM elements that were successfully bound to the specified data elements. The *update* selection also contains a reference to the [enter](Selections#wiki-enter) and [exit](Selections#wiki-exit) selections, for adding and removing nodes in correspondence with data. For example, if the default key-by-index is used, and the existing selection contains fewer elements than the specified data, then the *enter* selection will contain placeholders for the new data. On the other hand, if the existing contains more elements than the data, then the *exit* selection will contain the extra elements. And, if the existing selection exactly matches the data, then both the enter and exit selections will be empty, with all nodes in the update selection.

If a key function is specified, the `data` operator also affects the index of nodes; this index is passed as the second argument `i` to any operator function values. However, note that existing DOM elements are not automatically reordered; use the [sort](Selections#wiki-sort) operator as needed.

<a name="enter" href="Selections#wiki-enter">#</a> selection.<b>enter()</b>

Returns the entering selection: placeholder nodes for each data element for which no corresponding existing DOM element was found in the current selection. This method is only defined on a selection returned by the [data](Selections#wiki-data) operator. In addition, the entering selection only defines [append](Selections#wiki-append) and [insert](Selections#wiki-insert) operators; you must use these operators to instantiate the entering nodes before modifying any content. Note that the *enter* operator merely returns a reference to the entering selection, and it is up to you to add the new nodes.

As a simple example, consider the case where the existing selection is empty, and we wish to create new nodes to match our data:

```javascript
d3.select("body").selectAll("div")
    .data([4, 8, 15, 16, 23, 42])
  .enter().append("div")
    .text(function(d) { return d; });
```

Assuming that the body is initially empty, the above code will create six new DIV elements, append them to the body in order, and assign their text content as the associated (string-coerced) number:

```html
<div>4</div>
<div>8</div>
<div>15</div>
<div>16</div>
<div>23</div>
<div>42</div>
```

Another way to think about the entering placeholder nodes is that they are pointers to the parent node (in this example, the document body); however, they only support append and insert.

The enter selection merges into the update selection when you append or insert. This approach reduces code duplication between enter and update. Rather than applying operators to both the enter and update selection separately, you can now apply them to the update selection after entering the nodes. In the rare case that you want to run operators only on the
updating nodes, you can run them on the update selection before entering new nodes.

<a name="exit" href="Selections#wiki-exit">#</a> selection.<b>exit()</b>

Returns the exiting selection: existing DOM elements in the current selection for which no new data element was found. This method is only defined on a selection returned by the [data](Selections#wiki-data) operator. The exiting selection defines all the normal operators, though typically the main one you'll want to use is [remove](Selections#wiki-remove); the other operators exist primarily so you can define an exiting transition as desired. Note that the *exit* operator merely returns a reference to the exiting selection, and it is up to you to remove the new nodes.

As a simple example, consider updating the six DIV elements created in the above example for the enter operator. Here we bind those elements to a new array of data with some new and some old:

```javascript
var div = d3.select("body").selectAll("div")
    .data([1, 2, 4, 8, 16, 32], function(d) { return d; });
```

Now `div`—the result of the data operator—refers to the updating selection. Since we specified a key function using the identity function, and the new data array contains the numbers [4, 8, 16] which also exist in the old data array, this updating selection contains three DIV elements. Let's say we leave those elements as-is. We can instantiate and add the new elements [1, 2, 32] using the entering selection:

```javascript
div.enter().append("div")
    .text(function(d) { return d; });
```

Likewise, we can remove the exiting elements [15, 23, 42]:

```javascript
div.exit().remove();
```

Now the document body looks like this:

```html
<div>4</div>
<div>8</div>
<div>16</div>
<div>1</div>
<div>2</div>
<div>32</div>
```

Note that the DOM elements are now out-of-order. However, the selection index (the second `i` argument to any operator functions), will correctly match the new data array. For example, we could assign an index attribute:

```javascript
d3.selectAll("div").attr("index", function(d, i) { return i; });
```

This would result in:

```html
<div index="2">4</div>
<div index="3">8</div>
<div index="4">16</div>
<div index="0">1</div>
<div index="1">2</div>
<div index="5">32</div>
```

If you want the document traversal order to match the selection data order, you can use the [sort](Selections#wiki-sort) operator to reorder elements.

<a name="filter" href="Selections#wiki-filter">#</a> selection.<b>filter</b>(<i>function</i>)

Filters the selection, returning a new selection that contains only the elements for which the specified *function* returns true. As with other operators, the specified function is passed the current datum `d` and index `i`, with the `this` context as the current DOM element. Like the built-in array [[filter|https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/Filter]] method, the returned selection *does not* preserve the index of the original selection; it returns a copy with elements removed. If you want to preserve the index, use [select](Selections#wiki-select) instead. For example, to select every other element:

```javascript
var odds = selection.select(function(d, i) { return i & 1 ? this : null; }));
```

Thus, you can use either select or filter to apply operators to a subset of elements.

<a name="map" href="Selections#wiki-map">#</a> selection.<b>map</b>(<i>function</i>)

Assigns new data to the current selection based on the current data. The specified *function* is invoked for each element in the current selection, being passed the current datum `d` and index `i`, with the `this` context as the current DOM element. The return value of the function becomes the new data for the current DOM element, bound to `__data__`. This is conceptually similar to the built-in array [[map|https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/Map]] method, however this modifies the data bound to the current selection, rather than returning a new array. This operator has no effect on the index.

<a name="sort" href="Selections#wiki-sort">#</a> selection.<b>sort</b>(<i>comparator</i>)

Sorts the elements in the current selection according to the specified comparator function. The comparator function is passed two data elements *a* and *b* to compare, returning either a negative, positive, or zero value. If negative, then *a* should be before *b*; if positive, then *a* should be after *b*; otherwise, *a* and *b* are considered equal and the order is arbitrary. Note that the sort is not guaranteed to be stable; however, it is guaranteed to have the same behavior as your browser's built-in [[sort|https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/sort]] method on arrays.

### Animation & Interaction

<a name="on" href="Selections#wiki-on">#</a> selection.<b>on</b>(<i>type</i>, <i>listener</i>)

Adds or removes an event *listener* to each element in the current selection, for the specified *type*. The *type* is a string event type name, such as "click", "mouseover", or "submit". If an event listener was already registered for the same type on the selected element, the existing listener is removed before the new listener is added. To register multiple listeners for the same event type, the type may be followed by an optional namespace, such as "click.foo" and "click.bar". The specified *listener* is invoked in the same manner as other operator functions, being passed the current datum `d` and index `i`, with the `this` context as the current DOM element. To access the current event, use the global [d3.event](Selections#wiki-d3_event).

<a name="d3_event" href="Selections#wiki-d3_event">#</a> d3.<b>event</b>

Stores the current event, if any. This global is during an event listener callback registered with the [on](Selections#wiki-on) operator. The current event is reset after the listener is notified in a finally block. This allows the listener function to have the same form as other operator functions, being passed the current datum `d` and index `i`.

<a name="transition" href="Selections#wiki-transition">#</a> selection.<b>transition</b>()

Starts a [[transition|Transitions]] for the current selection. Transitions behave much like selections, except operators animate smoothly over time rather than applying instantaneously.

### Subselections

Whereas the top-level select methods query the entire document, a selection's [select](Selections#wiki-select) and [selectAll](Selections#wiki-selectAll) operators restrict queries to descendants of each selected element; we call this "subselection". For example, `d3.selectAll("p").select("b")` returns the first bold ("b") elements in every paragraph ("p") element. Subselecting via selectAll groups elements by ancestor. Thus, `d3.selectAll("p").selectAll("b")` groups by paragraph, while `d3.selectAll("p b")` returns a flat selection. Subselecting via select is similar, but preserves groups and propagates data. Grouping plays an important role in the data join, and functional operators may depend on the numeric index of the current element within its group.

<a name="select" href="Selections#wiki-select">#</a> selection.<b>select</b>(<i>selector</i>)

For each element in the current selection, selects the first descendant element that matches the specified *selector* string. If no element matches the specified selector for the current element, the element at the current index will be null in the returned selection; operators (with the exception of [data](Selections#wiki-data)) automatically skip null elements, thereby preserving the index of the existing selection. If the current element has associated data, this data is inherited by the returned subselection, and automatically bound to the newly selected elements. If multiple elements match the selector, only the first matching element in document traversal order will be selected.

The *selector* may also be specified as a function that returns an element, or null if there is no matching element. In this case, the specified *selector* is invoked in the same manner as other operator functions, being passed the current datum `d` and index `i`, with the `this` context as the current DOM element. 

<a name="selectAll" href="Selections#wiki-selectAll">#</a> selection.<b>selectAll</b>(<i>selector</i>)

For each element in the current selection, selects descendant elements that match the specified *selector* string. The returned selection is grouped by the ancestor node in the current selection. If no element matches the specified selector for the current element, the group at the current index will be empty in the returned selection. The subselection does not inherit data from the current selection; however, if the [data](Selections#wiki-data) value is specified as a function, this function will be based the data `d` of the ancestor node and the group index `i`.

Grouping by selectAll also affects subsequent entering placeholder nodes. Thus, to specify the parent node when appending entering nodes, use select followed by selectAll:

```javascript
d3.select("body").selectAll("div")
```

You can see the parent node of each group by inspecting the `parentNode` property of each group array, such as `selection[0].parentNode`.

The *selector* may also be specified as a function that returns an array of elements (or a NodeList), or the empty array if there are no matching elements. In this case, the specified *selector* is invoked in the same manner as other operator functions, being passed the current datum `d` and index `i`, with the `this` context as the current DOM element. 

### Control

For advanced usage, D3 has a few additional operators for custom control flow.

<a name="each" href="Selections#wiki-each">#</a> selection.<b>each</b>(<i>function</i>)

Invokes the specified *function* for each element in the current selection, passing in the current datum `d` and index `i`, with the `this` context of the current DOM element. This operator is used internally by nearly every other operator, and can be used to invoke arbitrary code for each selected element. The each operator can be used to process selections recursively, by using `d3.select(this)` within the callback function.

<a name="call" href="Selections#wiki-call">#</a> selection.<b>call</b>(<i>function</i>[, <i>arguments…</i>])

Invokes the specified *function* once, passing in the current selection along with any optional *arguments*. The call operator always returns the current selection, regardless of the return value of the specified function. The call operator is identical to invoking a function by hand; but it makes it easier to use method chaining. For example, say we want to set a number of attributes the same way in a number of different places. So we take the code and wrap it in a reusable function:

```javascript
function foo(selection) {
  selection
      .attr("name1", "value1")
      .attr("name2", "value2");
}
```

Now, we can say this:

```javascript
foo(d3.selectAll("div"))
```

Or equivalently:

```javascript
d3.selectAll("div").call(foo);
```

The `this` context of the called function is also the current selection. This is slightly redundant with the first argument, which we might fix in the future.

<a name="empty" href="Selections#wiki-empty">#</a> selection.<b>empty</b>()

Returns true if the current selection is empty; a selection is empty if it contains no non-null elements.

<a name="node" href="Selections#wiki-node">#</a> selection.<b>node</b>()

Returns the first non-null element in the current selection. If the selection is empty, returns null.
