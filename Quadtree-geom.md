A quadtree is a two-dimensional recursive spatial subdivision; see [bl.ock 4343214](http://bl.ocks.org/4343214) for an example.

This implementation uses square partitions, dividing each square into four equally-sized squares. Each point exists in a unique node; if multiple points are in the same position, some points may be stored on internal nodes rather than leaf nodes. Quadtrees can be used to accelerate various spatial operations, such as the Barnes-Hut approximation for computing n-body forces, or collision detection.

<a name="quadtree" href="#wiki-quadtree">#</a> d3.geom.<b>quadtree</b>(<i>point</i>, [<i>x1</i>, <i>y1</i>, <i>x2</i>, <i>y2</i>])

Constructs a new quadtree for the specified array of points.

<a name="add" href="#wiki-add">#</a> quadtree.<b>add</b>(<i>point</i>)

Adds a new point to the quadtree.

<a name="visit" href="#wiki-visit">#</a> quadtree.<b>visit</b>(<i>callback</i>)

The specified *callback* is invoked with the arguments (*node*, *x1*, *y1*, *x2*, *y2*) for each quadtree node pre-order.