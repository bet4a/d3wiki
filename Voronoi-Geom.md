> [Wiki](Home) ▸ [[API Reference]] ▸ [[Geometry]] ▸ **Voronoi Geom**

Voronoi layouts are particularly useful for invisible interactive regions, as demonstrated in Nate Vack’s [Voronoi picking](http://bl.ocks.org/njvack/1405439) example. See Tovi Grossman’s paper on [bubble cursors](http://www.tovigrossman.com/BubbleCursor) for a related concept.

<a name="voronoi" href="#wiki-voronoi">#</a> d3.geom.<b>voronoi</b>()

<a href="http://bl.ocks.org/4060366"><img src="https://raw.github.com/gist/4060366/thumbnail.png" width="202"></a>

Creates a Voronoi layout with default accessors.

<a name="_voronoi" href="#wiki-_voronoi">#</a> <b>voronoi</b>(<i>data</i>)

Returns an array of polygons, one for each input vertex in the specified *data* array. If any vertices are coincident or have NaN positions, *the behavior of this method is undefined*: most likely, invalid polygons will be returned! You should filter invalid vertices, and consolidate coincident vertices, before computing the tessellation.

<a name="x" href="#wiki-x">#</a> voronoi.<b>x</b>([<i>x</i>])

If *x* is specified, sets the x-coordinate accessor. If *x* is not specified, returns the current x-coordinate accessor, which defaults to:

```js
function(d) { return d[0]; }
```

<a name="y" href="#wiki-y">#</a> voronoi.<b>y</b>([<i>y</i>])

If *y* is specified, sets the y-coordinate accessor. If *y* is not specified, returns the current y-coordinate accessor, which defaults to:

```js
function(d) { return d[1]; }
```

<a name="size" href="#wiki-size">#</a> voronoi.<b>size</b>([<i>size</i>])

Get or set the clip size of the Voronoi layout. This implementation does not clip the returned polygons by default, but will clip them to a rectangle of the given size if specified. This is strongly recommended, as unclipped polygons may have large coordinates which do not display correctly. You can also employ custom clipping without specifying a size, either in SVG or by post-processing with [polygon.clip](Polygon-Geom#wiki-clip), as in [this example](http://bl.ocks.org/4237768). 

<a name="links" href="#wiki-links">#</a> voronoi.<b>links</b>(<i>data</i>)

…

<a name="triangles" href="#wiki-triangles">#</a> voronoi.<b>triangles</b>(<i>data</i>)

<a href="http://bl.ocks.org/4341156"><img src="https://raw.github.com/gist/4341156/thumbnail.png" width="202"></a>

Returns an array of triangles.