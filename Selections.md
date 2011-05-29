# Selections

A selection is an array of elements from the current document. D3 uses [[CSS3 Selectors|http://www.w3.org/TR/css3-selectors/]] to select elements. For example, you can select by tag ("tag"), class (".class"), unique identifier ("#id"), attribute ("[name=value]"), or containment ("parent child"). Selectors can also be intersected (".a.b") or unioned (".a, .b"). If your browser does not support the [[W3C Selectors API|http://www.w3.org/TR/selectors-api/]], you can include [[Sizzle|http://sizzlejs.com/]] before D3 for backwards-compatibility.

After selecting elements, you apply operators to them. These operators wrap the [[W3C DOM API|http://www.w3.org/TR/DOM-Level-3-Core/]], setting attributes (`attr`), styles (`style`), properties (`property`), HTML (`html`) and text (`text`) content. Operator values are specified either as constants or functions; the latter are evaluated for each element. While the built-in operators satisfy most needs, the `each` operator invokes an arbitrary JavaScript callback for total generality. Since each selection is simply an array, elements can also be accessed directly (e.g., `[0]`).

D3 supports method chaining for brevity when applying multiple operators: the operator return value is the selection. The `append` and `insert` operators add a new element for each element in the current selection, returning the added nodes, thus allowing the convenient creation of nested structures. The `remove` operator discards selected elements.

You can also join selections to data; this data is available to operators for data-driven transformations. In addition, joining to data produces *enter* and *exit* subselections, so that you may add or remove elements in response to changes in data.

## Generating Selections

D3 provides two top-level methods for selecting elements, called `select` and `selectAll`. These methods accept selectors; the former selects only the first matching element, while the latter selects *all* matching elements in document traversal order. These methods also directly accept nodes, which is useful for integration with third-party libraries (such as jQuery) or developer tools (`$0`). Another common use of selecting a node reference is `d3.select(this)` from within an event listener.

> <b>d3.select</b>(<i>selector</i>) <a name="d3_select"></a><br>
> <b>d3.select</b>(<i>node</i>)

…

> <b>d3.selectAll</b>(<i>selector</i>) <a name="d3_selectAll"></a><br>
> <b>d3.selectAll</b>(<i>nodes</i>)

…

## Working with Selections

Whereas the top-level select methods query the entire document, a selection’s select and selectAll operators restrict queries to descendants of each selected element; we call this subselection. For example, d3.selectAll("p").select("b") returns the first bold (“b”) elements in every paragraph (“p”) element.

> selection.<b>select</b>(<i>selector</i>)

…

> selection.<b>selectAll</b>(<i>selector</i>)

Subselecting via selectAll groups elements by ancestor. Thus, d3.selectAll("p").selectAll("b") groups by paragraph, while d3.selectAll("p b") returns a flat selection. Subselect- ing via select is similar, but preserves groups and propagates data. Grouping plays an important role in the data join, and functional operators may depend on the numeric index of the current element within its group.
