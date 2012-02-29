> [[API Reference]] ▸ [[SVG]]

## Brush

<a name="brush" href="#wiki-brush">#</a> d3.svg.**brush**()

…

<a name="_brush" href="#wiki-_brush">#</a> **brush**(*selection*)

The *selection* can also be a [transition](Transitions).

<a name="brush_x" href="#wiki-brush_x">#</a> brush.**x**([*scale*])

Gets or sets the *x*-scale associated with the brush. If *scale* is specified, sets the *x*-scale to the specified scale; if *scale* is not specified, returns the current *x*-scale, which defaults to null. The scale is typically defined as a [quantitative scale](Quantitative-Scales), which cases the [extent](#wiki-extent) to be represented in data space (from the scale's [domain](Quantitative-Scales#wiki-linear_domain)); however, it may also be defined as an [ordinal scale](Ordinal-Scale), in which case the extent is represented in pixel scale (from the scale's [range extent](Ordinal-Scales#wiki-ordinal_rangeExtent).

<a name="brush_y" href="#wiki-brush_y">#</a> brush.**y**([*scale*])

…

<a name="brush_extent" href="#wiki-brush_extent">#</a> brush.**extent**([*values*])

…

<a name="brush_clear" href="#wiki-brush_clear">#</a> brush.**clear**()

…

<a name="brush_empty" href="#wiki-brush_empty">#</a> brush.**empty**()

…

<a name="brush_on" href="#wiki-brush_on">#</a> brush.**on**(*type*[, *listener*])

…