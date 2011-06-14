> [[API Reference]] ▸ [[Layouts]]

The **cluster layout** produces [dendrograms](http://en.wikipedia.org/wiki/Dendrogram): node-link diagrams that place leaf nodes of the tree at the same depth. For example, a cluster layout can be used to organize software classes in a package hierarchy:

[![cluster](cluster.png)](http://mbostock.github.com/d3/ex/cluster.html)

The cluster layout is part of D3's family of [[hierarchical|Hierarchical-Layout]] layouts. These layouts follow the same basic structure: the input argument to the layout is the root node of the hierarchy, and the output return value is an array representing the computed positions of all nodes. The layout has a size in *x* and *y*, but this represents an arbitrary coordinate system; for example, you can treat *x* as a radius and *y* as an angle to produce a radial rather than Cartesian layout.

The layout object returned by d3.layout.cluster is both an object and a function. That is: you can call the layout like any other function, and the layout has additional methods that change its behavior. Like other classes in D3, layouts follow the method chaining pattern where setter methods return the layout itself, allowing multiple setters to be invoked in a concise statement.

<a name="cluster" href="#cluster">#</a> d3.layout.<b>cluster</b>()

Creates a new cluster layout with the default settings. The default sort order is null. The default children accessor assumes each input node is an object with a `children` array. The default separation function uses one node width for siblings, and two node widths for non-siblings. The default size is 1×1.

<a name="sort" href="#sort">#</a> cluster.<b>sort</b>([<i>comparator</i>])

If *comparator* is specified, sets the sort order of sibling nodes for the layout using the specified comparator function.  If *comparator* is not specified, returns the current group sort order, which defaults to null for no sorting. The comparator function is invoked for pairs of nodes, being passed the input data for each node. The default comparator is null, which disables sorting and uses tree traversal order. For example, to sort sibling nodes in descending order by the associated input data's numeric value attribute, say:

```javascript
function comparator(a, b) {
  return b.value - a.value;
}
```

Sorting by the node's name or key is also common. This can be done easily using [d3.ascending](Arrays#d3_ascending) or [d3.descending](Arrays#d3_descending).

<a name="children" href="#children">#</a> cluster.<b>children</b>([<i>children</i>])

<a name="links" href="#links">#</a> cluster.<b>links</b>(<i>nodes</i>)

<a name="separation" href="#separation">#</a> cluster.<b>separation</b>([<i>separation</i>])

<a name="size" href="#size">#</a> cluster.<b>size</b>([<i>size</i>])
