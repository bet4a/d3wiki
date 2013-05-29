> [Wiki](Home) ▸ [[API Reference]] ▸ [[SVG]] ▸ **SVG Controls**

## Brush

<a name="brush" href="#wiki-brush">#</a> d3.svg.<b>brush</b>()

Constructs a new brush with no default *x*- and *y*-scale, and an empty extent.

<a name="_brush" href="#wiki-_brush">#</a> <b>brush</b>(<i>selection</i>)

Draws or redraws this brush into the specified *selection* of elements. The brush may be drawn into multiple elements simultaneously, but note that these brushes would share the same backing extent; typically, a brush is drawn into only one element at a time.

The *selection* can also be a [transition](Transitions); however, the brush does not yet support automatic transitions, so the redraw will happen instantaneously. In a subsequent release, the brush will smoothly transition to the new extent when redrawn after the [extent](#wiki-brush_extent) is set.

<a name="brush_x" href="#wiki-brush_x">#</a> brush.<b>x</b>([<i>scale</i>])

Gets or sets the *x*-scale associated with the brush. If *scale* is specified, sets the *x*-scale to the specified scale and returns the brush; if *scale* is not specified, returns the current *x*-scale, which defaults to null. The scale is typically defined as a [quantitative scale](Quantitative-Scales), in which case the [extent](#wiki-extent) is in data space from the scale's [domain](Quantitative-Scales#wiki-linear_domain); however, it may instead be defined as an [ordinal scale](Ordinal-Scales), where the extent is in pixel space from the scale's [range extent](Ordinal-Scales#wiki-ordinal_rangeExtent).

<a name="brush_y" href="#wiki-brush_y">#</a> brush.<b>y</b>([<i>scale</i>])

Gets or sets the *y*-scale associated with the brush. If *scale* is specified, sets the *y*-scale to the specified scale and returns the brush; if *scale* is not specified, returns the current *y*-scale, which defaults to null. The scale is typically defined as a [quantitative scale](Quantitative-Scales), in which case the [extent](#wiki-extent) is in data space from the scale's [domain](Quantitative-Scales#wiki-linear_domain); however, it may instead be defined as an [ordinal scale](Ordinal-Scales), where the extent is in pixel space from the scale's [range extent](Ordinal-Scales#wiki-ordinal_rangeExtent).

<a name="brush_extent" href="#wiki-brush_extent">#</a> brush.<b>extent</b>([<i>values</i>])

Gets or sets the current brush extent. If *values* is specified, sets the extent to the specified values and returns the brush; if *values* is not specified, returns the current extent. The definition of the extent depends on the associated scales. If both an *x*- and *y*-scale are available, then the extent is the two-dimensional array [‍[ *x0*, *y0* ], [ *x1*, *y1* ]], where *x0* and *y0* are the lower bounds of the extent, and *x1* and *y1* are the upper bounds of the extent. If only the *x*-scale is available, then the extent is defined as the one-dimensional array [ *x0*, *x1* ]; likewise, if only the *y*-scale is available, then the extent is [ *y0*, *y1* ]. In neither scale is available, then the extent is null.

When the extent is set to *values*, the resulting extent is preserved exactly. However, as soon as the brush is moved by the user (on mousemove following a mousedown), then the extent must be recomputed by calling [scale.invert](Quantitative-Scales#wiki-linear_invert). Note that the values may be slightly imprecise due to the limited precision of pixels.

Note that this does not automatically redraw the brush or dispatch any events to listeners. To redraw the brush, call [brush](#wiki-_brush) on a selection or transition.

<a name="brush_clear" href="#wiki-brush_clear">#</a> brush.<b>clear</b>()

Clears the extent, making the brush extent [empty](#wiki-brush_empty).

<a name="brush_empty" href="#wiki-brush_empty">#</a> brush.<b>empty</b>()

Returns true if and only if the brush extent is empty. When a brush is created, it is initially empty; the brush may also become empty with a single click on the background without moving, or if the extent is [cleared](#wiki-brush_clear). A brush is considered empty if it has zero-width or zero-height. When the brush is empty, its extent is not strictly defined.

<a name="brush_on" href="#wiki-brush_on">#</a> brush.<b>on</b>(<i>type</i>[, <i>listener</i>])

Gets or sets the *listener* for the specified event *type*. Brushes support three types of events:

* brushstart - on mousedown
* brush - on mousemove, if the brush extent has changed
* brushend - on mouseup

Note that when clicking on the background, a mousedown also triggers a brushmove, since the brush extent is immediately cleared to start a new extent.