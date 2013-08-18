> [Wiki](Home) ▸ [[Geometry]] ▸ **Quadtree Geom**

A **quadtree** is a two-dimensional recursive spatial subdivision. This implementation uses square partitions, dividing each square into four equally-sized squares. Each point exists in a unique node; if multiple points are in the same position, some points may be stored on internal nodes rather than leaf nodes. Quadtrees can be used to accelerate various spatial operations, such as the Barnes-Hut approximation for computing n-body forces, or collision detection.

<a href="http://bl.ocks.org/4343214"><img src="https://raw.github.com/gist/4343214/thumbnail.png" width="202"></a>
<a href="http://bl.ocks.org/6216724"><img src="https://raw.github.com/gist/6216724/thumbnail.png" width="202"></a>
<a href="http://bl.ocks.org/6224050"><img src="https://raw.github.com/gist/6224050/thumbnail.png" width="202"></a>

<a name="quadtree" href="#wiki-quadtree">#</a> d3.geom.<b>quadtree</b>()

Creates a new quadtree layout with the default *x*-accessor and *y*-accessor (that assume the input data is a two-element array of numbers; see below for details). The default extent is null, such that it will be computed automatically from the input points.

<a name="_quadtree" href="Quadtree-Geom#wiki-_quadtree">#</a> <b>quadtree</b>(<i>points</i>)

Constructs a new quadtree for the specified array of points. Returns the root of the quadtree. Each node in the quadtree has several properties:

* _nodes_ - a sparse array of the four child nodes in order: top-left, top-right, bottom-left, bottom-right
* _leaf_ - a boolean indicating whether this is a internal or leaf node
* _point_ - the point associated with this node, if any (may apply to either internal or leaf nodes)
* _x_ - the _x_-coordinate of the associated point, if any
* _y_ - the _y_-coordinate of the associated point, if any

In addition, the returned *root* node defines [add](#wiki-add) and [visit](#wiki-visit) methods.

<a name="add" href="#wiki-add">#</a> root.<b>add</b>(<i>point</i>)

Adds a new point to the previously-computed quadtree.

<a name="visit" href="#wiki-visit">#</a> root.<b>visit</b>(<i>callback</i>)

The specified *callback* is invoked with the arguments (<i>node</i>, *x1*, *y1*, *x2*, *y2*) for each quadtree node pre-order, provided the *callback* returns false. If *callback* returns true for a node, then the children of that node are not visited.

<a name="x" href="#wiki-x">#</a> quadtree.<b>x</b>([<i>x</i>])

If *x* is specified, sets the x-coordinate accessor. If *x* is not specified, returns the current x-coordinate accessor, which defaults to:

```js
function(d) { return d[0]; }
```

<a name="y" href="#wiki-y">#</a> quadtree.<b>y</b>([<i>y</i>])

If *y* is specified, sets the y-coordinate accessor. If *y* is not specified, returns the current y-coordinate accessor, which defaults to:

```js
function(d) { return d[1]; }
```

<a name="extent" href="#wiki-extent">#</a> quadtree.<b>extent</b>([<i>extent</i>])

If the specified *extent* is null, this causes the quadtree extent to be automatically computed for the initial array of points.  If the specified *extent* is a two-dimensional array [‍[ *x0*, *y0* ], [ *x1*, *y1* ]], where *x0* and *y0* are the lower bounds of the extent, and *x1* and *y1* are the upper bounds of the extent, this sets the quadtree's extent.

If *extent* is not specified, returns the current extent, which defaults to null.