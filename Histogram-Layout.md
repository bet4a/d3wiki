> [[API Reference]] ▸ [[Layouts]]

<a name="histogram" href="#histogram">#</a> d3.layout.<b>histogram</b>()

Constructs a new histogram function with the default value accessor, range function, and bin function. By default, the histogram function returns frequencies.

<a name="_histogram" href="#_histogram">#</a> <b>histogram</b>(<i>values</i>[, <i>index</i>])

Evaluates the histogram function on the specified array of *values*. An optional *index* may be specified, which is passed along to the range and bin function.

<a name="value" href="#value">#</a> histogram.<b>value</b>([<i>value</i>])

Specifies how to extract a value from the associated data. The default value function is `Number`, which is equivalent to the identity function.

<a name="range" href="#range">#</a> histogram.<b>range</b>([<i>range</i>])

Specifies the range of the histogram. Values outside the specified range will be ignored. The argument `x` may be specified either as a two-element array representing the minimum and maximum value of the range, or as a function that returns the range given the array of values and the current index `i`. The default range is the extent (minimum and maximum) of the values.

<a name="bins" href="#bins">#</a> histogram.<b>bins</b>([<i>bins</i>])

Specifies how to bin values in the histogram. The argument `x` may be specified as a number, in which case the range of values will be split uniformly into the given number of bins. Or, `x` may be an array of threshold values, defining the bins; the specified array must contain the rightmost (upper) value, thus specifying n + 1 values for n bins. Or, `x` may be a function which is evaluated, being passed the range, the array of values, and the current index `i`, returning an array of thresholds. The default bin function will divide the values into uniform bins using [Sturges' formula](http://en.wikipedia.org/wiki/Histogram).

<a name="frequency" href="#frequency">#</a> histogram.<b>frequency</b>([<i>frequency</i>])

Specifies whether the histogram's `y` value is a count (frequency) or a probability (density). The default value is true.
