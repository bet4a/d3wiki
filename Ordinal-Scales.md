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

<a name="category10" href="#category10">#</a> d3.scale.<b>category10</b>()

<font color="#1f77b4">#1f77b4</font>
<font color="#ff7f0e">#ff7f0e</font>
<font color="#2ca02c">#2ca02c</font>
<font color="#d62728">#d62728</font>
<font color="#9467bd">#9467bd</font>
<font color="#8c564b">#8c564b</font>
<font color="#e377c2">#e377c2</font>
<font color="#7f7f7f">#7f7f7f</font>
<font color="#bcbd22">#bcbd22</font>
<font color="#17becf">#17becf</font>

<a name="category20" href="#category20">#</a> d3.scale.<b>category20</b>()

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
<font color="#9edae5">#9edae5</font>

<a name="category20b" href="#category20b">#</a> d3.scale.<b>category20b</b>()

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
<font color="#de9ed6">#de9ed6</font>

<a name="category20c" href="#category20c">#</a> d3.scale.<b>category20c</b>()

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
<font color="#d9d9d9">#d9d9d9</font>
