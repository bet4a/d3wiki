> [[API Reference]]

**Scales** are functions that map from an input domain to an output range. **Ordinal** scales have a discrete domain, such as a set of names or categories. There are also [[quantitative scales|Quantitative-Scales]], which have a continuous domain, such the set of real numbers. Scales are an optional feature in D3; you don't have to use them, if you prefer to do the math yourself. However, using scales can greatly simplify the code needed to map a dimension of data to a visual representation.

A scale object, such as that returned by [d3.scale.ordinal](#ordinal), is both an object and a function. That is: you can call the scale like any other function, and the scale has additional methods that change its behavior. Like other classes in D3, scales follow the method chaining pattern where setter methods return the scale itself, allowing multiple setters to be invoked in a concise statement.

<a name="ordinal" href="#ordinal">#</a> d3.scale.<b>ordinal</b>()

…

<a name="ordinal_domain" href="#ordinal_domain">#</a> ordinal.<b>domain</b>(<i>values</i>)

…

<a name="ordinal_range" href="#ordinal_range">#</a> ordinal.<b>range</b>(<i>values</i>)

…

<a name="ordinal_rangePoints" href="#ordinal_rangePoints">#</a> ordinal.<b>rangePoints</b>(<i>values</i>[, <i>padding</i>])

…

<a name="ordinal_rangeBands" href="#ordinal_rangeBands">#</a> ordinal.<b>rangeBands</b>(<i>values</i>[, <i>padding</i>])

…

<a name="ordinal_rangeRoundBands" href="#ordinal_rangeRoundBands">#</a> ordinal.<b>rangeRoundBands</b>(<i>values</i>[, <i>padding</i>])

…

<a name="ordinal_rangeBand" href="#ordinal_rangeBand">#</a> ordinal.<b>rangeBand</b>()

…