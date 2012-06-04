> [Wiki](Home) ▸ [[API Reference]] ▸ [[Geo]] ▸ **Geo Projections**

## Mercator

The spherical Mercator projection is commonly used by tiled mapping libraries (such as [OpenLayers](http://openlayers.org/) and [Leaflet](http://leaflet.cloudmade.com/)). It is [conformal](http://en.wikipedia.org/wiki/Conformal_map); however, it introduces severe area distortion at world scale and thus is not recommended for choropleths.

<a name="mercator" href="#wiki-mercator">#</a> d3.geo.**mercator**()

Construct a new spherical Mercator projection with the default scale (500) and translate ([480, 250]). The default Mercator projection is appropriate for displaying the [entire world](http://bl.ocks.org/2869760) in a 960×500 area.

<a name="_mercator" href="#wiki-_mercator">#</a> **mercator**(*location*)

The forward projection: returns a two-element array [*x*, *y*] given the input [*longitude*, *latitude*].

<a name="mercator_invert" href="#wiki-mercator_invert">#</a> mercator.**invert**(*point*)

The inverse projection: returns a two-element array [*longitude*, *latitude*] given the input [*x*, *y*].

<a name="mercator_scale" href="#wiki-mercator_scale">#</a> mercator.**scale**([*scale*])

Get or set the projection’s scale factor. If *scale* is specified, sets the projection’s scale factor to the specified value and returns the projection. If *scale* is not specified, returns the current scale factor which defaults to 500. The scale factor corresponds linearly to the distance between projected points. Note that scale factors may not be consistent across projection types (e.g., Mercator and Albers).

<a name="mercator_translate" href="#wiki-mercator_translate">#</a> mercator.**translate**([*offset*])

Get or set the projection's translation offset. If *offset* is specified, sets the projection’s translation offset to the specified two-element array [*x*, *y*] and returns the projection. If *offset* is not specified, returns the current translation offset which defaults to [480, 250]. The translation offset determines the pixel coordinates of the origin ([0, 0] in longitude and latitude). The default value is designed to place [null island](http://www.nullisland.com/) at the center of a 960×500 area.

## Albers

The Albers equal-area projection is highly recommended for [choropleths](http://mbostock.github.com/d3/ex/choropleth.html) as it does not preserves the relative areas of geographic features. However, you must determine appropriate parallels and origin.

<a name="albers" href="#wiki-albers">#</a> d3.geo.<b>albers</b>()

Construct a new Albers equal-area conic projection with the default scale (1000), translate ([480, 250]), origin ([-98, 38]) and parallels ([29.5, 45.5]). The default Albers projection is appropriate for displaying the [United States](http://bl.ocks.org/2869871) in a 960×500 area. The parallels of 29.5º and 45.5º were chosen by the [USGS](http://www.usgs.gov/) in their 1970 [National Atlas](http://www.nationalatlas.gov/).

<a name="_albers" href="#wiki-_albers">#</a> **albers**(*location*)

The forward projection: returns a two-element array [*x*, *y*] given the input [*longitude*, *latitude*].

<a name="albers_invert" href="#wiki-albers_invert">#</a> albers.**invert**(*point*)

The inverse projection: returns a two-element array [*longitude*, *latitude*] given the input [*x*, *y*].

<a name="albers_origin" href="#wiki-albers_origin">#</a> albers.**origin**([*origin*])

Get or set the projection’s origin. If *origin* is specified, sets the projection’s origin to the specified two-element array [*longitude*, *latitude*] and returns the projection. If *origin* is not specified, returns the current origin, which defaults to [-98, 38] ([Hutchinson, Kansas](https://maps.google.com/maps?q=Hutchinson,+Kansas&z=5)). To minimize the distortion of parallel lines, the origin should be chosen to be near the center of the region of interest.

<a name="albers_parallels" href="#wiki-albers_parallels">#</a> albers.**parallels*([*parallels*])

Get or set the projection’s two standard parallels. If *parallels* is specified, sets the projection’s parallels to the specified two-element array of latitudes and returns the projection. If *parallels* is not specified, returns the current parallels, which default to [29.5, 45.5]. To minimize the distortion of parallel lines, the parallels should surround the origin and cover the region of interest.

<a name="albers_scale" href="#wiki-albers_scale">#</a> albers.**scale**([*scale*])

Get or set the projection’s scale factor. If *scale* is specified, sets the projection’s scale factor to the specified value and returns the projection. If *scale* is not specified, returns the current scale factor which defaults to 1000. The scale factor corresponds linearly to the distance between projected points. Note that scale factors may not be consistent across projection types (e.g., Mercator and Albers).

<a name="albers_translate" href="#wiki-albers_translate">#</a> albers.**translate**([*offset*])

Get or set the projection's translation offset. If *offset* is specified, sets the projection’s translation offset to the specified two-element array [*x*, *y*] and returns the projection. If *offset* is not specified, returns the current translation offset which defaults to [480, 250]. The translation offset determines the pixel coordinates of the [origin](#wiki-albers_origin). The default value is designed to place Hutchinson, Kansas at the center of a 960×500 area.

## Albers USA (Composite)

The Albers USA projection is a [composite projection](http://bl.ocks.org/2869946) of four Albers projections, designed to display the forty-eight lower United States alongside Alaska, Hawaii and Puerto Rico. Although intended for choropleths, it distorts the area of Puerto Rico (1.5x) and Alaska (0.6x); Hawaii is shown at the same scale as the lower forty-eight.

The projection composition is implemented as:

```js
function albersUsa(coordinates) {
  var lon = coordinates[0],
      lat = coordinates[1];
  return (lat > 50 ? alaska
      : lon < -140 ? hawaii
      : lat < 21 ? puertoRico
      : lower48)(coordinates);
}
```

The Albers USA projection does not currently support inversion.

<a name="albersUsa" href="#wiki-albersUsa">#</a> d3.geo.**albersUsa**()

Construct a new composite Albers projection for the United States.

<a name="_albersUsa" href="#wiki-_albersUsa">#</a> **albersUsa**(*location*)

The forward projection: returns a two-element array [*x*, *y*] given the input [*longitude*, *latitude*].

<a name="albersUsa_scale" href="#wiki-albersUsa_scale">#</a> albersUsa.**scale**([*scale*])

Get or set the projection’s scale factor. If *scale* is specified, sets the projection’s scale factor to the specified value and returns the projection. If *scale* is not specified, returns the current scale factor which defaults to 1000. The scale factor corresponds linearly to the distance between projected points. Note that scale factors may not be consistent across projection types (e.g., Mercator and Albers).

(As noted above, a scale factor of 1000 corresponds to a scale of 1500 for Puerto Rico and 600 for Alaska.)

<a name="albers_translate" href="#wiki-albers_translate">#</a> albers.**translate**([*offset*])

Get or set the projection's translation offset. If *offset* is specified, sets the projection’s translation offset to the specified two-element array [*x*, *y*] and returns the projection. If *offset* is not specified, returns the current translation offset which defaults to [480, 250]. The translation offset determines the pixel coordinates of the [origin](#wiki-albers_origin). The default value is designed to place Hutchinson, Kansas at the center of a 960×500 area.

## Azimuthal

D3’s azimuthal projection implementation encompasses [orthographic](http://en.wikipedia.org/wiki/Orthographic_projection_(cartography\)), [stereographic](http://en.wikipedia.org/wiki/Stereographic_projection), [gnomonic](http://en.wikipedia.org/wiki/Gnomonic_projection), equidistant and equal-area projections.

<a name="azimuthal" href="#wiki-azimuthal">#</a> d3.geo.<b>azimuthal</b>()

Construct a new Azimuthal projection with the default mode (orthographic), origin (⟨0, 0⟩), scale (200) and translate ([480, 250]). The [default projection](http://bl.ocks.org/2870030) shows the hemisphere centered around null island in a 960×500 area. Azimuthal projections should typically be used in conjunction with [d3.geo.circle](Geo-Paths#wiki-circle)’s [clip](Geo-Paths#wiki-circle_clip) method to avoid showing the back-facing hemisphere.

<a name="_azimuthal" href="#wiki-_azimuthal">#</a> **azimuthal**(*location*)

The forward projection: returns a two-element array [*x*, *y*] given the input [*longitude*, *latitude*].

<a name="azimuthal_mode" href="#wiki-azimuthal_mode">#</a> azimuthal.**mode**([*mode*])

Get or set the projection’s mode. If *mode* is specified, sets the projection mode to the specified string and returns the projection. If *mode* is not specified, returns the current mode which defaults to orthographic. The allowed modes are:

* orthographic
* stereographic
* gnomonic
* equidistant
* equalarea

See [this interactive example](http://mbostock.github.com/d3/talk/20111018/azimuthal.html) for a demonstration of the different projection modes.

<a name="azimuthal_origin" href="#wiki-azimuthal_origin">#</a> azimuthal.**origin**([*origin*])

Get or set the projection’s origin. If *origin* is specified, sets the projection’s origin to the specified two-element array [*longitude*, *latitude*] and returns the projection. If *origin* is not specified, returns the current origin, which defaults to [0, 0] ([null island](http://nullisland.com)). To minimize distortion, the origin should be chosen to be near the center of the region of interest.

<a name="azimuthal_scale" href="#wiki-azimuthal_scale">#</a> azimuthal.**scale**([*scale*])

Get or set the projection’s scale factor. If *scale* is specified, sets the projection’s scale factor to the specified value and returns the projection. If *scale* is not specified, returns the current scale factor which defaults to 200. The scale factor corresponds linearly to the distance between projected points. Note that scale factors may not be consistent across projection types (e.g., Mercator and Albers).

<a name="azimuthal_translate" href="#wiki-azimuthal_translate">#</a> azimuthal.**translate**([*offset*])

Get or set the projection's translation offset. If *offset* is specified, sets the projection’s translation offset to the specified two-element array [*x*, *y*] and returns the projection. If *offset* is not specified, returns the current translation offset which defaults to [480, 250]. The translation offset determines the pixel coordinates of the [origin](#wiki-azimuthal_origin). The default value is designed to place Null Island at the center of a 960×500 area.
