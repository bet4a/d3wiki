> [Wiki](Home) ▸ [[API Reference]] ▸ [[Scales]] ▸ **Ordinal Scales**

**Scales** are functions that map from an input domain to an output range. **Ordinal** scales have a discrete domain, such as a set of names or categories. There are also [[quantitative scales|Quantitative-Scales]], which have a continuous domain, such the set of real numbers. Scales are an optional feature in D3; you don't have to use them, if you prefer to do the math yourself. However, using scales can greatly simplify the code needed to map a dimension of data to a visual representation.

A scale object, such as that returned by [d3.scale.ordinal](Ordinal-Scales#wiki-ordinal), is both an object and a function. That is: you can call the scale like any other function, and the scale has additional methods that change its behavior. Like other classes in D3, scales follow the method chaining pattern where setter methods return the scale itself, allowing multiple setters to be invoked in a concise statement.

<a name="ordinal" href="Ordinal-Scales#wiki-ordinal">#</a> d3.scale.<b>ordinal</b>()

Constructs a new ordinal scale with an empty domain and an empty range. The ordinal scale is invalid (always returning undefined) until an output range is specified.

<a name="_ordinal" href="Ordinal-Scales#wiki-_ordinal">#</a> <b>ordinal</b>(<i>x</i>)

Given a value *x* in the input domain, returns the corresponding value in the output range.

<a name="ordinal_domain" href="Ordinal-Scales#wiki-ordinal_domain">#</a> ordinal.<b>domain</b>([<i>values</i>])

If *values* is specified, sets the input domain of the ordinal scale to the specified array of values. The first element in *values* will be mapped to the first element in the output range, the second domain value to the second range value, and so on. Domain values are stored internally in an associative array as a mapping from value to index; the resulting index is then used to retrieve a value from the output range. Thus, an ordinal scale's values must be coercible to a string, and the stringified version of the domain value uniquely identifies the corresponding range value. If *values* is not specified, this method returns the current domain.

Setting the domain on an ordinal scale is optional. If no domain is set, each unique value that is passed to the scale function will be assigned a new value from the output range; in other words, the domain will be inferred implicitly from usage. However, it is a good idea to assign the ordinal scale's domain to ensure deterministic behavior, as inferring the domain from usage will be dependent on ordering. If the domain is set explicitly, values passed to the scale that were not explicitly part of the domain will be added. The return value of the domain method when called with no arguments will contain both explicitly-added and implicitly-added domain values.

<a name="ordinal_range" href="Ordinal-Scales#wiki-ordinal_range">#</a> ordinal.<b>range</b>([<i>values</i>])

If *values* is specified, sets the output range of the ordinal scale to the specified array of values. The first element in the domain will be mapped to the first element in *values*, the second domain value to the second range value, and so on. If there are fewer elements in the range than in the domain, the scale will recycle values from the start of the range. If *values* is not specified, this method returns the current output range.

This method is intended for when the set of discrete output values is computed explicitly, such as a set of categorical colors. In other cases, such as determining the layout of an ordinal scatterplot or bar chart, you may find the [rangePoints](Ordinal-Scales#wiki-rangePoints) or [rangeBands](Ordinal-Scales#wiki-rangeBands) operators more convenient.

<a name="ordinal_rangePoints" href="Ordinal-Scales#wiki-ordinal_rangePoints">#</a> ordinal.<b>rangePoints</b>(<i>interval</i>[, <i>padding</i>])

Sets the output range from the specified continuous *interval*. The array *interval* contains two elements representing the minimum and maximum numeric value. This interval is subdivided into *n* evenly-spaced points, where *n* is the number of (unique) values in the input domain. The first and last point may be offset from the edge of the interval according to the specified *padding*, which defaults to zero. The *padding* is expressed as a multiple of the spacing between points. A reasonable value is 1.0, such that the first and last point will be offset from the minimum and maximum value by half the distance between points.

<a name="ordinal_rangeBands" href="Ordinal-Scales#wiki-ordinal_rangeBands">#</a> ordinal.<b>rangeBands</b>(<i>interval</i>[, <i>padding</i>])

Sets the output range from the specified continuous *interval*. The array *interval* contains two elements representing the minimum and maximum numeric value. This interval is subdivided into *n* evenly-spaced bands, where *n* is the number of (unique) values in the domain. The bands may be offset from the edge of the interval and other bands according to the specified *padding*, which defaults to zero. The padding is typically in the range [0,1] and corresponds to the amount of space in the range interval to allocate to padding. A value of 0.5 means that the band width will be equal to the padding width.

<a name="ordinal_rangeRoundBands" href="Ordinal-Scales#wiki-ordinal_rangeRoundBands">#</a> ordinal.<b>rangeRoundBands</b>(<i>interval</i>[, <i>padding</i>])

Like [rangeBands](Ordinal-Scales#wiki-rangeBands), except guarantees that the band width and offset is a integer value, so as to avoid antialiasing artifacts.

<a name="ordinal_rangeBand" href="Ordinal-Scales#wiki-ordinal_rangeBand">#</a> ordinal.<b>rangeBand</b>()

Returns the band width. This method is used in conjunction with rangeBands or rangeRoundBands.

<a name="ordinal_rangeExtent" href="Ordinal-Scales#wiki-ordinal_rangeExtent">#</a> ordinal.<b>rangeExtent</b>()

Returns a two-element array representing the extent of the scale's range, i.e., the smallest and largest values.

<a name="ordinal_copy" href="#wiki-ordinal_copy">#</a> ordinal.<b>copy</b>()

Returns an exact copy of this ordinal scale. Changes to this scale will not affect the returned scale, and vice versa.

## Categorical Colors

<a name="category10" href="Ordinal-Scales#wiki-category10">#</a> d3.scale.<b>category10</b>()

Constructs a new ordinal scale with a range of ten categorical colors:
<font color="#1f77b4">#1f77b4</font>
<font color="#ff7f0e">#ff7f0e</font>
<font color="#2ca02c">#2ca02c</font>
<font color="#d62728">#d62728</font>
<font color="#9467bd">#9467bd</font>
<font color="#8c564b">#8c564b</font>
<font color="#e377c2">#e377c2</font>
<font color="#7f7f7f">#7f7f7f</font>
<font color="#bcbd22">#bcbd22</font>
<font color="#17becf">#17becf</font>.

<a name="category20" href="Ordinal-Scales#wiki-category20">#</a> d3.scale.<b>category20</b>()

Constructs a new ordinal scale with a range of twenty categorical colors:
<font color="#1f77b4">#1f77b4</font>
<font color="#aec7e8">#aec7e8</font>
<font color="#ff7f0e">#ff7f0e</font>
<font color="#ffbb78">#ffbb78</font>
<font color="#2ca02c">#2ca02c</font>
<font color="#98df8a">#98df8a</font>
<font color="#d62728">#d62728</font>
<font color="#ff9896">#ff9896</font>
<font color="#9467bd">#9467bd</font>
<font color="#c5b0d5">#c5b0d5</font>
<font color="#8c564b">#8c564b</font>
<font color="#c49c94">#c49c94</font>
<font color="#e377c2">#e377c2</font>
<font color="#f7b6d2">#f7b6d2</font>
<font color="#7f7f7f">#7f7f7f</font>
<font color="#c7c7c7">#c7c7c7</font>
<font color="#bcbd22">#bcbd22</font>
<font color="#dbdb8d">#dbdb8d</font>
<font color="#17becf">#17becf</font>
<font color="#9edae5">#9edae5</font>.

<a name="category20b" href="Ordinal-Scales#wiki-category20b">#</a> d3.scale.<b>category20b</b>()

Constructs a new ordinal scale with a range of twenty categorical colors:
<font color="#393b79">#393b79</font>
<font color="#5254a3">#5254a3</font>
<font color="#6b6ecf">#6b6ecf</font>
<font color="#9c9ede">#9c9ede</font>
<font color="#637939">#637939</font>
<font color="#8ca252">#8ca252</font>
<font color="#b5cf6b">#b5cf6b</font>
<font color="#cedb9c">#cedb9c</font>
<font color="#8c6d31">#8c6d31</font>
<font color="#bd9e39">#bd9e39</font>
<font color="#e7ba52">#e7ba52</font>
<font color="#e7cb94">#e7cb94</font>
<font color="#843c39">#843c39</font>
<font color="#ad494a">#ad494a</font>
<font color="#d6616b">#d6616b</font>
<font color="#e7969c">#e7969c</font>
<font color="#7b4173">#7b4173</font>
<font color="#a55194">#a55194</font>
<font color="#ce6dbd">#ce6dbd</font>
<font color="#de9ed6">#de9ed6</font>.

<a name="category20c" href="Ordinal-Scales#wiki-category20c">#</a> d3.scale.<b>category20c</b>()

Constructs a new ordinal scale with a range of twenty categorical colors:
<font color="#3182bd">#3182bd</font>
<font color="#6baed6">#6baed6</font>
<font color="#9ecae1">#9ecae1</font>
<font color="#c6dbef">#c6dbef</font>
<font color="#e6550d">#e6550d</font>
<font color="#fd8d3c">#fd8d3c</font>
<font color="#fdae6b">#fdae6b</font>
<font color="#fdd0a2">#fdd0a2</font>
<font color="#31a354">#31a354</font>
<font color="#74c476">#74c476</font>
<font color="#a1d99b">#a1d99b</font>
<font color="#c7e9c0">#c7e9c0</font>
<font color="#756bb1">#756bb1</font>
<font color="#9e9ac8">#9e9ac8</font>
<font color="#bcbddc">#bcbddc</font>
<font color="#dadaeb">#dadaeb</font>
<font color="#636363">#636363</font>
<font color="#969696">#969696</font>
<font color="#bdbdbd">#bdbdbd</font>
<font color="#d9d9d9">#d9d9d9</font>.

## ColorBrewer

D3 also bundles some fantastic categorical color scales by [[Cynthia Brewer|http://colorbrewer2.org/]]. You can find those in either CSS or JavaScript form in [lib/colorbrewer](/mbostock/d3/tree/master/lib/colorbrewer).

For CSS, assign a class such as "q0-3", "q1-3" or "q2-3" to the element you wish it be filled. Then, set the class attribute on a parent element (such as the SVG element) with the desired color scale name, such as "RdBu" or "Blues". For examples, see: [calendar heatmap](http://mbostock.github.com/d3/talk/20111116/calendar.html), [choropleth](http://mbostock.github.com/d3/talk/20111018/choropleth.html).

For JavaScript, you can use colorbrewer.RdBu[9] or equivalent as the range of a d3.scale.ordinal. For example:

```js
var z = d3.scale.ordinal()
    .domain(["foo", "bar", "baz"])
    .range(colorbrewer.RdBu[9]);
```