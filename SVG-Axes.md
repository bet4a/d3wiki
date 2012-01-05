> [[API Reference]] ▸ [[SVG]]

D3’s [axis component](http://bl.ocks.org/1166403) displays reference lines for scales automatically. This lets you focus on displaying the data, while the axis component takes care of the tedious task of drawing axes and labeled ticks.

## Axis

The axis component is designed to work with any of D3’s [quantitative scales](Quantitative-Scales).

<a name="axis" href="SVG-Axes#wiki-axis">#</a> d3.svg.<b>axis</b>()

<a name="_axis" href="SVG-Axes#wiki-_axis">#</a> <b>axis</b>(<i>selection</i>)

The *selection* can also be a [transition](Transitions).

<a name="axis_scale" href="SVG-Axes#wiki-axis_scale">#</a> axis.<b>scale</b>([<i>scale</i>])

<a name="axis_orient" href="SVG-Axes#wiki-axis_orient">#</a> axis.<b>orient</b>([<i>orientation</i>])

Describes how to display the axis tick marks and numeric labels in relation to the axis line. Valid values are `top`, `bottom`, `left` and `right`. For a vertical axis, you should specify `left` or `right` and for a horizontal axis, you will want to specify `top` or `bottom`.

<a name="axis_ticks" href="SVG-Axes#wiki-axis_ticks">#</a> axis.<b>ticks</b>([<i>arguments…</i>])

Sets the number of labeled major tick marks. The specified *arguments* are passed to the scale’s ticks method to compute the tick values. For [quantitative scales](Quantitative-Scales#wiki-linear_ticks), specify the desired tick count such as axis.ticks(20). For [time scales](Time-Scales#wiki-ticks), you can pass in a count or a function, such as axis.ticks(d3.time.minutes, 15).

The *arguments* are also passed to the scale’s tickFormat method to generate the default tick format. Thus, for [log scales](Quantitative-Scales#wiki-log_tickFormat), you might specify both a count and a tick format function.

<a name="axis_tickSubdivide" href="SVG-Axes#wiki-axis_tickSubdivide">#</a> axis.<b>tickSubdivide</b>([<i>n</i>])

The number of subdivisions to make in between major tick marks.

<a name="axis_tickSize" href="SVG-Axes#wiki-axis_tickSize">#</a> axis.<b>tickSize</b>([<i>major</i>[​[, <i>minor</i>], <i>end</i>]])

The length of the major, minor and ending tick marks. The end tick mark is the last one drawn in the scale and depending on spacing, it may end up quite close to the tick mark that precedes it. You can pass 0 to suppress displaying it. For example:

```js
var yAxis = d3.svg.axis()
    .scale(y)
    .ticks(4)
    .tickSize(6, 3, 0);
```

This will give you major tick marks of size 6, minor of size 3 and no ending mark.

<a name="axis_tickPadding" href="SVG-Axes#wiki-axis_tickPadding">#</a> axis.<b>tickPadding</b>([<i>padding</i>])

<a name="axis_tickFormat" href="SVG-Axes#wiki-axis_tickFormat">#</a> axis.<b>tickFormat</b>([<i>format</i>])

A [format](Formatting#wiki-d3_format) can be passed to override the scale's default. For example, `axis.tickFormat(d3.format(",.0f"))` will display integers with comma-grouping for thousands. Note that for log scales, the tick format must be passed to the [ticks](#ticks) method, instead.