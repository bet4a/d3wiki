# Selections

D3's atomic operand is the selection: a filtered set of elements queried from the current document. Operators act on selections, modifying content. Data joins bind input data to elements, enabling functional operators that depend on data, and producing enter and exit subselections for the creation and destruction of elements in correspondence with data.

D3 adopts the W3C Selectors API to identify document elements for selection; this mini-language consists of predicates that filter elements by tag (“tag”), class (“.class”), unique identifier (“#id”), attribute (“[name=value]”), containment (“parent child”), adjacency (“before ∼ after”), and various other facets. Predicates can be intersected (“.a.b”) or unioned (“.a, .b”), resulting in a rich but concise selection method.

These methods accept the selector mini-language; the former selects only the first element that matches the predicates, while the latter selects all matching elements in document traversal order. These methods also accept node references directly, for when nodes are accessed through external means such as a third-party library or developer tool.

Any number of operators can be applied to selected elements. These operators wrap the W3C DOM API, setting attributes (attr), styles (style), properties (property), HTML (html) and text (text) content. Operator values are specified either as constants or functions; the latter are evaluated for each element. While the built-in operators satisfy most needs, the each operator invokes an arbitrary JavaScript callback for total generality. Since each selection is simply an array, elements can also be accessed directly (e.g., [0]).

D3 supports method chaining for brevity when applying multiple operators: the operator return value is the selection. The append and insert operators add a new element for each element in the current selection, returning the added nodes, thus allowing the convenient creation of nested structures. The remove operator discards selected elements.

Whereas the top-level select methods query the entire document, a selection’s select and selectAll operators restrict queries to descendants of each selected element; we call this subselection. For example, d3.selectAll("p").select("b") returns the first bold (“b”) elements in every paragraph (“p”) element.

Subselecting via selectAll groups elements by ancestor. Thus, d3.selectAll("p").selectAll("b") groups by paragraph, while d3.selectAll("p b") returns a flat selection. Subselect- ing via select is similar, but preserves groups and propagates data. Grouping plays an important role in the data join, and functional operators may depend on the numeric index of the current element within its group.

## Generating Selections

> <b>d3.select</b>(<i>selector</i>) <a name="d3_select"></a>

…

> <b>d3.selectAll</b>(<i>selector</i>)

…

## Working with Selections

> selection.<b>select</b>(<i>selector</i>)

…

> selection.<b>selectAll</b>(<i>selector</i>)

…
