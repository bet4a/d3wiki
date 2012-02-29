> [[API Reference]] ▸ [[SVG]]

## Brush

<a name="brush" href="#wiki-brush">#</a> d3.svg.**brush**()

…

<a name="_brush" href="#wiki-_brush">#</a> **brush**(*selection*)

The *selection* can also be a [transition](Transitions).

<a name="brush_x" href="#wiki-brush_x">#</a> brush.**x**([*scale*])

Gets or sets the *x*-scale associated with the brush. If *scale* is specified, sets the *x*-scale to the specified scale and returns the brush; if *scale* is not specified, returns the current *x*-scale, which defaults to null. The scale is typically defined as a [quantitative scale](Quantitative-Scales), in which case the [extent](#wiki-extent) is in data space from the scale's [domain](Quantitative-Scales#wiki-linear_domain); however, it may instead be defined as an [ordinal scale](Ordinal-Scale), where the extent is in pixel space from the scale's [range extent](Ordinal-Scales#wiki-ordinal_rangeExtent).

<a name="brush_y" href="#wiki-brush_y">#</a> brush.**y**([*scale*])

Gets or sets the *y*-scale associated with the brush. If *scale* is specified, sets the *y*-scale to the specified scale and returns the brush; if *scale* is not specified, returns the current *y*-scale, which defaults to null. The scale is typically defined as a [quantitative scale](Quantitative-Scales), in which case the [extent](#wiki-extent) is in data space from the scale's [domain](Quantitative-Scales#wiki-linear_domain); however, it may instead be defined as an [ordinal scale](Ordinal-Scale), where the extent is in pixel space from the scale's [range extent](Ordinal-Scales#wiki-ordinal_rangeExtent).

<a name="brush_extent" href="#wiki-brush_extent">#</a> brush.**extent**([*values*])

Gets or sets the current brush extent. If *values* is specified, sets the extent to the specified values and returns the brush; if *values* is not specified, returns the current extent. The definition of the extent depends on the associated scales. If both an *x*- and *y*-scale are available, then the extent is the two-dimensional array [[*x0*, *y0*], [*x1*, *y1*]], where *x0* and *y0* are the lower bounds of the extent, and *x1* and *y1* are the upper bounds of the extent. If only the *x*-scale is available, then the extent is defined as the one-dimensional array [*x0*, *x1*]; likewise, if only the *y*-scale is available, then the extent is [*y0*, *y1*]. In neither scale is available, then the extent is null.

When the extent is set to *values*, the resulting extent is preserved exactly. However, as soon as the brush is moved by the user (on mousemove following a mousedown), then the extent must be recomputed by calling [scale.invert](Quantitative-Scales#wiki-linear_invert). Note that the values may be slightly imprecise due to the limited precision of pixels.

Note that this does not automatically redraw the brush or dispatch any events to listeners. To redraw the brush, call [brush](#wiki-_brush) on a selection or transition.

<a name="brush_clear" href="#wiki-brush_clear">#</a> brush.**clear**()

…

<a name="brush_empty" href="#wiki-brush_empty">#</a> brush.**empty**()

…

<a name="brush_on" href="#wiki-brush_on">#</a> brush.**on**(*type*[, *listener*])

…