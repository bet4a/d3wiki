> [Wiki](Home) ▸ [[Geometry]] ▸ **Quadtree Geom**

A **quadtree** is a two-dimensional recursive spatial subdivision. This implementation uses square partitions, dividing each square into four equally-sized squares. Each point exists in a unique node; if multiple points are in the same position, some points may be stored on internal nodes rather than leaf nodes. Quadtrees can be used to accelerate various spatial operations, such as the Barnes-Hut approximation for computing n-body forces, or collision detection.

<a href="http://bl.ocks.org/4343214"><img src="http://bl.ocks.org/mbostock/raw/4343214/thumbnail.png" width="202"></a>
<a href="http://bl.ocks.org/6216724"><img src="http://bl.ocks.org/mbostock/raw/6216724/thumbnail.png" width="202"></a>
<a href="http://bl.ocks.org/6224050"><img src="http://bl.ocks.org/mbostock/raw/6224050/thumbnail.png" width="202"></a>

<a name="quadtree" href="#wiki-quadtree">#</a> d3.geom.<b>quadtree</b>()

Creates a new quadtree factory with the default [_x_-accessor](#wiki-x), [_y_-accessor](#wiki-y) and [extent](#wiki-extent). The [returned function](#wiki-_quadtree) can be used to create any number of quadtrees from data with the factory’s configuration.

<a name="_quadtree" href="Quadtree-Geom#wiki-_quadtree">#</a> <b>quadtree</b>(<i>points</i>)

Constructs a new quadtree for the specified array of data _points_, returning the root node of a new quadtree. The _x_- and _y_-coordinates of each point are determined using the current [_x_-](#wiki-x) and [_y_-](#wiki-y) accessor functions. To build a quadtree by adding points incrementally, the specified _points_ array can be empty, and then points can be later [added](#wiki-add) to the returned root node; in this case, you must also specify the [extent](#wiki-extent) of the quadtree.

Each node in the quadtree has several properties:

* _nodes_ - a sparse array of the four child nodes in order: top-left, top-right, bottom-left, bottom-right
* _leaf_ - a boolean indicating whether this is a internal or leaf node
* _point_ - the point associated with this node, if any (may apply to either internal or leaf nodes)
* _x_ - the _x_-coordinate of the associated point, if any
* _y_ - the _y_-coordinate of the associated point, if any

The returned root node also defines [add](#wiki-add) and [visit](#wiki-visit) methods.

<a name="add" href="#wiki-add">#</a> root.<b>add</b>(<i>point</i>)

Adds the specified new _point_ to the quadtree.

<a name="visit" href="#wiki-visit">#</a> root.<b>visit</b>(<i>callback</i>)

Visits each node in the quadtree, invoking the specified *callback* with arguments {<i>node</i>, *x1*, *y1*, *x2*, *y2*} for each node. Nodes are traversed in pre-order. If the *callback* returns true for a the given node, then the children of that node are not visited; otherwise, all child nodes are visited.

<a name="x" href="#wiki-x">#</a> quadtree.<b>x</b>([<i>x</i>])

If *x* is specified, sets the x-coordinate accessor and returns this quadtree factory. If *x* is not specified, returns the current _x_-coordinate accessor, which defaults to:

```js
function(d) { return d[0]; }
```

For each point added to the quadtree, either during [initial construction](#wiki-_quadtree) or lazily [added](#wiki-add), the _x_-accessor is invoked with the arguments {<i>d</i>, <i>i</i>}, where _d_ is the current point and _i_ is its index in the array of all points. The _x_-accessor must then return a numeric value indicating the _x_-coordinate of the given point. The _x_-accessor may also be defined as a constant number rather than a function, if desired.

<a name="y" href="#wiki-y">#</a> quadtree.<b>y</b>([<i>y</i>])

If *y* is specified, sets the y-coordinate accessor and returns this quadtree factory. If *y* is not specified, returns the current _y_-coordinate accessor, which defaults to:

```js
function(d) { return d[1]; }
```

For each point added to the quadtree, either during [initial construction](#wiki-_quadtree) or lazily [added](#wiki-add), the _y_-accessor is invoked with the arguments {<i>d</i>, <i>i</i>}, where _d_ is the current point and _i_ is its index in the array of all points. The _y_-accessor must then return a numeric value indicating the _y_-coordinate of the given point. The _y_-accessor may also be defined as a constant number rather than a function, if desired.

<a name="extent" href="#wiki-extent">#</a> quadtree.<b>extent</b>([<i>extent</i>])

If *extent* is specified, sets the current extent and returns this quadtree factory. If *extent* is not specified, returns the current extent, which defaults to null. When the extent is null, an extent will be computed automatically by scanning the array of input points passed to the [quadtree constructor](#wiki-_quadtree). Otherwise, the *extent* must be specified as a two-dimensional array [​[<i>x0</i>, <i>y0</i>], [​<i>x1</i>, <i>y1</i>]​], where *x0* and *y0* are the lower bounds of the extent, and *x1* and *y1* are the upper bounds of the extent. Setting an extent is required when constructing a quadtree lazily from an initially-empty set of nodes.