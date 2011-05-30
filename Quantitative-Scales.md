> [[API Reference]]

**Scales** are functions that map from an input domain to an output range. **Quantitative** scales have a continuous domain, such as the set of real numbers, or dates. There are also [[ordinal scales|Ordinal-Scales]], which have a discrete domain, such as a set of names or categories. Scales are an optional feature in D3; you don't have to use them, if you prefer to do the math yourself. However, using scales can greatly simplify the code needed to map a dimension of data to a visual representation.

A scale object, such as that returned by [d3.scale.linear](#linear), is both an object and a function. (In fact, every function is also an object in JavaScript, though not every object is a function.) That is, you can call the scale like any other function. And, the scale has additional methods that change its behavior, such as setting the domain.

## Linear Scales

Linear scales are the most common, and are used to map a continuous input domain to a continuous output range. The mapping is linear in that the output range value *y* can be expressed as a linear function of the input domain value *x*: *y* = *mx* + *b*. The input domain is typically a dimension of the data that you want to visualize, such as the height of students (measured in meters) in a sample population. The output range is typically a dimension of the desired visual encoding, such as the height of bars (measured in pixels) in a histogram.

<a name="linear" href="#linear">#</a> d3.scale.<b>linear</b>()

Constructs a new linear scale with the default domain [0,1] and the default range [0,1]. The returned scale is a function that takes a single argument *x* representing a value in the input domain; the return value is the corresponding value in the output range. Thus, the default linear scale is equivalent to the identity function for numbers; for example linear(0.5) returns 0.5.

<a name="linear_invert" href="#linear_invert">#</a> linear.<b>invert</b>(<i>y</i>)

<a name="linear_domain" href="#linear_domain">#</a> linear.<b>domain</b>([<i>values</i>])

<a name="linear_range" href="#linear_range">#</a> linear.<b>range</b>([<i>values</i>])

<a name="linear_rangeRound" href="#linear_rangeRound">#</a> linear.<b>rangeRound</b>(<i>values</i>)

<a name="linear_interpolate" href="#linear_interpolate">#</a> linear.<b>interpolate</b>([<i>interpolator</i>])

<a name="linear_clamp" href="#linear_clamp">#</a> linear.<b>clamp</b>([<i>boolean</i>])

<a name="linear_ticks" href="#linear_ticks">#</a> linear.<b>ticks</b>([<i>count</i>])

<a name="linear_tickFormat" href="#linear_tickFormat">#</a> linear.<b>tickFormat</b>([<i>count</i>])

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
