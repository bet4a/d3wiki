> [Wiki](Home) ▸ [[Geometry]] ▸ **Quadtree Geom**

A quadtree is a two-dimensional recursive spatial subdivision. This implementation uses square partitions, dividing each square into four equally-sized squares. Each point exists in a unique node; if multiple points are in the same position, some points may be stored on internal nodes rather than leaf nodes. Quadtrees can be used to accelerate various spatial operations, such as the Barnes-Hut approximation for computing n-body forces, or collision detection.

<a name="quadtree" href="#wiki-quadtree">#</a> d3.geom.<b>quadtree</b>([<i>points</i>, [<i>x1</i>, <i>y1</i>, <i>x2</i>, <i>y2</i> | <i>width</i>, <i>height</i>]])

<a href="http://bl.ocks.org/4343214"><img src="https://raw.github.com/gist/4343214/thumbnail.png" width="202"></a>

**Deprecated:** If *points* is specified, constructs a new quadtree for the specified array of points. Bounds are optional and can be specified explicitly as *x1*, *y1*, *x2*, *y2*, or as *width*, *height*, which is equivalent to *0*, *width*, *0*, *height*. Points are assumed to be of the form `{x: …, y: …}`.

<a name="_quadtree" href="Quadtree-Geom#wiki-_quadtree">#</a> <b>quadtree</b>(<i>points</i>)

Constructs a new quadtree for the specified array of points.

<a name="add" href="#wiki-add">#</a> quadtree.<b>add</b>(<i>point</i>)

Adds a new point to the quadtree.

<a name="visit" href="#wiki-visit">#</a> quadtree.<b>visit</b>(<i>callback</i>)

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

<a name="size" href="#wiki-size">#</a> quadtree.<b>size</b>([<i>size</i>])

If the specified *size* is null, this causes the quadtree size to be automatically computed for the initial array of points.  If the specified *size* is a two-element array, [width, height], this sets the quadtree's size.

If *size* is not specified, returns the current size, which defaults to null.