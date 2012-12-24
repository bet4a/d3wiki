> [Wiki](Home) ▸ [[API Reference]] ▸ [[Geometry]] ▸ **Voronoi Geom**

This implementation does not clip the returned polygons, so if you want to clip them to a particular shape you will need to do that either in SVG or by post-processing with [polygon.clip](Polygon-Geom#wiki-clip), as in [this Voronoi clipping example](http://bl.ocks.org/4237768). If any vertices are coincident or have NaN positions, *the behavior of this method is undefined*: most likely, invalid polygons will be returned! You should filter invalid vertices, and consolidate coincident vertices, before computing the tessellation.

<a name="voronoi" href="Voronoi-Geom#wiki-voronoi">#</a> d3.geom.<b>voronoi</b>([<i>vertices</i>])

Returns an array of polygons, one for each input *vertex*.

<a name="delaunay" href="Voronoi-Geom#wiki-delaunay">#</a> d3.geom.<b>delaunay</b>([<i>vertices</i>])

Returns an array of triangles.