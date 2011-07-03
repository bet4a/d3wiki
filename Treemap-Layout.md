> [[API Reference]] ▸ [[Layouts]]

Introduced by [Ben Shneiderman](http://www.cs.umd.edu/hcil/treemap-history/) in 1991, a **treemap** recursively subdivides area into rectangles. As with [adjacency diagrams](Partition-Layout), the size of any node in the tree is quickly revealed. “Squarified” treemaps use approximately-square rectangles, which offer better readability and size estimation than naïve “slice-and-dice” subdivision. Fancier algorithms such as [Voronoi](http://portal.acm.org/citation.cfm?id=1056018.1056041) and [jigsaw](http://www.research.ibm.com/visual/papers/158-wattenberg-final3.pdf) treemaps also exist but are less common.

![treemap](treemap.png)

Like other classes in D3, layouts follow the method chaining pattern where setter methods return the layout itself, allowing multiple setters to be invoked in a concise statement.

<a name="treemap" href="#treemap">#</a> d3.layout.<b>treemap</b>()

Creates a new treemap layout with the default settings: the default sort order is by descending value; the default value accessor assumes each input data is an object with a numeric value attribute; the default children accessor assumes each input data is an object with a children array; the default size is 1×1.

<a name="sort" href="#sort">#</a> treemap.<b>sort</b>([<i>comparator</i>])

If *comparator* is specified, sets the sort order of sibling nodes for the layout using the specified comparator function.  If *comparator* is not specified, returns the current group sort order, which defaults to descending order by the associated input data's numeric value attribute:

```javascript
function comparator(a, b) {
  return b.value - a.value;
}
```

The comparator function is invoked for pairs of nodes, being passed the input data for each node. A null comparator disables sorting and uses tree traversal order. Comparator functions may also be implemented using [d3.ascending](Arrays#d3_ascending) or [d3.descending](Arrays#d3_descending).

<a name="children" href="#children">#</a> treemap.<b>children</b>([<i>children</i>])

If *children* is specified, sets the specified children accessor function. If *children* is not specified, returns the current children accessor function, which by default assumes that the input data is an object with a children array:

```javascript
function children(d) {
  return d.children;
}
```

Often, it is convenient to load the node hierarchy using [d3.json](Requests#d3_json), and represent the input hierarchy as a nested [JSON](http://json.org) object. For example:

```javascript
{
 "name": "flare",
 "children": [
  {
   "name": "analytics",
   "children": [
    {
     "name": "cluster",
     "children": [
      {"name": "AgglomerativeCluster", "size": 3938},
      {"name": "CommunityStructure", "size": 3812},
      {"name": "MergeEdge", "size": 743}
     ]
    },
    {
     "name": "graph",
     "children": [
      {"name": "BetweennessCentrality", "size": 3534},
      {"name": "LinkDistance", "size": 5731}
     ]
    }
   ]
  }
 ]
}
```

The children accessor is first invoked for root node in the hierarchy. If the accessor returns null, then the node is assumed to be a leaf node at the layout traversal terminates. Otherwise, the accessor should return an array of data elements representing the child nodes.

<a name="nodes" href="#nodes">#</a> treemap.<b>nodes</b>(<i>root</i>)

<a name="links" href="#links">#</a> treemap.<b>links</b>(<i>nodes</i>)

<a name="value" href="#value">#</a> treemap.<b>value</b>([<i>value</i>])

<a name="size" href="#size">#</a> treemap.<b>size</b>([<i>size</i>])

<a name="round" href="#round">#</a> treemap.<b>round</b>([<i>round</i>])

<a name="sticky" href="#sticky">#</a> treemap.<b>sticky</b>([<i>sticky</i>])
