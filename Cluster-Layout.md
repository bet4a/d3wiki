> [[API Reference]] ▸ [[Layouts]]

The **cluster layout** produces [dendrograms](http://en.wikipedia.org/wiki/Dendrogram): node-link diagrams that place leaf nodes of the tree at the same depth. For example, a cluster layout can be used to organize software classes in a package hierarchy:

[![cluster](cluster.png)](http://mbostock.github.com/d3/ex/cluster.html)

Like most other layouts, the object returned by d3.layout.cluster is both an object and a function. That is: you can call the layout like any other function, and the layout has additional methods that change its behavior. Like other classes in D3, layouts follow the method chaining pattern where setter methods return the layout itself, allowing multiple setters to be invoked in a concise statement.

<a name="cluster" href="#cluster">#</a> d3.layout.<b>cluster</b>()

Creates a new cluster layout with the default settings: the default sort order is null; the default children accessor assumes each input node is an object with a children array; the default separation function uses one node width for siblings, and two node widths for non-siblings; the default size is 1×1.

The cluster layout is part of D3's family of [[hierarchical|Hierarchical-Layout]] layouts. These layouts follow the same basic structure: the input argument to the layout is the root node of the hierarchy, and the output return value is an array representing the computed positions of all nodes.  Note that these are not the same as the input data passed to the layout function; the computed layout nodes wrap the data objects, and provide several attributes:

* parent - the parent node, or null for the root.
* children - the array of child nodes, or null for leaf nodes.
* depth - the depth of the node, starting at 0 for the root.
* x - the computed *x*-coordinate of the node position.
* y - the computed *y*-coordinate of the node position.
* data - the underlying data represented by this node.

Although the layout has a size in *x* and *y*, this represents an arbitrary coordinate system; for example, you can treat *x* as a radius and *y* as an angle to produce a radial rather than Cartesian layout.

<a name="sort" href="#sort">#</a> cluster.<b>sort</b>([<i>comparator</i>])

If *comparator* is specified, sets the sort order of sibling nodes for the layout using the specified comparator function.  If *comparator* is not specified, returns the current group sort order, which defaults to null for no sorting. The comparator function is invoked for pairs of nodes, being passed the input data for each node. The default comparator is null, which disables sorting and uses tree traversal order. For example, to sort sibling nodes in descending order by the associated input data's numeric value attribute, say:

```javascript
function comparator(a, b) {
  return b.value - a.value;
}
```

Sorting by the node's name or key is also common. This can be done easily using [d3.ascending](Arrays#d3_ascending) or [d3.descending](Arrays#d3_descending).

<a name="children" href="#children">#</a> cluster.<b>children</b>([<i>children</i>])

If *children* is specified, sets the specified children accessor function. If *children* is not specified, returns the current children accessor function, which by default assumes that the input data is an object with a children array:

```javascript
function children(d) {
  return d.children;
}
```

The children accessor is first invoked for root node in the hierarchy. If the accessor returns null, then the node is assumed to be a leaf node at the layout traversal terminates. Otherwise, the accessor should return an array of data elements representing the child nodes.

Often, it is convenient to load the node hierarchy using [d3.json](Requests#d3_json), and represent the input hierarchy efficiently as a nested [JSON](http://json.org) object, rather than an explicit array of children. In this case, the leaf nodes of the hierarchy may be simple numbers rather than objects. Using the *children* accessor function, you can easily tell the layout how to traverse the input hierarchy. For example, if the input is:

```javascript
{
  "analytics": {
    "cluster": {
      "AgglomerativeCluster": 3938,
      "CommunityStructure": 3812,
      "MergeEdge": 743
    },
    "graph": {
      "BetweennessCentrality": 3534,
      "LinkDistance": 5731
    }
  }
}
```

Then a suitable *children* accessor will iterate over the values in each object, if the current node is an object, or return null for non-objects to indicate that the specified input is a leaf node:

```javascript
function children(d) {
  return isNaN(d) ? d3.values(d) : null;
}
```

However, note that with this accessor, the data associated with each node will only have access to the child nodes, and will not know its own key! To store the name of the current node, in addition to the child nodes, we can use the [d3.entries](Arrays#d3_entries) helper:

```javascript
function children(d) {
  return isNaN(d.value) ? d3.values(d.value) : null;
}
```

With this children accessor, the input to the layout must itself be an object with key and value attributes. This can be achieved by saying d3.entries(*object*)[0], where *object* is the root JSON object.

<a name="links" href="#links">#</a> cluster.<b>links</b>(<i>nodes</i>)

<a name="separation" href="#separation">#</a> cluster.<b>separation</b>([<i>separation</i>])

<a name="size" href="#size">#</a> cluster.<b>size</b>([<i>size</i>])
