> [Wiki](Home) ▸ [[API Reference]] ▸ [[Geometry]] ▸ **Hull Geom**

<a name="hull" href="Hull-Geom#wiki-hull">#</a> d3.geom.<b>hull</b>([<i>vertices</i>])

<a href="http://bl.ocks.org/4341699"><img src="https://raw.github.com/gist/4341699/thumbnail.png" width="202"></a>

If *vertices* is specified, returns their convex hull, using the default x- and y-coordinate accessors.  The convex hull is represented by an array containing a subset of the input vertices, arranged in clockwise order.

If *vertices* is not specified, creates a new hull layout with the default settings.

<a name="x" href="Hull-Geom#wiki-x">#</a> hull.<b>x</b>([<i>x</i>])

If *x* is specified, sets the x-coordinate accessor.  If *x* is not specified, returns the current x-coordinate accessor, which defaults to:

```js
function(d) { return d[0]; }
```

<a name="y" href="Hull-Geom#wiki-y">#</a> hull.<b>y</b>([<i>y</i>])

If *y* is specified, sets the y-coordinate accessor.  If *y* is not specified, returns the current y-coordinate accessor, which defaults to:

```js
function(d) { return d[1]; }
```