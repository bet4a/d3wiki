> [[API Reference]]

**Scales** are functions that map from an input domain to an output range. **Quantitative** scales have a continuous domain, such as the set of real numbers, or dates. There are also [[ordinal scales|Ordinal-Scales]], which have a discrete domain, such as a set of names or categories. Scales are an optional feature in D3; you don't have to use them, if you prefer to do the math yourself. However, using scales can greatly simplify the code needed to map a dimension of data to a visual representation.

A scale object, such as that returned by [d3.scale.linear](#linear), is both an object and a function. That is: you can call the scale like any other function, and the scale has additional methods that change its behavior. Like other classes in D3, scales follow the method chaining pattern where setter methods return the scale itself, allowing multiple setters to be invoked in a concise statement.

## Linear Scales

Linear scales are the most common scale, and a good default choice to map a continuous input domain to a continuous output range. The mapping is *linear* in that the output range value *y* can be expressed as a linear function of the input domain value *x*: *y* = *mx* + *b*. The input domain is typically a dimension of the data that you want to visualize, such as the height of students (measured in meters) in a sample population. The output range is typically a dimension of the desired output visualization, such as the height of bars (measured in pixels) in a histogram.

<a name="linear" href="#linear">#</a> d3.scale.<b>linear</b>()

Constructs a new linear scale with the default domain [0,1] and the default range [0,1]. The returned scale is a function that takes a single argument *x* representing a value in the input domain; the return value is the corresponding value in the output range. Thus, the default linear scale is equivalent to the identity function for numbers; for example linear(0.5) returns 0.5.

<a name="linear_invert" href="#linear_invert">#</a> linear.<b>invert</b>(<i>y</i>)

Returns the value in the input domain *x* for the corresponding value in the output range *y*. This represents the inverse mapping from range to domain. For a valid value *y* in the output range, linear(linear.invert(*y*)) equals *y*; similarly, for a valid value *x* in the input domain, linear.invert(linear(*x*)) equals *x*. Equivalently, you can construct the invert operator by building a new scale while swapping the domain and range. The invert operator is particularly useful for interaction, say to determine the value in the input domain that corresponds to the pixel location under the mouse.

Note: the invert operator is only supported if the output range is numeric! D3 allows the output range to be any type; under the hood, [[d3.interpolate|Transitions#d3_interpolate]] or a custom interpolator of your choice is used to map the normalized parameter *t* to a value in the output range. Thus, the output range may be colors, strings, or even arbitrary objects. As there is no facility to "uninterpolate" arbitrary types, the invert operator is currently supported only on numeric ranges.

<a name="linear_domain" href="#linear_domain">#</a> linear.<b>domain</b>([<i>numbers</i>])

If *numbers* is specified, sets the scale's input domain to the specified array of numbers. The array must contain two or more numbers. If the elements in the given array are not numbers, they will be coerced to numbers; this coercion happens similarly when the scale is called. Thus, a linear can be used to encode types such as [[date objects|https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Date]] that can be converted to numbers. (You can implement your own convertible number objects using [[valueOf|https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object/valueOf]].) If *numbers* is not specified, returns the scale's current input domain.

Although linear scales typically have just two numeric values in their domain, you can specify more than two values for a *polylinear* scale. In this case, there must be an equivalent number of values in the output range. A polylinear scale represents multiple piecewise linear scales that divide a continuous domain and range. This is particularly useful for defining diverging quantitative scales. For example, to interpolate between white and red for negative values, and white and green for positive values, say:

    var color = d3.scale.linear()
        .domain([-1, 0, 1])
        .range(["red", "white", "green"]);

The resulting value of color(-.5) is "#ff8080", and the value of color(.5) is "#80c080". Internally, polylinear scales perform a binary search for the output interpolator corresponding to the given domain value. By repeating values in both the domain and range, you can also force a chunk of the input domain to map to a constant in the output range.

<a name="linear_range" href="#linear_range">#</a> linear.<b>range</b>([<i>values</i>])

If *values* is specified, sets the scale's output range to the specified array of values. The array must contain two or more values, to match the cardinality of the input domain. The elements in the given array need not be numbers; any value that is supported by the underlying [interpolator](#linear_interpolate) will work. However, numeric ranges are required for the invert operator. If *values* is not specified, returns the scale's current output range.

<a name="linear_rangeRound" href="#linear_rangeRound">#</a> linear.<b>rangeRound</b>(<i>values</i>)

Sets the scale's output range to the specified array of values, while also setting the scale's interpolator to [[d3.interpolateRound|Transitions#d3_interpolateRound]]. This is a convenience routine for when the values output by the scale should be exact integers, such as to avoid antialiasing artifacts. It is also possible to round the output values manually after the scale is applied.

<a name="linear_interpolate" href="#linear_interpolate">#</a> linear.<b>interpolate</b>([<i>factory</i>])

If *factory* is specified, sets the scale's output interpolator using the specified *factory*. The interpolator factory defaults to [[d3.interpolate|Transitions#d3_interpolate]], and is used to map the normalized domain parameter *t* in [0,1] to the corresponding value in the output range. The interpolator factory will be used to construct interpolators for each adjacent pair of values from the output range.

If *factory* is not specified, returns the scale's interpolator factory.

<a name="linear_clamp" href="#linear_clamp">#</a> linear.<b>clamp</b>([<i>boolean</i>])

If *boolean* is specified, enables or disables clamping accordingly. By default, clamping is disabled, such that if a value outside the input domain is passed to the scale, the scale may return a value outside the output range through linear extrapolation. For example, with the default domain and range of [0,1], an input value of 2 will return an output value of 2. If clamping is enabled, the normalized domain parameter *t* is clamped to the range [0,1], such that the return value of the scale is always within the scale's output range.

If *boolean* is not specified, returns whether or not the scale currently clamps values to within the output range.

<a name="linear_ticks" href="#linear_ticks">#</a> linear.<b>ticks</b>(<i>count</i>)

Returns approximately *count* representative values from the scale's input domain. The returned tick values are uniformly spaced, have human-readable values (such as multiples of powers of 10), and are guaranteed to be within the extent of the input domain. Ticks are often used to display reference lines, or tick marks, in conjunction with the visualized data. The specified *count* is only a hint; the scale may return more or fewer values depending on the input domain.

<a name="linear_tickFormat" href="#linear_tickFormat">#</a> linear.<b>tickFormat</b>(<i>count</i>)

Returns a [[number format|Formatting#d3_format]] function suitable for displaying a tick value. The specified *count* should have the same value as the count that is used to generate the tick values. You don't have to use the scale's built-in tick format, but it automatically computes the appropriate precision based on the fixed interval between tick values.

## Power Scales

<a name="sqrt" href="#sqrt">#</a> d3.scale.<b>sqrt</b>()

<a name="pow" href="#pow">#</a> d3.scale.<b>pow</b>()

<a name="pow_invert" href="#pow_invert">#</a> pow.<b>invert</b>(<i>y</i>)

<a name="pow_domain" href="#pow_domain">#</a> pow.<b>domain</b>([<i>values</i>])

<a name="pow_range" href="#pow_range">#</a> pow.<b>range</b>([<i>values</i>])

<a name="pow_rangeRound" href="#pow_rangeRound">#</a> pow.<b>rangeRound</b>(<i>values</i>)

<a name="pow_interpolate" href="#pow_interpolate">#</a> pow.<b>interpolate</b>([<i>interpolator</i>])

<a name="pow_clamp" href="#pow_clamp">#</a> pow.<b>clamp</b>([<i>boolean</i>])

<a name="pow_ticks" href="#pow_ticks">#</a> pow.<b>ticks</b>([<i>count</i>])

<a name="pow_tickFormat" href="#pow_tickFormat">#</a> pow.<b>tickFormat</b>([<i>count</i>])

## Log Scales

<a name="log" href="#log">#</a> d3.scale.<b>log</b>()

<a name="log_invert" href="#log_invert">#</a> log.<b>invert</b>(<i>y</i>)

<a name="log_domain" href="#log_domain">#</a> log.<b>domain</b>([<i>values</i>])

<a name="log_range" href="#log_range">#</a> log.<b>range</b>([<i>values</i>])

<a name="log_rangeRound" href="#log_rangeRound">#</a> log.<b>rangeRound</b>(<i>values</i>)

<a name="log_interpolate" href="#log_interpolate">#</a> log.<b>interpolate</b>([<i>interpolator</i>])

<a name="log_clamp" href="#log_clamp">#</a> log.<b>clamp</b>([<i>boolean</i>])

<a name="log_ticks" href="#log_ticks">#</a> log.<b>ticks</b>()

<a name="log_tickFormat" href="#log_tickFormat">#</a> log.<b>tickFormat</b>()

## Quantize Scales

<a name="quantize" href="#quantize">#</a> d3.scale.<b>quantize</b>()

<a name="quantize_domain" href="#quantize_domain">#</a> quantize.<b>domain</b>([<i>values</i>])

<a name="quantize_range" href="#quantize_range">#</a> quantize.<b>range</b>([<i>values</i>])

## Quantile Scales

<a name="quantile" href="#quantile">#</a> d3.scale.<b>quantile</b>()

<a name="quantile_domain" href="#quantile_domain">#</a> quantile.<b>domain</b>([<i>values</i>])

<a name="quantile_range" href="#quantile_range">#</a> quantile.<b>range</b>([<i>values</i>])

<a name="quantile_quantiles" href="#quantile_quantiles">#</a> quantile.<b>quantiles</b>()
