> [Wiki](Home) ▸ [[API Reference]] ▸ [[Behaviors]] ▸ **Zoom Behavior**

[![Pan+Zoom](http://bl.ocks.org/mbostock/raw/3892919/thumbnail.png)](http://bl.ocks.org/mbostock/3892919)
[![Zoomable Area](http://bl.ocks.org/mbostock/raw/4015254/thumbnail.png)](http://bl.ocks.org/mbostock/4015254)
[![Geometric Zooming](http://bl.ocks.org/mbostock/raw/3680999/thumbnail.png)](http://bl.ocks.org/mbostock/3680999)
[![d3.geo.tile](http://bl.ocks.org/mbostock/raw/4132797/thumbnail.png)](http://bl.ocks.org/mbostock/4132797)
[![Raster & Vector Zoom](http://bl.ocks.org/mbostock/raw/5914438/thumbnail.png)](http://bl.ocks.org/mbostock/5914438)
[![Zoomable Geography](http://bl.ocks.org/mbostock/raw/2374239/thumbnail.png)](http://bl.ocks.org/mbostock/2374239)

This behavior automatically creates event listeners to handle zooming and panning gestures on a container element. Both mouse and touch events are supported.

<a name="zoom" href="Zoom-Behavior#wiki-zoom">#</a> d3.behavior.<b>zoom</b>()

Constructs a new zoom behavior.

<a name="x" href="Zoom-Behavior#wiki-x">#</a> zoom.<b>x</b>([<i>x</i>])

Specifies an x-scale whose domain should be automatically adjusted when zooming. If not specified, returns the current x-scale, which defaults to null. If the scale's domain or range is modified programmatically, this function should be called again.

<a name="y" href="Zoom-Behavior#wiki-y">#</a> zoom.<b>y</b>([<i>y</i>])

Specifies an y-scale whose domain should be automatically adjusted when zooming. If not specified, returns the current y-scale, which defaults to null. If the scale's domain or range is modified programmatically, this function should be called again.

<a name="scaleExtent" href="Zoom-Behavior#wiki-scaleExtent">#</a> zoom.<b>scaleExtent</b>([<i>extent</i>])

Specifies the zoom scale's allowed range as a two-element array, [*minimum*, *maximum*]. If not specified, returns the current scale extent, which defaults to [0, Infinity].

<a name="scale" href="Zoom-Behavior#wiki-scale">#</a> zoom.<b>scale</b>([<i>scale</i>])

Specifies the current zoom scale. If not specified, returns the current zoom scale, which defaults to 1.

<a name="translate" href="Zoom-Behavior#wiki-translate">#</a> zoom.<b>translate</b>([<i>translate</i>])

Specifies the current zoom translation vector. If not specified, returns the current translation vector, which defaults to [0, 0].

<a name="on" href="Zoom-Behavior#wiki-on">#</a> zoom.<b>on</b>(<i>type</i>, <i>listener</i>)

Registers the specified *listener* to receive events of the specified *type* from the zoom behavior. Currently, only the "zoom" event is supported. When fired, the d3.event object will contain the following properties:

* "scale": a number; the current scale.
* "translate": a two-element array representing the current translation vector.