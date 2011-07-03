> [[API Reference]] ▸ [[Layouts]]

![pie](pie.png)

<a name="pie" href="#pie">#</a> d3.layout.<b>pie</b>()

<a name="_pie" href="#_pie">#</a> pie(<i>array</i>[, <i>index</i>])

<a name="value" href="#value">#</a> pie.<b>value</b>([<i>accessor</i>])

Specifies how to extract a value from the associated data; *accessor* is a function which is invoked on each input value passed to [pie](#_pie), equivalent to calling *array.map(accessor)* before computing the pie layout. The default value function is the built-in [Number](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number), which is similar to the identity function. If *accessor* is not specified, returns the current value accessor.

<a name="sort" href="#sort">#</a> pie.<b>sort</b>([<i>comparator</i>])

<a name="startAngle" href="#startAngle">#</a> pie.<b>startAngle</b>([<i>angle</i>])

<a name="endAngle" href="#endAngle">#</a> pie.<b>endAngle</b>([<i>angle</i>])
