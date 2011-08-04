> [[API Reference]] ▸ [[Layouts]]

A **histogram layout** shows the distribution of data by grouping discrete data points into bins.

<a name="histogram" href="Histogram-Layout#histogram">#</a> d3.layout.<b>histogram</b>()

Constructs a new histogram function with the default value accessor, range function, and bin function. By default, the histogram function returns frequencies. The returned layout object is both an object and a function. That is: you can call the layout like any other function, and the layout has additional methods that change its behavior. Like other classes in D3, layouts follow the method chaining pattern where setter methods return the layout itself, allowing multiple setters to be invoked in a concise statement.

<a name="_histogram" href="Histogram-Layout#_histogram">#</a> <b>histogram</b>(<i>values</i>[, <i>index</i>])

Evaluates the histogram function on the specified array of *values*. An optional *index* may be specified, which is passed along to the range and bin function. The return value is an array of arrays: each element in the outer array represents a bin, and each bin contains the associated elements from the input *values*. In addition, each bin has three attributes:

* x - the lower bound of the bin (inclusive).
* dx - the width of the bin; x + dx is the upper bound (exclusive).
* y - the count (if [frequency](#frequency) is true), or the probability (if frequency is false).

Note that the y attribute is the same as the length attribute, in frequency mode.

<a name="value" href="Histogram-Layout#value">#</a> histogram.<b>value</b>([<i>accessor</i>])

Specifies how to extract a value from the associated data; *accessor* is a function which is invoked on each input value passed to [histogram](#_histogram), equivalent to calling *values.map(accessor)* before computing the histogram. The default value function is the built-in [Number](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number), which is similar to the identity function. If *accessor* is not specified, returns the current value accessor.

<a name="range" href="Histogram-Layout#range">#</a> histogram.<b>range</b>([<i>range</i>])

Specifies the range of the histogram. Values outside the specified range will be ignored. The *range* may be specified either as a two-element array representing the minimum and maximum value of the range, or as a function that returns the range given the array of *values* and the current *index* passed to [histogram](#_histogram). The default range is the extent ([minimum](Arrays#d3_min) and [maximum](Arrays#d3_max)) of the values. If *range* is not specified, returns the current range function.

<a name="bins" href="Histogram-Layout#bins">#</a> histogram.<b>bins</b>([<i>bins</i>])

Specifies how to bin values in the histogram. The *bins* may be specified as a number, in which case the range of values will be split uniformly into the given number of bins. Or, *bins* may be an array of threshold values, defining the bins; the specified array must contain the rightmost (upper) value, thus specifying *n* + 1 values for *n* bins. Or, *bins* may be a function which is evaluated, being passed the [range](#range), the array of *values* and the current *index* passed to [histogram](#_histogram), returning an array of thresholds. The default bin function will divide the values into uniform bins using [Sturges' formula](http://en.wikipedia.org/wiki/Histogram).

<a name="frequency" href="Histogram-Layout#frequency">#</a> histogram.<b>frequency</b>([<i>frequency</i>])

Specifies whether the histogram's `y` value is a count (frequency) or a probability (density); the default is frequency. If *frequency* is not specified, returns the current frequency boolean.
