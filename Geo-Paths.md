> [Wiki](Home) ▸ [[API Reference]] ▸ [[Geo]] ▸ **Geo Paths**

For cartographic visualizations, D3 supports a handful of components for displaying and manipulating **geographic data**. These components use the [GeoJSON format](http://geojson.org/geojson-spec.html)—a standard way of representing geographic features in JavaScript. (See also the [TopoJSON format](/mbostock/topojson), an extension of GeoJSON that is significantly more compact.) To convert shapefiles to GeoJSON, use ogr2ogr, part of the [GDAL package](http://www.gdal.org/).

<a href="http://bl.ocks.org/4060606"><img src="https://raw.github.com/gist/4060606/thumbnail.png" height="120"></a>

Some other tools you may be interested in:

* [TopoJSON](/mbostock/topojson) - shapefile simplification, topology construction and GeoJSON compression.
* [Shapely](http://trac.gispython.org/lab/wiki/Shapely) - manipulation of planar geometry objects.
* [ColorBrewer](http://colorbrewer2.org) - color scales for maps.
* [PostGIS](http://postgis.refractions.net/) - a geospatial database.

The primary mechanism for displaying geographic data is [d3.geo.path](#wiki-path). This class is similar to [d3.svg.line](SVG-Shapes#wiki-line) and the other SVG shape generators: given a geometry or feature object, it generates the path data string suitable for the "d" attribute of an SVG path element. The d3.geo.path class can [render directly to Canvas](http://bl.ocks.org/3783604), which may offer better performance when animating the projection.

<a name="path" href="#wiki-path">#</a> d3.geo.<b>path</b>()

Creates a new geographic path generator with the default settings: the [albersUsa](Geo-Projections#wiki-albersUsa) projection and a point radius of 4.5 pixels.

<a name="_path" href="#wiki-_path">#</a> <b>path</b>(<i>feature</i>[, <i>index</i>])

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

An optional *index* may be specified, which is passed along to the [pointRadius](Geo-Paths#wiki-pointRadius) accessor. (The *index* is passed automatically when the path generator is invoked by [selection.attr](Selections#wiki-attr).)

To display multiple features, you can place them in a single feature collection and a single path element:

```javascript
svg.append("path")
    .datum({type: "FeatureCollection", features: features})
    .attr("d", d3.geo.path());
```

Alternatively, you can create multiple distinct path elements:

```javascript
svg.selectAll("path")
    .data(features)
  .enter().append("path")
    .attr("d", d3.geo.path());
```

Using distinct path elements is typically slower than a single path element for a collection. However, distinct path elements are preferred if you want interact with features separately (e.g., using CSS :hover or click events).

<a name="projection" href="#wiki-projection">#</a> path.<b>projection</b>([<i>projection</i>])

If *projection* is specified, sets the projection used by the path generator to the specified projection function. If *projection* is not specified, returns the current projection, which defaults to [albersUsa](Geo-Projections#wiki-albersUsa). The projection is typically one of D3's built-in [geographic projections](Geo-Projections); however, any function can be used. A projection function takes a two-element array of numbers representing the coordinates of a location, [<i>longitude</i>, <i>latitude</i>], and returns a similar two-element array of numbers representing the projected pixel position [<i>x</i>, <i>y</i>]. For example, a rudimentary spherical Mercator projection:

```javascript
function mercator(coordinates) {
  return [
    coordinates[0] / 360,
    (-180 / Math.PI * Math.log(Math.tan(Math.PI / 4 + coordinates[1] * Math.PI / 360))) / 360
  ];
}
```

Internally, this point projection function is wrapped with a fallback [stream transformation](Geo-Streams) that performs [adaptive resampling](http://bl.ocks.org/3795544). However, the fallback stream does not perform any clipping or cutting. For more control over the stream transformation, the *projection* may be specified as an object that implements the *stream* method. The stream method takes a stream listener as input, and returns a wrapped stream listener that projects the input geometry; in other words, it implements [projection.stream](Geo-Projection#wiki-stream).

If *projection* is null, the path uses the identity transformation, where the input geometry is not projected and is instead rendered directly in raw coordinates. This can be useful for fast rendering of already-projected geometry, or for fast rendering of the equirectangular projection.

<a name="context" href="#wiki-context">#</a> path.<b>context</b>([<i>context</i>])

…

<a name="area" href="#wiki-area">#</a> path.<b>area</b>(<i>feature</i>)

Computes the projected area (in square pixels) for the specified *feature*. Point, MultiPoint, LineString and MultiLineString features have zero area. For Polygon and MultiPolygon features, this method first computes the area of the exterior ring, and then subtracts the area of any interior holes. This method observes any clipping and resampling performed by the projection stream.

<a name="centroid" href="#wiki-centroid">#</a> path.<b>centroid</b>(<i>feature</i>)

Computes the projected centroid (in pixels) for the specified *feature*. This is handy for, say, labeling state or county boundaries, or displaying a symbol map. The [noncontiguous cartogram](http://mbostock.github.com/d3/ex/cartogram.html) example scales each state around its centroid. This method observes any clipping and resampling performed by the projection stream.

<a name="bounds" href="#wiki-bounds">#</a> path.<b>bounds</b>(<i>feature</i>)

Computes the projected bounding box (in pixels) for the specified *feature*. This is handy for, say, zooming in to a particular feature. This method observes any clipping and resampling performed by the projection stream.

<a name="pointRadius" href="#wiki-pointRadius">#</a> path.<b>pointRadius</b>([<i>radius</i>])

If *radius* is specified, sets the radius used to display Point and MultiPoint features to the specified number. If *radius* is not specified, returns the current radius. While the radius is commonly specified as a number constant, it may also be specified as a function which is computed per feature, being passed the *feature* and *index* arguments from the [path](Geo-Paths#wiki-_path) function. For example, if your GeoJSON data has additional properties, you might access those properties inside the radius function to vary the point size; alternatively, you could [d3.svg.symbol](SVG-Shapes#wiki-symbol) and a [projection](Geo-Projections) for more control over the display.

<a name="greatArc" href="#wiki-greatArc">#</a> d3.geo.<b>greatArc</b>()

Constructs a feature generator for creating the great arc between two geographic points, using a segment of a <a href="http://en.wikipedia.org/wiki/Great_circle">great circle</a>. The great arc represents the shortest path between the two points on the surface of the sphere.

<a name="_greatArc" href="#wiki-_greatArc">#</a> <b>greatArc</b>(<i>arguments…</i>)

Returns a GeoJSON LineString approximating a great circle segment. The source and target accessors specify how to determine the source and target points for the given *arguments*; the default accessors expect a single argument with source and target properties: `{source: …, target: …}`.

<a name="greatArc_distance" href="#wiki-greatArc_distance">#</a> greatArc.<b>distance</b>(<i>arguments…</i>)

Returns the length of the great arc between the two points represented by *arguments* in radians. To convert the angular distance to a linear one, simply multiply by the radius of the sphere, which is around *6,371km* on average for Earth. The source and target accessors specify how to determine the source and target points for the given *arguments*; the default accessors expect a single argument with source and target properties: `{source: …, target: …}`.

<a name="greatArc_source" href="#wiki-greatArc_source">#</a> greatArc.<b>source</b>([<i>source</i>])

If *source* is specified, sets the *source*-accessor to the specified function or constant point, [<i>longitude</i>, <i>latitude</i>]. If *source* is not specified, returns the current *source*-accessor.  This accessor is invoked every time the interpolator is called.  The default is `function(d) { return d.source; }`.

<a name="greatArc_target" href="#wiki-greatArc_target">#</a> greatArc.<b>target</b>([<i>target</i>])

If *target* is specified, sets the *target*-accessor to the specified function or constant point, [<i>longitude</i>, <i>latitude</i>]. If *source* is not specified, returns the current *target*-accessor.  This accessor is invoked every time the interpolator is called.  The default is `function(d) { return d.target; }`.

<a name="greatArc_precision" href="#wiki-greatArc_precision">#</a> greatArc.<b>precision</b>([<i>precision</i>])

If *precision* is specified, sets the maximum segment length of the interpolated path in degrees. If *precision* is not specified, returns the current precision, which defaults to 6°.

<a name="circle" href="#wiki-circle">#</a> d3.geo.<b>circle</b>

Constructs a feature generator for creating circles centered at a given geographic location with a given radius in degrees.

<a name="_circle" href="#wiki-_circle">#</a> <b>circle</b>(<i>arguments…</i>)

Returns a GeoJSON Polygon approximating a circle. The origin accessor specifies how to determine the origin for the given *arguments*; the default accessor uses the constant ⟨0°,0°⟩.

<a name="circle_origin" href="#wiki-circle_origin">#</a> circle.<b>origin</b>([<i>origin</i>])

If *origin* is specified, sets the circle origin.  A two-element coordinate array should be specified, or an accessor function.  If *origin* is not specified, returns the current origin, which defaults to ⟨0°,0°⟩.

<a name="circle_angle" href="#wiki-circle_angle">#</a> circle.<b>angle</b>([<i>angle</i>])

If *angle* is specified, sets the angular radius of the circle in degrees.  If *angle* is not specified, returns the current radius, which defaults to 90°.

<a name="circle_precision" href="#wiki-circle_precision">#</a> circle.<b>precision</b>([<i>precision</i>])

If *precision* is specified, sets the precision of the interpolated circle segments in degrees.  These interpolated segments are inserted when a feature is clipped by the circle. If *precision* is not specified, returns the current precision, which defaults to 6°.

## Math

<a name="d3_geo_area" href="#wiki-d3_geo_area">#</a> d3.geo.<b>area</b>(<i>feature</i>)

…

<a name="d3_geo_centroid" href="#wiki-d3_geo_centroid">#</a> d3.geo.<b>centroid</b>(<i>feature</i>)

…

<a name="d3_geo_bounds" href="#wiki-d3_geo_bounds">#</a> d3.geo.<b>bounds</b>(<i>feature</i>)

Given a GeoJSON *feature*, returns the corresponding bounding box. The bounding box is represented by a two-dimensional array: [​[*left*, *bottom*], [*right*, *top*]​], where *left* is the minimum longitude, *bottom* is the minimum latitude, *right* is maximum longitude, and *top* is the maximum latitude.

<a name="d3_geo_interpolate" href="#wiki-d3_geo_interpolate">#</a> d3.geo.<b>interpolate</b>(<i>a</i>, <i>b</i>)

…