> [[API Reference]] ▸ [[SVG]]

D3’s [axis component](http://bl.ocks.org/1166403) displays reference lines for scales automatically. This lets you focus on displaying the data, while the axis component takes care of the tedious task of drawing axes and labeled ticks.

## Axis

The axis component is designed to work with any of D3’s [quantitative scales](Quantitative-Scales).

<a name="axis" href="SVG-Axes#wiki-axis">#</a> d3.svg.<b>axis</b>()

<a name="_axis" href="SVG-Axes#wiki-_axis">#</a> <b>axis</b>(<i>selection</i>)

The *selection* can also be a [transition](Transitions).

<a name="axis_scale" href="SVG-Axes#wiki-axis_scale">#</a> axis.<b>scale</b>([<i>scale</i>])

<a name="axis_orient" href="SVG-Axes#wiki-axis_orient">#</a> axis.<b>orient</b>([<i>orientation</i>])

<a name="axis_ticks" href="SVG-Axes#wiki-axis_ticks">#</a> axis.<b>ticks</b>([<i>arguments…</i>])

<a name="axis_tickSubdivide" href="SVG-Axes#wiki-axis_tickSubdivide">#</a> axis.<b>tickSubdivide</b>([<i>n</i>])

<a name="axis_tickSize" href="SVG-Axes#wiki-axis_tickSize">#</a> axis.<b>tickSize</b>([<i>major</i>[​[, <i>minor</i>], <i>end</i>]])

<a name="axis_tickPadding" href="SVG-Axes#wiki-axis_tickPadding">#</a> axis.<b>tickPadding</b>([<i>padding</i>])

<a name="axis_tickFormat" href="SVG-Axes#wiki-axis_tickFormat">#</a> axis.<b>tickFormat</b>([<i>format</i>])

A [format](Formatting#wiki-d3_format) can be passed to override the scale's default.
