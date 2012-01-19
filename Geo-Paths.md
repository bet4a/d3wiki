> [[API Reference]] ▸ [[Geo]]

For cartographic visualizations, D3 supports a handful of utilities for displaying and manipulating **geographic data**. These utilities are based on the [GeoJSON format](http://geojson.org/geojson-spec.html)—a standard way of representing geographic features in JavaScript. For example, [GDAL](http://www.gdal.org/) includes the ogr2ogr tool which can convert binary shapefiles into GeoJSON; the shapefile is another common representation for geographic data, frequently used by the [U.S. Census Bureau](http://www.census.gov/).

![choropleth](choropleth.png)

Some other tools you may be interested in:

* [Shapely](http://trac.gispython.org/lab/wiki/Shapely) - manipulation of planar geometry objects.
* [MapShaper](http://mapshaper.org/) and [Bloch](https://github.com/migurski/Bloch/) - shapefile simplification.
* [ColorBrewer](http://colorbrewer2.org) - color scales for maps.
* [PostGIS](http://postgis.refractions.net/) - a geospatial database.

The primary mechanism for displaying geographic data is [d3.geo.path](Geo-Paths#wiki-path). In many ways, this class is similar to [d3.svg.line](SVG-Shapes#wiki-line) and the other SVG shape generators: given a geometry or feature object, it generates the path data string suitable for the "d" attribute of an SVG path element.

<a name="path" href="Geo-Paths#wiki-path">#</a> d3.geo.<b>path</b>()

Creates a new geographic path generator with the default settings: the [albersUsa](Geo-Projections#wiki-albersUsa) projection and a point radius of 4.5 pixels.

<a name="_path" href="Geo-Paths#wiki-_path">#</a> <b>path</b>(<i>feature</i>[, <i>index</i>])

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
  .enter().append("path")
    .attr("d", d3.geo.path());
```

An optional *index* may be specified, which is passed along to the [pointRadius](Geo-Paths#wiki-pointRadius) accessor.

<a name="path_projection" href="Geo-Paths#wiki-path_projection">#</a> path.<b>projection</b>([<i>projection</i>])

If *projection* is specified, sets the projection used by the path generator to the specified projection function. If *projection* is not specified, returns the current projection, which defaults to [albersUsa](Geo-Projections#wiki-albersUsa). Typically, the projection is one of D3's built-in [projections](Geo-Projections); however, any function can be used. The function takes a two-element array of numbers representing the coordinates of a single position, [*longitude*, *latitude*], and returns a similar two-element array of numbers representing the projected pixel position [*x*, *y*]. For example, a rudimentary spherical Mercator projection:

```javascript
function mercator(coordinates) {
  return [
    coordinates[0] / 360,
    (-180 / Math.PI * Math.log(Math.tan(Math.PI / 4 + coordinates[1] * Math.PI / 360))) / 360
  ];
}
```

If you want to use a projection that D3 does not already support, you might be able to adapt [Proj4js](http://trac.osgeo.org/proj4js/).

<a name="path_area" href="Geo-Paths#wiki-path_area">#</a> path.<b>area</b>(<i>feature</i>)

Computes the projected area (in square pixels) for the specified *feature*. Point, MultiPoint, LineString and MultiLineString features are ignored, returning zero. For Polygon and MultiPolygon features, this method first computes the area of the exterior ring, and then subtracts the area of any interior holes.

Note: this method depends on [d3.geom.polygon](Polygon-Geom), so you must load d3.geom.js, or build a custom d3.js that includes d3.geom.polygon.

<a name="path_centroid" href="Geo-Paths#wiki-path_area">#</a> path.<b>centroid</b>(<i>feature</i>)

Computes the projected centroid (in pixels) for the specified *feature*. This method is currently only supported for Polygon and MultiPolygon features. This is handy for, say, labeling state or county boundaries, or displaying a symbol map. The [noncontiguous cartogram](http://mbostock.github.com/d3/ex/cartogram.html) example scales each state around its centroid.

Note: this method depends on [d3.geom.polygon](Polygon-Geom), so you must load d3.geom.js, or build a custom d3.js that includes d3.geom.polygon.

<a name="path_pointRadius" href="Geo-Paths#wiki-path_pointRadius">#</a> path.<b>pointRadius</b>([<i>radius</i>])

If *radius* is specified, sets the radius used to display Point and MultiPoint features to the specified number. If *radius* is not specified, returns the current radius. While the radius is commonly specified as a number constant, it may also be specified as a function which is computed per feature, being passed the *feature* and *index* arguments from the [path](Geo-Paths#wiki-_path) function. For example, if your GeoJSON data has additional properties, you might access those properties inside the radius function to vary the point size; alternatively, you could [d3.svg.symbol](SVG-Shapes#wiki-symbol) and a [projection](Geo-Projections) for more control over the display.

<a name="bounds" href="Geo-Paths#wiki-bounds">#</a> d3.geo.<b>bounds</b>(<i>feature</i>)

Given a GeoJSON *feature*, returns the corresponding bounding box. The bounding box is represented by a two-dimensional array: [​[*left*, *bottom*], [*right*, *top*]​], where *left* is the minimum longitude, *bottom* is the minimum latitude, *right* is maximum longitude, and *top* is the maximum latitude.

<a name="greatArc" href="Geo-Paths#wiki-greatArc">#</a> d3.geo.<b>greatArc</b>()

Constructs a new interpolator to approximate the shortest path between two geographic points, using a segment of a <a href="http://en.wikipedia.org/wiki/Great_circle">great circle</a>.

<a name="_greatArc" href="Geo-Paths#wiki-_greatArc">#</a> <b>greatArc</b>([<i>…</i>])

Returns a GeoJSON LineString approximating a great circle segment.  If source and target accessors are in use, they will retrieve the source and target points from the given arguments.  By default, they expect `{source: …, target: …}`.

<a name="_greatArc" href="Geo-Paths#wiki-greatArc_distance">#</a> greatArc.<b>distance</b>([<i>…</i>])

Returns the great circle distance along this great circle segment.  If source and target accessors are in use, they will retrieve the source and target points from the given arguments.  By default, they expect `{source: …, target: …}`.

<a name="greatArc_source" href="Geo-Paths#wiki-greatArc_source">#</a> greatArc.<b>source</b>([<i>source</i>])

If *source* is specified, sets the *source*-accessor to the specified function or constant point, [*longitude*, *latitude*]. If *source* is not specified, returns the current *source*-accessor.  This accessor is invoked every time the interpolator is called.  The default is `function(d) { return d.source; }`.

<a name="greatArc_target" href="Geo-Paths#wiki-greatArc_target">#</a> greatArc.<b>target</b>([<i>target</i>])

If *target* is specified, sets the *target*-accessor to the specified function or constant point, [*longitude*, *latitude*]. If *source* is not specified, returns the current *target*-accessor.  This accessor is invoked every time the interpolator is called.  The default is `function(d) { return d.target; }`.

<a name="greatArc_precision" href="Geo-Paths#wiki-greatArc_precision">#</a> greatArc.<b>precision</b>([<i>precision</i>])

If *precision* is specified, sets the maximum segment length of the interpolated path in degrees. If *precision* is not specified, returns the current precision, which defaults to 6°.

<a name="circle" href="Geo-Paths#wiki-circle">#</a> d3.geo.<b>circle</b>

Represents a geographic circle with arbitrary radius and origin, which can be used to clip geographic features.  This is particularly useful for azimuthal projections.

<a name="circle_origin" href="Geo-Paths#wiki-circle_origin">#</a> circle.<b>origin</b>([<i>origin</i>])

If *origin* is specified, sets the circle origin.  A two-element coordinate array should be specified, or an accessor function.  If *origin* is not specified, returns the current origin, which defaults to `[0, 0]`.

<a name="circle_angle" href="Geo-Paths#wiki-circle_angle">#</a> circle.<b>angle</b>([<i>angle</i>])

If *angle* is specified, sets the angular radius of the circle in degrees.  If *angle* is not specified, returns the current radius, which defaults to 89.9°.

<a name="circle_precision" href="Geo-Paths#wiki-circle_precision">#</a> circle.<b>precision</b>([<i>precision</i>])

If *precision* is specified, sets the precision of the interpolated circle segments in degrees.  These interpolated segments are inserted when a feature is clipped by the circle.

If *precision* is not specified, returns the current precision, which defaults to 6°.

<a name="circle_clip" href="Geo-Paths#wiki-circle_clip">#</a> circle.<b>clip</b>(<i>feature</i>[, <i>index</i>])

Clips a given GeoJSON *feature* or geometry object against this circle.