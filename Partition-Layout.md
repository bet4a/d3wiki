> [[API Reference]] ▸ [[Layouts]]

The **partition layout** produces adjacency diagrams: a space-filling variant of a node-link tree diagram. Rather than drawing a link between parent and child in the hierarchy, nodes are drawn as solid areas (either arcs or rectangles), and their placement relative to other nodes reveals their position in the hierarchy. The size of the nodes encodes a quantitative dimension that would be difficult to show in a node-link diagram.

![partition](partition.png)

Like most other layouts, the object returned by d3.layout.partition is both an object and a function. That is: you can call the layout like any other function, and the layout has additional methods that change its behavior. Like other classes in D3, layouts follow the method chaining pattern where setter methods return the layout itself, allowing multiple setters to be invoked in a concise statement.

<a name="partition" href="#partition">#</a> d3.layout.<b>partition</b>()

Creates a new partition layout with the default settings: the default sort order is by descending value; the default value accessor assumes each input data is an object with a value number; the default children accessor assumes each input data is an object with a children array; the default size is 1×1.

The partition layout is part of D3's family of [[hierarchical|Hierarchical-Layout]] layouts. These layouts follow the same basic structure: the input argument to the layout is the root node of the hierarchy, and the output return value is an array representing the computed positions of all nodes. Note that these position objects are not the same as the input data passed to the layout function; the computed layout nodes wrap the data objects, and provide several attributes:

* parent - the parent node, or null for the root.
* children - the array of child nodes, or null for leaf nodes.
* value - the node value, as returned by the value accessor.
* depth - the depth of the node, starting at 0 for the root.
* x - the minimum *x*-coordinate of the node position.
* y - the minimum *y*-coordinate of the node position.
* dx - the *x*-extent of the node position. 
* dy - the *y*-extent of the node position. 
* data - the underlying data represented by this node.

Although the layout has a size in *x* and *y*, this represents an arbitrary coordinate system; for example, you can treat *x* as a radius and *y* as an angle to produce a radial rather than Cartesian layout. In Cartesian orientation, *x*, *y*, *dx* and *dy* correspond to the "x", "y", "width" and "height" attributes of the SVG [[rect|SVG-Shapes#svg_rect]] element. In radial orientation, they can be used to compute the innerRadius, startAngle, outerRadius and endAngle of an [[arc|SVG-Shapes#arc]] generator. The Cartesian orientation may be called an **icicle tree**, while the radial orientation is called a **sunburst**.

<a name="sort" href="#sort">#</a> partition.<b>sort</b>([<i>comparator</i>])

If *comparator* is specified, sets the sort order of sibling nodes for the layout using the specified comparator function.  If *comparator* is not specified, returns the current group sort order, which defaults to descending order by the associated input data's numeric value attribute:

```javascript
function comparator(a, b) {
  return b.value - a.value;
}
```

The comparator function is invoked for pairs of nodes, being passed the input data for each node. A null comparator disables sorting and uses tree traversal order. Comparator functions may also be implemented using [d3.ascending](Arrays#d3_ascending) or [d3.descending](Arrays#d3_descending).

<a name="children" href="#children">#</a> partition.<b>children</b>([<i>children</i>])

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

<a name="links" href="#links">#</a> partition.<b>links</b>(<i>nodes</i>)

Given the specified array of *nodes*, such as the computed nodes returned by the cluster layout, returns an array of objects representing the links from parent to child for each node. Leaf nodes will not have any links. Each link is an object with two attributes:

* source - the parent node (as described above).
* target - the child node.

This method is useful for retrieving a set of link descriptions suitable for display, often in conjunction with the [diagonal](SVG-Shapes#diagonal) shape generator. For example:

```javascript
svg.selectAll("path")
    .data(cluster.links(nodes))
  .enter().append("svg:path")
    .attr("d", d3.svg.diagonal());
```

<a name="value" href="#value">#</a> partition.<b>value</b>([<i>value</i>])

If *value* is specified, sets the value accessor to the specified function. If *value* is not specified, returns the current value accessor, which assumes that the input data is an object with a numeric value attribute:

```javascript
function value(d) {
  return d.value;
}
```

The value accessor is invoked for each input data element, and must return a number representing the numeric value of the node. This value is used to set the area of each node proportionally to the value.

<a name="size" href="#size">#</a> partition.<b>size</b>([<i>size</i>])

If *size* is specified, sets the available layout size to the specified two-element array of numbers representing *x* and *y*. If *size* is not specified, returns the current size, which defaults to 1×1.
