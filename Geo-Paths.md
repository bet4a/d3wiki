> [[API Reference]] ▸ [[Geo]]

For cartographic visualizations, D3 supports a handful of utilities for displaying and manipulating **geographic data**. These utilities are based on the [GeoJSON format](http://geojson.org/geojson-spec.html)—a standard way of representing geographic features in JavaScript. For example, [GDAL](http://www.gdal.org/) includes the ogr2ogr tool which can convert binary shapefiles into GeoJSON; the shapefile is another common representation for geographic data, frequently used by the [U.S. Census Bureau](http://www.census.gov/).

![choropleth](choropleth.png)

Some other tools you may be interested in:

* [Shapely](http://trac.gispython.org/lab/wiki/Shapely) - manipulation of planar geometry objects.
* [MapShaper](http://mapshaper.org/) and [Bloch](https://github.com/migurski/Bloch/) - shapefile simplification.
* [ColorBrewer](http://colorbrewer2.org) - color scales for maps.
* [PostGIS](http://postgis.refractions.net/) - a geospatial database.

The primary mechanism for displaying geographic data is [d3.geo.path](#path). In many ways, this class is similar to [d3.svg.line](SVG-Shapes#line) and the other SVG shape generators: given a geometry or feature object, it generates the path data string suitable for the "d" attribute of an SVG path element.

<a name="path" href="#path">#</a> d3.geo.<b>path</b>()

Creates a new geographic path generator with the default settings: the [albersUsa](Geo-Projections#albersUsa) projection and a point radius of 4.5 pixels.

<a name="_path" href="#_path">#</a> <b>path</b>(<i>feature</i>[, <i>index</i>])

Returns the path data string for the given *feature*, which may be any GeoJSON feature or geometry object:

* Point - a single position.
* MultiPoint - an array of positions.
* LineString - an array of positions forming a continuous line.
* MultiLineString - an array of arrays of positions forming several lines.
* Polygon - an array of arrays of positions forming a polygon (possibly with holes).
* MultiPolygon - a multidimensional array of positions forming multiple polygons.
* GeometryCollection - an array of geometry objects.
* Feature - a feature containing one of the above geometry objects.
* FeatureCollection - an array of feature objects.

For example, to display multiple features:

```javascript
vis.selectAll("path")
    .data(features)
  .enter().append("svg:path")
    .attr("d", d3.geo.path());
```

An optional *index* may be specified, which is passed along to the [pointRadius](#pointRadius) accessor. Note: you probably want to specify the style property "fill-rule" as "evenodd". Without this, geographic features with holes (such as [South Africa](http://en.wikipedia.org/wiki/South_Africa) surrounding [Lesotho](http://en.wikipedia.org/wiki/Lesotho)) will not display correctly.

<a name="path_projection" href="#path_projection">#</a> path.<b>projection</b>([<i>projection</i>])

<a name="path_area" href="#path_area">#</a> path.<b>area</b>(<i>feature</i>)

<a name="path_centroid" href="#path_area">#</a> path.<b>centroid</b>(<i>feature</i>)

<a name="path_pointRadius" href="#path_pointRadius">#</a> path.<b>pointRadius</b>([<i>radius</i>])

<a name="bounds" href="#bounds">#</a> d3.geo.<b>bounds</b>(<i>feature</i>)
