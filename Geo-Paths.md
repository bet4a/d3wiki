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

For polygons, you should specify the style property "fill-rule" as "evenodd" on path elements. This ensures that geographic features with holes (such as [South Africa](http://en.wikipedia.org/wiki/South_Africa) surrounding [Lesotho](http://en.wikipedia.org/wiki/Lesotho)) are displayed correctly. To display multiple features, you can either place them in a single feature collection and a single path element, or create multiple distinct path elements:

```javascript
vis.selectAll("path")
    .data(features)
  .enter().append("svg:path")
    .attr("d", d3.geo.path());
```

An optional *index* may be specified, which is passed along to the [pointRadius](#pointRadius) accessor.

<a name="path_projection" href="#path_projection">#</a> path.<b>projection</b>([<i>projection</i>])

If *projection* is specified, sets the projection used by the path generator to the specified projection function. If *projection* is not specified, returns the current projection, which defaults to [albersUsa](Geo-Projections#albersUsa). Typically, the projection is one of D3's built-in [projections](Geo-Projections); however, any function can be used. The function takes a two-element array of numbers representing the coordinates of a single position, [*longitude*, *latitude*], and returns a similar two-element array of numbers representing the projected pixel position [*x*, *y*]. For example, a rudimentary spherical Mercator projection:

```javascript
function mercator(coordinates) {
  return [
    coordinates[0] / 360,
    (-180 / Math.PI * Math.log(Math.tan(Math.PI / 4 + coordinates[1] * Math.PI / 360))) / 360
  ];
}
```

If you want to use a projection that D3 does not already support, you might be able to adapt [Proj4js](http://trac.osgeo.org/proj4js/).

<a name="path_area" href="#path_area">#</a> path.<b>area</b>(<i>feature</i>)

Computes the projected area (in square pixels) for the specified *feature*. Point, MultiPoint, LineString and MultiLineString features are ignored, returning zero. For Polygon and MultiPolygon features, this method first computes the area of the exterior ring, and then subtracts the area of any interior holes.

Note: this method depends on [d3.geom.polygon](Polygon-Geom), so you must load d3.geom.js or build a custom d3.js that includes d3.geom.polygon.

<a name="path_centroid" href="#path_area">#</a> path.<b>centroid</b>(<i>feature</i>)

Computes the projected centroid (in pixels) for the specified *feature*. This method is currently only supported for Polygon and MultiPolygon features. This is handy for, say, labeling state or county boundaries, or displaying a symbol map. The [noncontiguous cartogram](http://mbostock.github.com/d3/ex/cartogram.html) example scales each state around its centroid.

Note: this method depends on [d3.geom.polygon](Polygon-Geom), so you must load d3.geom.js or build a custom d3.js that includes d3.geom.polygon.

<a name="path_pointRadius" href="#path_pointRadius">#</a> path.<b>pointRadius</b>([<i>radius</i>])

If *radius* is specified, sets the radius used to display Point and MultiPoint features to the specified number. If *radius* is not specified, returns the current radius. While the radius is commonly specified as a number constant, it may also be specified as a function which is computed per feature, being passed the *feature* and *index* arguments from the [path](#_path) function. For example, if your GeoJSON data has additional properties, you might access those properties inside the radius function to vary the point size; alternatively, you could [d3.svg.symbol](SVG-Shapes#symbol) and a [projection](Geo-Projections) for more control over the display.

<a name="bounds" href="#bounds">#</a> d3.geo.<b>bounds</b>(<i>feature</i>)

Given a GeoJSON *feature*, returns the corresponding bounding box. The bounding box is represented by a two-dimensional array: [​[*left*, *bottom*], [*right*, *top*]​], where *left* is the minimum longitude, *bottom* is the minimum latitude, *right* is maximum longitude, and *top* is the maximum latitude.
