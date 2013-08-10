> [Wiki](Home) ▸ [[API Reference]] ▸ [[SVG]] ▸ **SVG Axes**

D3’s [axis component](http://bl.ocks.org/1166403) displays reference lines for scales automatically. This lets you focus on displaying the data, while the axis component takes care of the tedious task of drawing axes and labeled ticks.

## Axis

The axis component is designed to work with D3’s [quantitative](Quantitative-Scales), [time](Time-Scales) and [ordinal](Ordinal-Scales) scales.

<a name="axis" href="SVG-Axes#wiki-axis">#</a> d3.svg.<b>axis</b>()

Create a new default axis.

<a name="_axis" href="SVG-Axes#wiki-_axis">#</a> <b>axis</b>(<i>selection</i>)

Apply the axis to a [selection](Selections) or [transition](Transitions). The selection must contain an SVG or G element. For example:

```js
d3.select("body").append("svg")
    .attr("class", "axis")
    .attr("width", 1440)
    .attr("height", 30)
  .append("g")
    .attr("transform", "translate(0,30)")
    .call(axis);
```

<a name="scale" href="#wiki-scale">#</a> axis.<b>scale</b>([<i>scale</i>])

Get or set the associated scale. If *scale* is specified, sets the scale and returns the axis. If *scale* is not specified, returns the current scale which defaults to a linear scale.

<a name="orient" href="#wiki-orient">#</a> axis.<b>orient</b>([<i>orientation</i>])

Get or set the position of the ticks and their labels in relation to the axis path. If instead you want to determine the position of the axis with respect to the plot, use the [[transform|http://www.w3.org/TR/SVG/coords.html#TransformAttribute]] attribute. If *orientation* is specified, sets the axis *orientation* and returns the axis. If *orientation* is not specified, returns the current orientation, which defaults to "bottom". Valid values are "top", "bottom", "left" and "right". For a vertical axis, specify "left" or "right"; for a horizontal axis, specify "top" or "bottom".

<a name="ticks" href="#wiki-ticks">#</a> axis.<b>ticks</b>([<i>arguments…</i>])

Get or set the arguments that are passed to the underlying scale’s tick function. The specified *arguments* are passed to scale.ticks to compute the tick values. For [quantitative scales](Quantitative-Scales#wiki-linear_ticks), specify the desired tick count such as `axis.ticks(20)`. For [time scales](Time-Scales#wiki-ticks), you can pass in a count or a function, such as `axis.ticks(d3.time.minutes, 15)`.

The *arguments* are also passed to the scale’s tickFormat method to generate the default tick format. Thus, for [log scales](Quantitative-Scales#wiki-log_tickFormat), you might specify both a count and a tick format function.

<a name="tickValues" href="#wiki-tickValues">#</a> axis.<b>tickValues</b>([<i>values</i>])

Get or set the explicit tick values. If the array *values* is specified, the values are used to generate ticks rather than using the scale's tick generator. If *values* is null, clears any previously-set explicit tick values, reverting back to the scale's tick generator. If *values* is not specified, returns the currently-set tick values, if any. For example, to generate ticks at specific values:

```js
var xAxis = d3.svg.axis()
    .scale(x)
    .tickValues([1, 2, 3, 5, 8, 13, 21]);
```

The explicit tick values take precedent over the tick arguments set by [axis.ticks](#axis_ticks). Note, however, that the tick arguments are still passed to the scale's [tickFormat](Quantitative-Scales#wiki-linear_tickFormat) function if tick format is not also set. Thus, it is valid to set both axis.ticks and axis.tickValues.

<a name="tickSubdivide" href="#wiki-tickSubdivide">#</a> axis.<b>tickSubdivide</b>([<i>count</i>])

Get or set the tick subdivision count. If *count* is specified, sets the number of uniform subdivision ticks to make **between major tick marks** and returns the axis. If *count* is not specified, returns the current subdivision tick count which defaults to zero. The specified *count* specifies the number of _minor_ ticks, which is one less than the number of _subdivisions_. For example, `axis.tickSubdivide(true)` produces one minor tick per major tick, thus cutting the space between each major tick in two. As another example, decimal subdivision is specified as `axis.tickSubdivide(9)`.

<a name="tickSize" href="#wiki-tickSize">#</a> axis.<b>tickSize</b>([<i>major</i>[​[, <i>minor</i>], <i>end</i>]])

If *major* is specified, sets the major tick size and returns the axis. If *major* and *end* are specified, sets the major and minor tick sizes to *major*, the end tick size to *end*, and returns the axis. If *major*, *minor* and *end* are specified, sets the respective tick sizes and returns the axis. If no arguments are specified, returns the current major tick size, which defaults to 6. For example:

```js
axis.tickSize(); // returns the current major tick size
axis.tickSize(6); // sets the major, minor and end to 6
axis.tickSize(6, 0); // sets major and minor to 6, end to 0
axis.tickSize(6, 3, 0); // sets major to 6, minor to 3, and end to 0
```

Note that the end ticks are actually part of the domain path rather than discrete tick elements; their position is determined by the associated scale's domain extent rather than the scale’s tick generator (or the axis’s tick values if specified explicitly). Thus, end ticks may overlap with the first or last tick. An end tick size of 0 suppresses end ticks, producing a straight line for the domain path.

<a name="tickPadding" href="#wiki-tickPadding">#</a> axis.<b>tickPadding</b>([<i>padding</i>])

Set or get the padding between ticks and tick labels. If *padding* is specified, sets the padding to the specified value in pixels and returns the axis. If *padding* is not specified, returns the current padding which defaults to 3 pixels.

<a name="tickFormat" href="#wiki-tickFormat">#</a> axis.<b>tickFormat</b>([<i>format</i>])

Set or get the tick value formatter for labels. If *format* is specified, sets the format to the specified function and returns the axis. If *format* is not specified, returns the current format function, which defaults to null. A null format indicates that the scale's default formatter should be used, which is generated by calling [scale.tickFormat](Quantitative-Scales#wiki-linear_tickFormat). In this case, the arguments specified by [ticks](#wiki-ticks) are likewise passed to scale.tickFormat.

See [d3.format](Formatting#wiki-d3_format) for help creating formatters. For example, `axis.tickFormat(d3.format(",.0f"))` will display integers with comma-grouping for thousands. Defining the formatter first: `var commasFormatter = d3.format(",.0f")` lets you to call it as a function of your data, for example, to add currency units in front of the comma-grouped integers: `.tickFormat(function(d) { return "$" + commasFormatter(d); })`.

Note: for log scales, the number of ticks cannot be customized; however, the number of tick labels *can* be customized via [ticks](#wiki-ticks). Likewise, the tick formatter for log scales is typically specified via ticks rather than tickFormat, so as to preserve the default label-hiding behavior.