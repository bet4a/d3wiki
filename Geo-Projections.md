> [Wiki](Home) ▸ [[API Reference]] ▸ [[Geo]] ▸ **Geo Projections**

## Mercator

The spherical Mercator projection is commonly used by tiled mapping libraries (such as [OpenLayers](http://openlayers.org/) and [Leaflet](http://leaflet.cloudmade.com/)). It is [conformal](http://en.wikipedia.org/wiki/Conformal_map); however, it introduces severe area distortion at world scale and is thus not recommended for choropleths.

<a name="mercator" href="#wiki-mercator">#</a> d3.geo.**mercator**()

Construct a new spherical Mercator projection with the default scale (500) and translate ([480, 250]). The default Mercator projection is appropriate for displaying the [entire world](http://bl.ocks.org/2869760) in a 960×500 area.

<a name="_mercator" href="#wiki-_mercator">#</a> **mercator**(*location*)

The forward projection: returns a two-element array [*x*, *y*] given the input [*longitude*, *latitude*].

<a name="mercator_invert" href="#wiki-mercator_invert">#</a> mercator.**invert**(*point*)

The inverse projection: returns a two-element array [*longitude*, *latitude*] given the input [*x*, *y*].

<a name="mercator_scale" href="#wiki-mercator_scale">#</a> mercator.**scale**([*scale*])

Get or set the projection’s scale factor. If *scale* is specified, sets the projection’s scale factor to the specified value and returns the projection. If *scale* is not specified, returns the current scale factor which defaults to 500. The scale factor corresponds linearly to the distance between projected points.

<a name="mercator_translate" href="#wiki-mercator_translate">#</a> mercator.**translate**([*offset*])

Get or set the projection's translation offset. If *offset* is specified, sets the projection’s translation offset to the specified two-element array [*x*, *y*] and returns the projection. If *offset* is not specified, returns the current translation offset which defaults to [480, 250]. The translation offset determines the pixel coordinates of the origin ([0, 0] in longitude and latitude). The default value is designed to place [null island](http://www.nullisland.com/) at the center of a 960×500 area.

## Albers

The Albers equal-area projection is highly recommended for choropleths as it does not preserves the relative areas of geographic features. However, you must determine appropriate parallels.

<a name="albers" href="#wiki-albers">#</a> d3.geo.<b>albers</b>()

Construct a new Albers equal-area conic projection.

<a name="_albers" href="Geo-Projections#wiki-_albers">#</a> <b>albers</b>(<i>position</i>)

Project the specified position.

<a name="albers_origin" href="Geo-Projections#wiki-albers_origin">#</a> albers.<b>origin</b>([<i>origin</i>])

Get or set the projection's origin.

<a name="albers_parallels" href="Geo-Projections#wiki-albers_parallels">#</a> albers.<b>parallels</b>([<i>parallels</i>])

Get or set the projection's two standard parallels.

<a name="albers_scale" href="Geo-Projections#wiki-albers_scale">#</a> albers.<b>scale</b>([<i>scale</i>])

Get or set the projection's scale factor.

<a name="albers_translate" href="Geo-Projections#wiki-albers_translate">#</a> albers.<b>translate</b>([<i>offset</i>])

Get or set the projection's translate offset.

<a name="albersUsa" href="Geo-Projections#wiki-albersUsa">#</a> d3.geo.<b>albersUsa</b>()

Construct a new composite Albers projection for the United States.

<a name="_albersUsa" href="Geo-Projections#wiki-_albersUsa">#</a> <b>albersUsa</b>(<i>position</i>)

Project the specified position.

<a name="albersUsa_scale" href="Geo-Projections#wiki-albersUsa_scale">#</a> albersUsa.<b>scale</b>([<i>scale</i>])

Get or set the projection's scale factor.

<a name="albersUsa_translate" href="Geo-Projections#wiki-albersUsa_translate">#</a> albersUsa.<b>translate</b>([<i>offset</i>])

Get or set the projection's translate offset.

## Azimuthal

<a name="azimuthal" href="Geo-Projections#wiki-azimuthal">#</a> d3.geo.<b>azimuthal</b>()

Construct a new Azimuthal (orthographic or stereographic) projection.

<a name="_azimuthal" href="Geo-Projections#wiki-_azimuthal">#</a> <b>azimuthal</b>(<i>position</i>)

Project the specified position.

<a name="azimuthal_mode" href="Geo-Projections#wiki-azimuthal_mode">#</a> azimuthal.<b>mode</b>([<i>mode</i>])

Get or set the projection's mode (orthographic or stereographic).

<a name="azimuthal_origin" href="Geo-Projections#wiki-azimuthal_origin">#</a> azimuthal.<b>origin</b>([<i>origin</i>])

Get or set the projection's origin.

<a name="azimuthal_scale" href="Geo-Projections#wiki-azimuthal_scale">#</a> azimuthal.<b>scale</b>([<i>scale</i>])

Get or set the projection's scale factor.

<a name="azimuthal_translate" href="Geo-Projections#wiki-azimuthal_translate">#</a> azimuthal.<b>translate</b>([<i>offset</i>])

Get or set the projection's translate offset.