> [Wiki](Home) ▸ [[API Reference]] ▸ [[Geo]] ▸ **Geo Streams**

For fast transformations of geometry without temporary copies of geometry objects, D3 uses **geometry streams**. The main [d3.geo.stream](#wiki-d3_geo_stream) method converts a GeoJSON input object to a stream: a series of method calls on a *stream listener*. In addition, D3 provides several stream transformations that wrap listeners and transform the geometry. For example, the [projection.stream](Geo-Projections#stream) interface transforms spherical coordinates to Cartesian coordinates, and [d3.geo.path](Geo-Paths) serializes geometry to either SVG or Canvas. Internally, clipping and rotating are also implemented as stream transformations.

<a name="d3_geo_stream" href="#wiki-d3_geo_stream">#</a> d3.geo.<b>stream</b>(<i>object</i>, <i>listener</i>)

Streams the specified [GeoJSON](http://geojson.org) *object* to the specified stream *listener*. (Despite the name “stream”, these method calls are currently synchronous.) While both features and geometry objects are supported as input, the stream interface only describes the geometry, and thus additional feature properties are not visible to listeners.

## Stream Listeners

Stream listeners must implement several methods to traverse geometry. Listeners are inherently stateful; the meaning of a [point](#wiki-point) depends on whether the point is inside of a [line](#wiki-lineStart), and likewise a line is distinguished from a ring by a [polygon](#wiki-polygonStart).

<a name="point" href="#wiki-point">#</a> listener.<b>point</b>(<i>x</i>, <i>y</i>[, <i>z</i>])

…

<a name="lineStart" href="#wiki-lineStart">#</a> listener.<b>lineStart</b>()

…

<a name="lineEnd" href="#wiki-lineEnd">#</a> listener.<b>lineEnd</b>()

…

<a name="polygonStart" href="#wiki-polygonStart">#</a> listener.<b>polygonStart</b>()

…

<a name="polygonEnd" href="#wiki-polygonEnd">#</a> listener.<b>polygonEnd</b>()

…

<a name="sphere" href="#wiki-sphere">#</a> listener.<b>sphere</b>()

…
