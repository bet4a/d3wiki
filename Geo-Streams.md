> [Wiki](Home) ▸ [[API Reference]] ▸ [[Geo]] ▸ **Geo Streams**

For fast transformations of geometry without creating lots of temporary copies of geometry objects, D3 uses **geometry streams**. The main [d3.geo.stream](#wiki-d3_geo_stream) method converts a GeoJSON input object to a stream as a series of method calls on a *stream listener*. (Despite the name “stream”, these method calls are currently synchronous.) In addition, D3 provides several implementations of stream transformations that wrap listeners and transform the geometry. For example, the [projection.stream](Geo-Projections#stream) interface transforms spherical coordinates to Cartesian coordinates, and [d3.geo.path](Geo-Paths) serializes geometry to either SVG or Canvas.

<a name="d3_geo_stream" href="#wiki-d3_geo_stream">#</a> d3.geo.<b>stream</b>(object, listener)

…

<a name="point" href="#wiki-point">#</a> listener.<b>point</b>(<i>x</i>, <i>y</i>)

…

<a name="lineStart" href="#wiki-lineStart">#</a> listener.<b>lineStart</b>()

…

<a name="lineEnd" href="#wiki-lineEnd">#</a> listener.<b>lineEnd</b>()

…

<a name="polygonStart" href="#wiki-polygonStart">#</a> listener.<b>polygonStart</b>()

…

<a name="polygonEnd" href="#wiki-polygonEnd">#</a> listener.<b>polygonEnd</b>()

…

