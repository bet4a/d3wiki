> [Wiki](Home) ▸ **API Reference**

Everything in D3 is scoped under the `d3` namespace. D3 uses [[semantic versioning|http://semver.org]]. You can find the current version of D3 as `d3.version`.

## [d3 (core)](Core)

### [[Selections]]

* [[d3.select|Selections#wiki-d3_select]] - select an element from the current document.(从,当前文档中,选择一个元素)
* [[d3.selectAll|Selections#wiki-d3_selectAll]] - select multiple elements from the current document.
* [[selection.attr|Selections#wiki-attr]] - get or set attribute values.
* [[selection.classed|Selections#wiki-classed]] - add or remove CSS classes.
* [[selection.style|Selections#wiki-style]] - get or set style properties.
* [[selection.property|Selections#wiki-property]] - get or set raw properties.
* [[selection.text|Selections#wiki-text]] - get or set text content.
* [[selection.html|Selections#wiki-html]] - get or set inner HTML content.
* [[selection.append|Selections#wiki-append]] - create and append new elements.
* [[selection.insert|Selections#wiki-insert]] - create and insert new elements before existing elements.
* [[selection.remove|Selections#wiki-remove]] - remove elements from the document.
* [[selection.data|Selections#wiki-data]] - get or set data for a group of elements, while computing a relational join.
* [[selection.enter|Selections#wiki-enter]] - returns placeholders for missing elements.
* [[selection.exit|Selections#wiki-exit]] - returns elements that are no longer needed.
* [[selection.datum|Selections#wiki-datum]] - get or set data for individual elements, without computing a join.
* [[selection.filter|Selections#wiki-filter]] - filter a selection based on data.
* [[selection.sort|Selections#wiki-sort]] - sort elements in the document based on data.
* [[selection.order|Selections#wiki-order]] - reorders elements in the document to match the selection.
* [[selection.on|Selections#wiki-on]] - add or remove event listeners for interaction.
* [[selection.transition|Selections#wiki-transition]] - start a transition on the selected elements.
* [[selection.each|Selections#wiki-each]] - call a function for each selected element.
* [[selection.call|Selections#wiki-call]] - call a function passing in the current selection.
* [[selection.empty|Selections#wiki-empty]] - returns true if the selection is empty.
* [[selection.node|Selections#wiki-node]] - access the first node in a selection.
* [[selection.select|Selections#wiki-select]] - subselect a descendant element for each selected element.
* [[selection.selectAll|Selections#wiki-selectAll]] - subselect multiple descendants for each selected element.
* [[d3.selection|Selections#wiki-d3_selection]] - augment the selection prototype, or test instance types.
* [[d3.event|Selections#wiki-d3_event]] - access the current user event for interaction.
* [[d3.mouse|Selections#wiki-d3_mouse]] - gets the mouse position relative to a specified container.
* [[d3.touches|Selections#wiki-d3_touches]] - gets the touch positions relative to a specified container.

### [[Transitions]]

* [[d3.transition|Transitions#wiki-d3_transition]] - start an animated transition.
* [[transition.delay|Transitions#wiki-delay]] - specify per-element delay in milliseconds.
* [[transition.duration|Transitions#wiki-duration]] - specify per-element duration in milliseconds.
* [[transition.ease|Transitions#wiki-ease]] - specify transition easing function.
* [[transition.attr|Transitions#wiki-attr]] - smoothly transition to the new attribute value.
* [[transition.attrTween|Transitions#wiki-attrTween]] - smoothly transition between two attribute values.
* [[transition.style|Transitions#wiki-style]] - smoothly transition to the new style property value.
* [[transition.styleTween|Transitions#wiki-styleTween]] - smoothly transition between two style property values.
* [[transition.text|Transitions#wiki-text]] - set the text content when the transition starts.
* [[transition.tween|Transitions#wiki-tween]] - specify a custom tween operator to run as part of the transition.
* [[transition.select|Transitions#wiki-select]] - start a transition on a descendant element for each selected element.
* [[transition.selectAll|Transitions#wiki-selectAll]] - start a transition on multiple descendants for each selected element.
* [[transition.filter|Transitions#wiki-filter]] - filter a transition based on data.
* [[transition.transition|Transitions#wiki-transition]] - when this transition ends, start another one on the same elements.
* [[transition.remove|Transitions#wiki-remove]] - remove selected elements at the end of a transition.
* [[transition.each|Transitions#wiki-each]] - add a listener for transition end events.
* [[transition.call|Transitions#wiki-call]] - call a function passing in the current transition.
* [[d3.ease|Transitions#wiki-d3_ease]] - customize transition timing.
* [[ease|Transitions#wiki-_ease]] - a parametric easing function.
* [[d3.timer|Transitions#wiki-d3_timer]] - start a custom animation timer.
* [[d3.timer.flush|Transitions#wiki-d3_timer_flush]] - immediately execute any zero-delay timers.
* [[d3.interpolate|Transitions#wiki-d3_interpolate]] - interpolate two values.
* [[interpolate|Transitions#wiki-_interpolate]] - a parametric interpolation function.
* [[d3.interpolateNumber|Transitions#wiki-d3_interpolateNumber]] - interpolate two numbers.
* [[d3.interpolateRound|Transitions#wiki-d3_interpolateRound]] - interpolate two integers.
* [[d3.interpolateString|Transitions#wiki-d3_interpolateString]] - interpolate two strings.
* [[d3.interpolateRgb|Transitions#wiki-d3_interpolateRgb]] - interpolate two RGB colors.
* [[d3.interpolateHsl|Transitions#wiki-d3_interpolateHsl]] - interpolate two HSL colors.
* [[d3.interpolateLab|Transitions#wiki-d3_interpolateLab]] - interpolate two L\*a\*b\* colors.
* [[d3.interpolateHcl|Transitions#wiki-d3_interpolateHcl]] - interpolate two HCL colors.
* [[d3.interpolateArray|Transitions#wiki-d3_interpolateArray]] - interpolate two arrays of values.
* [[d3.interpolateObject|Transitions#wiki-d3_interpolateObject]] - interpolate two arbitrary objects.
* [[d3.interpolateTransform|Transitions#wiki-d3_interpolateTransform]] - interpolate two 2D matrix transforms.
* [[d3.interpolators|Transitions#wiki-d3_interpolators]] - register a custom interpolator.

### [[Working with Arrays|Arrays]]

* [[d3.ascending|Arrays#wiki-d3_ascending]] - compare two values for sorting.
* [[d3.descending|Arrays#wiki-d3_descending]] - compare two values for sorting.
* [[d3.min|Arrays#wiki-d3_min]] - find the minimum value in an array.
* [[d3.max|Arrays#wiki-d3_max]] - find the maximum value in an array.
* [[d3.extent|Arrays#wiki-d3_extent]] - find the minimum and maximum value in an array.
* [[d3.sum|Arrays#wiki-d3_sum]] - compute the sum of an array of numbers.
* [[d3.mean|Arrays#wiki-d3_mean]] - compute the arithmetic mean of an array of numbers.
* [[d3.median|Arrays#wiki-d3_median]] - compute the median of an array of numbers (the 0.5-quantile).
* [[d3.quantile|Arrays#wiki-d3_quantile]] - compute a quantile for a sorted array of numbers.
* [[d3.bisect|Arrays#wiki-d3_bisect]] - search for a value in a sorted array.
* [[d3.bisectRight|Arrays#wiki-d3_bisectRight]] - search for a value in a sorted array.
* [[d3.bisectLeft|Arrays#wiki-d3_bisectLeft]] - search for a value in a sorted array.
* [[d3.bisector|Arrays#wiki-d3_bisector]] - bisect using an accessor.
* [d3.shuffle](Arrays#wiki-d3_shuffle) - randomize the order of an array.
* [[d3.permute|Arrays#wiki-d3_permute]] - reorder an array of elements according to an array of indexes.
* [[d3.zip|Arrays#wiki-d3_zip]] - transpose a variable number of arrays.
* [[d3.transpose|Arrays#wiki-d3_transpose]] - transpose an array of arrays.
* [[d3.keys|Arrays#wiki-d3_keys]] - list the keys of an associative array.
* [[d3.values|Arrays#wiki-d3_values]] - list the values of an associated array.
* [[d3.entries|Arrays#wiki-d3_entries]] - list the key-value entries of an associative array.
* [[d3.merge|Arrays#wiki-d3_merge]] - merge multiple arrays into one array.
* [[d3.range|Arrays#wiki-d3_range]] - generate a range of numeric values.
* [[d3.nest|Arrays#wiki-d3_nest]] - group array elements hierarchically.
* [[nest.key|Arrays#wiki-nest_key]] - add a level to the nest hierarchy.
* [[nest.sortKeys|Arrays#wiki-nest_sortKeys]] - sort the current nest level by key.
* [[nest.sortValues|Arrays#wiki-nest_sortValues]] - sort the leaf nest level by value.
* [[nest.rollup|Arrays#wiki-nest_rollup]] - specify a rollup function for leaf values.
* [[nest.map|Arrays#wiki-nest_map]] - evaluate the nest operator, returning an associative array.
* [[nest.entries|Arrays#wiki-nest_entries]] - evaluate the nest operator, returning an array of key-values tuples.
* [d3.map](Arrays#wiki-d3_map) - a shim for ES6 maps, since objects are not hashes!
* [map.has](Arrays#wiki-map_has) - returns true if the map contains the specified key.
* [map.get](Arrays#wiki-map_get) - returns the value for the specified key.
* [map.set](Arrays#wiki-map_set) - sets the value for the specified key.
* [map.remove](Arrays#wiki-map_remove) - removes the entry for specified key.
* [map.keys](Arrays#wiki-map_keys) - returns the map’s array of keys.
* [map.values](Arrays#wiki-map_values) - returns the map’s array of values.
* [map.entries](Arrays#wiki-map_entries) - returns the map’s array of entries (key-values objects).
* [map.forEach](Arrays#wiki-map_forEach) - calls the specified function for each entry in the map.

### [[Math]]

* [[d3.random.normal|Math#wiki-random_normal]] - generate a random number with a normal distribution.
* [[d3.random.logNormal|Math#wiki-random_logNormal]] - generate a random number with a log-normal distribution.
* [[d3.random.irwinHall|Math#wiki-random_irwinHall]] - generate a random number with an Irwin–Hall distribution.
* [[d3.transform|Math#wiki-transform]] - compute the standard form of a 2D matrix transform.

### [[Loading External Resources|Requests]]

* [[d3.xhr|Requests#wiki-d3_xhr]] - request a resource using XMLHttpRequest.
* [xhr.header](Requests#wiki-header) - set a request header.
* [xhr.mimeType](Requests#wiki-mimeType) - set the Accept request header and override the response MIME type.
* [xhr.response](Requests#wiki-response) - set a response mapping function.
* [xhr.get](Requests#wiki-get) - issue a GET request.
* [xhr.post](Requests#wiki-post) - issue a POST request.
* [xhr.send](Requests#wiki-send) - issue a request with the specified method and data.
* [xhr.abort](Requests#wiki-abort) - abort an outstanding request.
* [xhr.on](Requests#wiki-on) - add an event listener for "progress", "load" or "error" events.
* [[d3.text|Requests#wiki-d3_text]] - request a text file.
* [[d3.json|Requests#wiki-d3_json]] - request a JSON blob.
* [[d3.html|Requests#wiki-d3_html]] - request an HTML document fragment.
* [[d3.xml|Requests#wiki-d3_xml]] - request an XML document fragment.
* [[d3.csv|CSV]] - request a comma-separated values (CSV) file.
* [[d3.tsv|CSV#wiki-tsv]] - request a tab-separated values (TSV) file.

### [[String Formatting|Formatting]]

* [[d3.format|Formatting#wiki-d3_format]] - format a number as a string.
* [d3.formatPrefix](Formatting#wiki-d3_formatPrefix) - returns the [SI prefix] for the specified value and precision.
* [[d3.requote|Formatting#wiki-d3_requote]] - quote a string for use in a regular expression.
* [[d3.round|Formatting#wiki-d3_round]] - rounds a value to some digits after the decimal point.

### [[CSV Formatting (d3.csv)|CSV]]

* [[d3.csv|CSV#wiki-csv]] - request a comma-separated values (CSV) file.
* [[d3.csv.parse|CSV#wiki-parse]] - parse a CSV string into objects using the header row.
* [[d3.csv.parseRows|CSV#wiki-parseRows]] - parse a CSV string into tuples, ignoring the header row.
* [[d3.csv.format|CSV#wiki-format]] - format an array of tuples into a CSV string.
* [[d3.tsv|CSV#wiki-tsv]] - request a tab-separated values (TSV) file.
* [[d3.tsv.parse|CSV#wiki-tsv_parse]] - parse a TSV string into objects using the header row.
* [[d3.tsv.parseRows|CSV#wiki-tsv_parseRows]] - parse a TSV string into tuples, ignoring the header row.
* [[d3.tsv.format|CSV#wiki-tsv_format]] - format an array of tuples into a TSV string.

### [[Colors]]

* [[d3.rgb|Colors#wiki-d3_rgb]] - specify a color in RGB space.
* [[rgb.brighter|Colors#wiki-rgb_brighter]] - increase RGB channels by some exponential factor (gamma).
* [[rgb.darker|Colors#wiki-rgb_darker]] - decrease RGB channels by some exponential factor (gamma).
* [[rgb.hsl|Colors#wiki-rgb_hsl]] - convert from RGB to HSL.
* [[rgb.toString|Colors#wiki-rgb_toString]] - convert an RGB color to a string.
* [[d3.hsl|Colors#wiki-d3_hsl]] - specify a color in HSL space.
* [[hsl.brighter|Colors#wiki-hsl_brighter]] - increase lightness by some exponential factor (gamma).
* [[hsl.darker|Colors#wiki-hsl_darker]] - decrease lightness by some exponential factor (gamma).
* [[hsl.rgb|Colors#wiki-hsl_rgb]] - convert from HSL to RGB.
* [[hsl.toString|Colors#wiki-hsl_toString]] - convert an HSL color to a string.
* [[d3.lab|Colors#wiki-d3_lab]] - specify a color in L\*a\*b\* space.
* [[lab.brighter|Colors#wiki-lab_brighter]] - increase lightness by some exponential factor (gamma).
* [[lab.darker|Colors#wiki-lab_darker]] - decrease lightness by some exponential factor (gamma).
* [[lab.rgb|Colors#wiki-lab_rgb]] - convert from L\*a\*b\* to RGB.
* [[lab.toString|Colors#wiki-lab_toString]] - convert a L\*a\*b\* color to a string.
* [[d3.hcl|Colors#wiki-d3_hcl]] - specify a color in HCL space.
* [[hcl.brighter|Colors#wiki-hcl_brighter]] - increase lightness by some exponential factor (gamma).
* [[hcl.darker|Colors#wiki-hcl_darker]] - decrease lightness by some exponential factor (gamma).
* [[hcl.rgb|Colors#wiki-hcl_rgb]] - convert from HCL to RGB.
* [[hcl.toString|Colors#wiki-hcl_toString]] - convert an HCL color to a string.

### [[Namespaces]]

* [[d3.ns.prefix|Namespaces#wiki-prefix]] - access or extend known XML namespaces.
* [[d3.ns.qualify|Namespaces#wiki-qualify]] - qualify a prefixed name, such as "xlink:href".

### [[Internals]]

* [[d3.functor|Internals#wiki-functor]] - create a function that returns a constant.
* [[d3.rebind|Internals#wiki-rebind]] - rebind an inherited getter/setter method to a subclass.
* [[d3.dispatch|Internals#wiki-d3_dispatch]] - create custom event dispatchers.
* [[dispatch.on|Internals#wiki-dispatch_on]] - register an event listener.
* [[dispatch|Internals#wiki-_dispatch]] - dispatch an event to registered listeners.

## [d3.scale (Scales)](Scales)

### [[Quantitative|Quantitative-Scales#wiki-quantitative]]

* [[d3.scale.linear|Quantitative-Scales#wiki-linear]] - construct a linear quantitative scale.
* [[linear|Quantitative-Scales#wiki-_linear]] - get the range value corresponding to a given domain value.
* [[linear.invert|Quantitative-Scales#wiki-linear_invert]] - get the domain value corresponding to a given range value.
* [[linear.domain|Quantitative-Scales#wiki-linear_domain]] - get or set the scale's input domain.
* [[linear.range|Quantitative-Scales#wiki-linear_range]] - get or set the scale's output range.
* [[linear.rangeRound|Quantitative-Scales#wiki-linear_rangeRound]] - set the scale's output range, and enable rounding.
* [[linear.interpolate|Quantitative-Scales#wiki-linear_interpolate]] - get or set the scale's output interpolator.
* [[linear.clamp|Quantitative-Scales#wiki-linear_clamp]] - enable or disable clamping of the output range.
* [[linear.nice|Quantitative-Scales#wiki-linear_nice]] - extend the scale domain to nice round numbers.
* [[linear.ticks|Quantitative-Scales#wiki-linear_ticks]] - get representative values from the input domain.
* [[linear.tickFormat|Quantitative-Scales#wiki-linear_tickFormat]] - get a formatter for displaying tick values.
* [[linear.copy|Quantitative-Scales#wiki-linear_copy]] - create a new scale from an existing scale.
* [[d3.scale.sqrt|Quantitative-Scales#wiki-sqrt]] - construct a quantitative scale with a square root transform.
* [[d3.scale.pow|Quantitative-Scales#wiki-pow]] - construct a quantitative scale with an exponential transform.
* [[pow|Quantitative-Scales#wiki-_pow]] - get the range value corresponding to a given domain value.
* [[pow.invert|Quantitative-Scales#wiki-pow_invert]] - get the domain value corresponding to a given range value.
* [[pow.domain|Quantitative-Scales#wiki-pow_domain]] - get or set the scale's input domain.
* [[pow.range|Quantitative-Scales#wiki-pow_range]] - get or set the scale's output range.
* [[pow.rangeRound|Quantitative-Scales#wiki-pow_rangeRound]] - set the scale's output range, and enable rounding.
* [[pow.interpolate|Quantitative-Scales#wiki-pow_interpolate]] - get or set the scale's output interpolator.
* [[pow.clamp|Quantitative-Scales#wiki-pow_clamp]] - enable or disable clamping of the output range.
* [[pow.nice|Quantitative-Scales#wiki-pow_nice]] - extend the scale domain to nice round numbers.
* [[pow.ticks|Quantitative-Scales#wiki-pow_ticks]] - get representative values from the input domain.
* [[pow.tickFormat|Quantitative-Scales#wiki-pow_tickFormat]] - get a formatter for displaying tick values.
* [[pow.exponent|Quantitative-Scales#wiki-pow_exponent]] - get or set the exponent power.
* [[pow.copy|Quantitative-Scales#wiki-pow_copy]] - create a new scale from an existing scale.
* [[d3.scale.log|Quantitative-Scales#wiki-log]] - construct a quantitative scale with an logarithmic transform.
* [[log|Quantitative-Scales#wiki-_log]] - get the range value corresponding to a given domain value.
* [[log.invert|Quantitative-Scales#wiki-log_invert]] - get the domain value corresponding to a given range value.
* [[log.domain|Quantitative-Scales#wiki-log_domain]] - get or set the scale's input domain.
* [[log.range|Quantitative-Scales#wiki-log_range]] - get or set the scale's output range.
* [[log.rangeRound|Quantitative-Scales#wiki-log_rangeRound]] - set the scale's output range, and enable rounding.
* [[log.interpolate|Quantitative-Scales#wiki-log_interpolate]] - get or set the scale's output interpolator.
* [[log.clamp|Quantitative-Scales#wiki-log_clamp]] - enable or disable clamping of the output range.
* [[log.nice|Quantitative-Scales#wiki-log_nice]] - extend the scale domain to nice powers of ten.
* [[log.ticks|Quantitative-Scales#wiki-log_ticks]] - get representative values from the input domain.
* [[log.tickFormat|Quantitative-Scales#wiki-log_tickFormat]] - get a formatter for displaying tick values.
* [[log.copy|Quantitative-Scales#wiki-log_copy]] - create a new scale from an existing scale.
* [[d3.scale.quantize|Quantitative-Scales#wiki-quantize]] - construct a linear quantitative scale with a discrete output range.
* [[quantize|Quantitative-Scales#wiki-_quantize]] - get the range value corresponding to a given domain value.
* [[quantize.domain|Quantitative-Scales#wiki-quantize_domain]] - get or set the scale's input domain.
* [[quantize.range|Quantitative-Scales#wiki-quantize_range]] - get or set the scale's output range (as discrete values).
* [[quantize.copy|Quantitative-Scales#wiki-quantize_copy]] - create a new scale from an existing scale.
* [[d3.scale.threshold|Quantitative-Scales#wiki-threshold]] - construct a threshold scale with a discrete output range.
* [[threshold|Quantitative-Scales#wiki-_threshold]] - get the range value corresponding to a given domain value.
* [[threshold.domain|Quantitative-Scales#wiki-threshold_domain]] - get or set the scale's input domain.
* [[threshold.range|Quantitative-Scales#wiki-threshold_range]] - get or set the scale's output range (as discrete values).
* [[threshold.copy|Quantitative-Scales#wiki-threshold_copy]] - create a new scale from an existing scale.
* [[d3.scale.quantile|Quantitative-Scales#wiki-quantile]] - construct a quantitative scale mapping to quantiles.
* [[quantile|Quantitative-Scales#wiki-_quantile]] - get the range value corresponding to a given domain value.
* [[quantile.domain|Quantitative-Scales#wiki-quantile_domain]] - get or set the scale's input domain (as discrete values).
* [[quantile.range|Quantitative-Scales#wiki-quantile_range]] - get or set the scale's output range (as discrete values).
* [[quantile.quantiles|Quantitative-Scales#wiki-quantile_quantiles]] - get the scale's quantile bin thresholds.
* [[quantile.copy|Quantitative-Scales#wiki-quantile_copy]] - create a new scale from an existing scale.
* [[d3.scale.identity|Quantitative-Scales#wiki-identity]] - construct a linear identity scale.
* [[identity|Quantitative-Scales#wiki-_identity]] - the identity function.
* [[identity.invert|Quantitative-Scales#wiki-_identity]] - equivalent to identity; the identity function.
* [[identity.domain|Quantitative-Scales#wiki-identity_domain]] - get or set the scale's domain and range.
* [[identity.range|Quantitative-Scales#wiki-identity_domain]] - equivalent to identity.domain.
* [[identity.ticks|Quantitative-Scales#wiki-identity_ticks]] - get representative values from the domain.
* [[identity.tickFormat|Quantitative-Scales#wiki-identity_tickFormat]] - get a formatter for displaying tick values.
* [[identity.copy|Quantitative-Scales#wiki-identity_copy]] - create a new scale from an existing scale.

### [[Ordinal|Ordinal-Scales#wiki-ordinal]]

* [[d3.scale.ordinal|Ordinal-Scales#wiki-ordinal]] - construct an ordinal scale.
* [[ordinal|Ordinal-Scales#wiki-_ordinal]] - get the range value corresponding to a given domain value.
* [[ordinal.domain|Ordinal-Scales#wiki-ordinal_domain]] - get or set the scale's input domain.
* [[ordinal.range|Ordinal-Scales#wiki-ordinal_range]] - get or set the scale's output range.
* [[ordinal.rangePoints|Ordinal-Scales#wiki-ordinal_rangePoints]] - divide a continuous output range for discrete points.
* [[ordinal.rangeBands|Ordinal-Scales#wiki-ordinal_rangeBands]] - divide a continuous output range for discrete bands.
* [[ordinal.rangeRoundBands|Ordinal-Scales#wiki-ordinal_rangeRoundBands]] - divide a continuous output range for discrete bands.
* [[ordinal.rangeBand|Ordinal-Scales#wiki-ordinal_rangeBand]] - get the discrete range band width.
* [[ordinal.rangeExtent|Ordinal-Scales#wiki-ordinal_rangeExtent]] - get the minimum and maximum values of the output range.
* [[ordinal.copy|Ordinal-Scales#wiki-ordinal_copy]] - create a new scale from an existing scale.
* [[d3.scale.category10|Ordinal-Scales#wiki-category10]] - construct an ordinal scale with ten categorical colors.
* [[d3.scale.category20|Ordinal-Scales#wiki-category20]] - construct an ordinal scale with twenty categorical colors.
* [[d3.scale.category20b|Ordinal-Scales#wiki-category20b]] - construct an ordinal scale with twenty categorical colors.
* [[d3.scale.category20c|Ordinal-Scales#wiki-category20c]] - construct an ordinal scale with twenty categorical colors.

## [d3.svg (SVG)](SVG)

### [[Shapes|SVG-Shapes]]

* [[d3.svg.line|SVG-Shapes#wiki-line]] - create a new line generator.
* [[line|SVG-Shapes#wiki-_line]] - generate a piecewise linear curve, as in a line chart.
* [[line.x|SVG-Shapes#wiki-line_x]] - get or set the *x*-coordinate accessor.
* [[line.y|SVG-Shapes#wiki-line_y]] - get or set the *y*-coordinate accessor.
* [[line.interpolate|SVG-Shapes#wiki-line_interpolate]] - get or set the interpolation mode.
* [[line.tension|SVG-Shapes#wiki-line_tension]] - get or set the cardinal spline tension.
* [line.defined](SVG-Shapes#wiki-line_defined) - control whether the line is defined at a given point.
* [[d3.svg.line.radial|SVG-Shapes#wiki-line_radial]] - create a new radial line generator.
* [[line|SVG-Shapes#wiki-_line_radial]] - generate a piecewise linear curve, as in a polar line chart.
* [[line.radius|SVG-Shapes#wiki-line_radial_radius]] - get or set the *radius* accessor.
* [[line.angle|SVG-Shapes#wiki-line_radial_angle]] - get or set the *angle* accessor.
* [line.defined](SVG-Shapes#wiki-line_radial_defined) - control whether the line is defined at a given point.
* [[d3.svg.area|SVG-Shapes#wiki-area]] - create a new area generator.
* [[area|SVG-Shapes#wiki-_area]] - generate a piecewise linear area, as in an area chart.
* [[area.x|SVG-Shapes#wiki-area_x]] - get or set the *x*-coordinate accessors.
* [[area.x0|SVG-Shapes#wiki-area_x0]] - get or set the *x0*-coordinate (baseline) accessor.
* [[area.x1|SVG-Shapes#wiki-area_x1]] - get or set the *x1*-coordinate (topline) accessor.
* [[area.y|SVG-Shapes#wiki-area_y]] - get or set the *y*-coordinate accessors.
* [[area.y0|SVG-Shapes#wiki-area_y0]] - get or set the *y0*-coordinate (baseline) accessor.
* [[area.y1|SVG-Shapes#wiki-area_y1]] - get or set the *y1*-coordinate (topline) accessor.
* [[area.interpolate|SVG-Shapes#wiki-area_interpolate]] - get or set the interpolation mode.
* [[area.tension|SVG-Shapes#wiki-area_tension]] - get or set the cardinal spline tension.
* [area.defined](SVG-Shapes#wiki-area_defined) - control whether the area is defined at a given point.
* [[d3.svg.area.radial|SVG-Shapes#wiki-area_radial]] - create a new area generator.
* [[area|SVG-Shapes#wiki-_area_radial]] - generate a piecewise linear area, as in a polar area chart.
* [[area.radius|SVG-Shapes#wiki-area_radial_radius]] - get or set the *radius* accessors.
* [[area.innerRadius|SVG-Shapes#wiki-area_radial_innerRadius]] - get or set the inner *radius* (baseline) accessor.
* [[area.outerRadius|SVG-Shapes#wiki-area_radial_outerRadius]] - get or set the outer *radius* (topline) accessor.
* [[area.angle|SVG-Shapes#wiki-area_radial_angle]] - get or set the *angle* accessors.
* [[area.startAngle|SVG-Shapes#wiki-area_radial_startAngle]] - get or set the *angle* (baseline) accessor.
* [[area.endAngle|SVG-Shapes#wiki-area_radial_endAngle]] - get or set the *angle* (topline) accessor.
* [area.defined](SVG-Shapes#wiki-area_radial_defined) - control whether the area is defined at a given point.
* [[d3.svg.arc|SVG-Shapes#wiki-arc]] - create a new arc generator.
* [[arc|SVG-Shapes#wiki-_arc]] - generate a solid arc, as in a pie or donut chart.
* [[arc.innerRadius|SVG-Shapes#wiki-arc_innerRadius]] - get or set the inner radius accessor.
* [[arc.outerRadius|SVG-Shapes#wiki-arc_outerRadius]] - get or set the outer radius accessor.
* [[arc.startAngle|SVG-Shapes#wiki-arc_startAngle]] - get or set the start angle accessor.
* [[arc.endAngle|SVG-Shapes#wiki-arc_endAngle]] - get or set the end angle accessor.
* [[arc.centroid|SVG-Shapes#wiki-arc_centroid]] - compute the arc centroid.
* [[d3.svg.symbol|SVG-Shapes#wiki-symbol]] - create a new symbol generator.
* [[symbol|SVG-Shapes#wiki-_symbol]] - generate categorical symbols, as in a scatterplot.
* [[symbol.type|SVG-Shapes#wiki-symbol_type]] - get or set the symbol type accessor.
* [[symbol.size|SVG-Shapes#wiki-symbol_size]] - get or set the symbol size (in square pixels) accessor.
* [d3.svg.symbolTypes](SVG-Shapes#wiki-symbolTypes) - the array of supported symbol types.
* [[d3.svg.chord|SVG-Shapes#wiki-chord]] - create a new chord generator.
* [[chord|SVG-Shapes#wiki-_chord]] - generate a quadratic Bézier connecting two arcs, as in a chord diagram.
* [[chord.radius|SVG-Shapes#wiki-chord_radius]] - get or set the arc radius accessor.
* [[chord.startAngle|SVG-Shapes#wiki-chord_startAngle]] - get or set the arc start angle accessor.
* [[chord.endAngle|SVG-Shapes#wiki-chord_endAngle]] - get or set the arc end angle accessor.
* [[chord.source|SVG-Shapes#wiki-chord_source]] - get or set the source arc accessor.
* [[chord.target|SVG-Shapes#wiki-chord_target]] - get or set the target arc accessor.
* [[d3.svg.diagonal|SVG-Shapes#wiki-diagonal]] - create a new diagonal generator.
* [[diagonal|SVG-Shapes#wiki-_diagonal]] - generate a two-dimensional Bézier connector, as in a node-link diagram.
* [[diagonal.source|SVG-Shapes#wiki-diagonal_source]] - get or set the source point accessor.
* [[diagonal.target|SVG-Shapes#wiki-diagonal_target]] - get or set the target point accessor.
* [[diagonal.projection|SVG-Shapes#wiki-diagonal_projection]] - get or set an optional point transform.
* [[d3.svg.diagonal.radial|SVG-Shapes#wiki-diagonal_radial]] - create a new diagonal generator.
* [[diagonal|SVG-Shapes#wiki-_diagonal_radial]] - generate a two-dimensional Bézier connector, as in a node-link diagram.

### [[Axes|SVG-Axes]]

* [[d3.svg.axis|SVG-Axes#wiki-axis]] - create a new axis generator.
* [[axis|SVG-Axes#wiki-_axis]] - creates or updates an axis for the given selection or transition.
* [[axis.scale|SVG-Axes#wiki-scale]] - get or set the axis scale.
* [[axis.orient|SVG-Axes#wiki-orient]] - get or set the axis orientation.
* [[axis.ticks|SVG-Axes#wiki-ticks]] - control how ticks are generated for the axis.
* [[axis.tickValues|SVG-Axes#wiki-tickValues]] - specify tick values explicitly.
* [[axis.tickSubdivide|SVG-Axes#wiki-tickSubdivide]] - optionally subdivide ticks uniformly.
* [[axis.tickSize|SVG-Axes#wiki-tickSize]] - specify the size of major, minor and end ticks.
* [[axis.tickPadding|SVG-Axes#wiki-tickPadding]] - specify padding between ticks and tick labels.
* [[axis.tickFormat|SVG-Axes#wiki-tickFormat]] - override the tick formatting for labels.

### [[Controls|SVG-Controls]]

* [[d3.svg.brush|SVG-Controls#wiki-brush]] - click and drag to select one- or two-dimensional regions.
* [[brush|SVG-Controls#wiki-_brush]] - creates or updates a brush for the given selection or transition.
* [[brush.x|SVG-Controls#wiki-brush_x]] - get or set the brush’s x-scale.
* [[brush.y|SVG-Controls#wiki-brush_y]] - get or set the brush’s y-scale.
* [[brush.extent|SVG-Controls#wiki-brush_extent]] - get or set the brush’s extent.
* [[brush.clear|SVG-Controls#wiki-brush_clear]] - reset the brush extent.
* [[brush.empty|SVG-Controls#wiki-brush_empty]] - returns true if the brush extent is empty.
* [[brush.on|SVG-Controls#wiki-brush_on]] - respond to events when the brush is moved.

## [d3.time (Time)](Time)

### [[Time Formatting]]

* [[d3.time.format|Time-Formatting#wiki-format]] - create a new local time formatter for a given specifier.
* [[format|Time-Formatting#wiki-_format]] - format a date into a string.
* [[format.parse|Time-Formatting#wiki-parse]] - parse a string into a date.
* [[d3.time.format.utc|Time-Formatting#wiki-format_utc]] - create a new UTC time formatter for a given specifier.
* [[d3.time.format.iso|Time-Formatting#wiki-format_iso]] - the ISO 8601 UTC time formatter.

### [[Time Scales]]

* [[d3.time.scale|Time-Scales#wiki-scale]] - construct a linear time scale.
* [[scale|Time-Scales#wiki-_scale]] - get the range value corresponding to a given domain value.
* [[scale.invert|Time-Scales#wiki-invert]] - get the domain value corresponding to a given range value.
* [[scale.domain|Time-Scales#wiki-domain]] - get or set the scale's input domain.
* [[scale.range|Time-Scales#wiki-range]] - get or set the scale's output range.
* [[scale.rangeRound|Time-Scales#wiki-rangeRound]] - set the scale's output range, and enable rounding.
* [[scale.interpolate|Time-Scales#wiki-interpolate]] - get or set the scale's output interpolator.
* [[scale.clamp|Time-Scales#wiki-clamp]] - enable or disable clamping of the output range.
* [[scale.ticks|Time-Scales#wiki-ticks]] - get representative values from the input domain.
* [[scale.tickFormat|Time-Scales#wiki-tickFormat]] - get a formatter for displaying tick values.
* [[scale.copy|Time-Scales#wiki-copy]] - create a new scale from an existing scale.

### [[Time Intervals]]

* [[d3.time.interval|Time-Intervals#wiki-interval]] - a time interval in local time.
* [[interval|Time-Intervals#wiki-_interval]] - alias for interval.floor.
* [[interval.range|Time-Intervals#wiki-interval_range]] - returns dates within the specified range.
* [[interval.floor|Time-Intervals#wiki-interval_floor]] - rounds down to the nearest interval.
* [[interval.round|Time-Intervals#wiki-interval_round]] - rounds up or down to the nearest interval.
* [[interval.ceil|Time-Intervals#wiki-interval_ceil]] - rounds up to the nearest interval.
* [[interval.offset|Time-Intervals#wiki-interval_offset]] - returns a date offset by some interval.
* [[interval.utc|Time-Intervals#wiki-interval_utc]] - returns the UTC-equivalent time interval.
* [[d3.time.day|Time-Intervals#wiki-day]] - every day (12:00 AM).
* [[d3.time.days|Time-Intervals#wiki-day]] - alias for day.range.
* [d3.time.dayOfYear](Time-Intervals#wiki-dayOfYear) - computes the day number.
* [[d3.time.hour|Time-Intervals#wiki-hour]] - every hour (e.g., 1:00 AM).
* [[d3.time.hours|Time-Intervals#wiki-hours]] - alias for hour.range.
* [[d3.time.minute|Time-Intervals#wiki-minute]] - every minute (e.g., 1:02 AM).
* [[d3.time.minutes|Time-Intervals#wiki-minutes]] - alias for minute.range.
* [[d3.time.month|Time-Intervals#wiki-month]] - every month (e.g., February 1, 12:00 AM).
* [[d3.time.months|Time-Intervals#wiki-months]] - alias for month.range.
* [[d3.time.second|Time-Intervals#wiki-second]] - every second (e.g., 1:02:03 AM).
* [[d3.time.seconds|Time-Intervals#wiki-seconds]] - alias for second.range.
* [[d3.time.sunday|Time-Intervals#wiki-sunday]] - every Sunday (e.g., February 5, 12:00 AM).
* [[d3.time.sundays|Time-Intervals#wiki-sundays]] - alias for sunday.range.
* [d3.time.sundayOfYear](Time-Intervals#wiki-sundayOfYear) - computes the sunday-based week number.
* [[d3.time.monday|Time-Intervals#wiki-monday]] - every Monday (e.g., February 5, 12:00 AM).
* [[d3.time.mondays|Time-Intervals#wiki-mondays]] - alias for monday.range.
* [d3.time.mondayOfYear](Time-Intervals#wiki-mondayOfYear) - computes the monday-based week number.
* [[d3.time.tuesday|Time-Intervals#wiki-tuesday]] - every Tuesday (e.g., February 5, 12:00 AM).
* [[d3.time.tuesdays|Time-Intervals#wiki-tuesdays]] - alias for tuesday.range.
* [d3.time.tuesdayOfYear](Time-Intervals#wiki-tuesdayOfYear) - computes the tuesday-based week number.
* [[d3.time.wednesday|Time-Intervals#wiki-wednesday]] - every Wednesday (e.g., February 5, 12:00 AM).
* [[d3.time.wednesdays|Time-Intervals#wiki-wednesdays]] - alias for wednesday.range.
* [d3.time.wednesdayOfYear](Time-Intervals#wiki-tuesdayOfYear) - computes the wednesday-based week number.
* [[d3.time.thursday|Time-Intervals#wiki-thursday]] - every Thursday (e.g., February 5, 12:00 AM).
* [[d3.time.thursdays|Time-Intervals#wiki-thursdays]] - alias for thursday.range.
* [d3.time.thursdayOfYear](Time-Intervals#wiki-thursdayOfYear) - computes the thursday-based week number.
* [[d3.time.friday|Time-Intervals#wiki-friday]] - every Friday (e.g., February 5, 12:00 AM).
* [[d3.time.fridays|Time-Intervals#wiki-fridays]] - alias for friday.range.
* [d3.time.fridayOfYear](Time-Intervals#wiki-fridayOfYear) - computes the friday-based week number.
* [[d3.time.saturday|Time-Intervals#wiki-saturday]] - every Saturday (e.g., February 5, 12:00 AM).
* [[d3.time.saturdays|Time-Intervals#wiki-saturdays]] - alias for saturday.range.
* [d3.time.saturdayOfYear](Time-Intervals#wiki-saturdayOfYear) - computes the saturday-based week number.
* [[d3.time.week|Time-Intervals#wiki-week]] - alias for sunday.
* [[d3.time.weeks|Time-Intervals#wiki-weeks]] - alias for sunday.range.
* [d3.time.weekOfYear](Time-Intervals#wiki-weekOfYear) - alias for sundayOfYear.
* [[d3.time.year|Time-Intervals#wiki-year]] - every year (e.g., January 1, 12:00 AM).
* [[d3.time.years|Time-Intervals#wiki-years]] - alias for year.range.

## [d3.layout (Layouts)](Layouts)

### [[Bundle|Bundle-Layout]]

* [[d3.layout.bundle|Bundle-Layout#wiki-bundle]] - construct a new default bundle layout.
* [[bundle|Bundle-Layout#wiki-_bundle]] - apply Holten's *hierarchical bundling* algorithm to edges.

### [[Chord|Chord-Layout]]

* [[d3.layout.chord|Chord-Layout#wiki-chord]] - produce a chord diagram from a matrix of relationships.
* [[chord.matrix|Chord-Layout#wiki-matrix]] - get or set the matrix data backing the layout.
* [[chord.padding|Chord-Layout#wiki-padding]] - get or set the angular padding between chord segments.
* [[chord.sortGroups|Chord-Layout#wiki-sortGroups]] - get or set the comparator function for groups.
* [[chord.sortSubgroups|Chord-Layout#wiki-sortSubgroups]] - get or set the comparator function for subgroups.
* [[chord.sortChords|Chord-Layout#wiki-sortChords]] - get or set the comparator function for chords (z-order).
* [[chord.chords|Chord-Layout#wiki-chords]] - retrieve the computed chord angles.
* [[chord.groups|Chord-Layout#wiki-groups]] - retrieve the computed group angles.

### [[Cluster|Cluster-Layout]]

* [[d3.layout.cluster|Cluster-Layout#wiki-cluster]] - cluster entities into a dendrogram.
* [[cluster.sort|Cluster-Layout#wiki-sort]] - get or set the comparator function for sibling nodes.
* [[cluster.children|Cluster-Layout#wiki-children]] - get or set the accessor function for child nodes.
* [[cluster.nodes|Cluster-Layout#wiki-nodes]] - compute the cluster layout and return the array of nodes.
* [[cluster.links|Cluster-Layout#wiki-links]] - compute the parent-child links between tree nodes.
* [[cluster.separation|Cluster-Layout#wiki-separation]] - get or set the spacing function between neighboring nodes.
* [[cluster.size|Cluster-Layout#wiki-size]] - get or set the layout size in *x* and *y*.

### [[Force|Force-Layout]]

* [[d3.layout.force|Force-Layout#wiki-force]] - position linked nodes using physical simulation.
* [[force.on|Force-Layout#wiki-on]] - listen to updates in the computed layout positions.
* [[force.nodes|Force-Layout#wiki-nodes]] - get or set the array of nodes to layout.
* [[force.links|Force-Layout#wiki-links]] - get or set the array of links between nodes.
* [[force.size|Force-Layout#wiki-size]] - get or set the layout size in *x* and *y*.
* [[force.linkDistance|Force-Layout#wiki-linkDistance]] - get or set the link distance.
* [[force.linkStrength|Force-Layout#wiki-linkStrength]] - get or set the link strength.
* [[force.friction|Force-Layout#wiki-friction]] - get or set the friction coefficient.
* [[force.charge|Force-Layout#wiki-charge]] - get or set the charge strength.
* [[force.gravity|Force-Layout#wiki-gravity]] - get or set the gravity strength.
* [[force.theta|Force-Layout#wiki-theta]] - get or set the accuracy of the charge interaction.
* [[force.start|Force-Layout#wiki-start]] - start or restart the simulation when the nodes change.
* [[force.resume|Force-Layout#wiki-resume]] - reheat the cooling parameter and restart simulation.
* [[force.stop|Force-Layout#wiki-stop]] - immediately terminate the simulation.
* [[force.alpha|Force-Layout#wiki-alpha]] - get or set the layout's cooling parameter.
* [[force.tick|Force-Layout#wiki-tick]] - run the layout simulation one step.
* [[force.drag|Force-Layout#wiki-drag]] - bind a behavior to nodes to allow interactive dragging.

### [[Hierarchy|Hierarchy-Layout]]

* [[d3.layout.hierarchy|Hierarchy-Layout#wiki-hierarchy]] - derive a custom hierarchical layout implementation.
* [[hierarchy.sort|Hierarchy-Layout#wiki-sort]] - get or set the comparator function for sibling nodes.
* [[hierarchy.children|Hierarchy-Layout#wiki-children]] - get or set the accessor function for child nodes.
* [[hierarchy.nodes|Hierarchy-Layout#wiki-nodes]] - compute the layout and return the array of nodes.
* [[hierarchy.links|Hierarchy-Layout#wiki-links]] - compute the parent-child links between tree nodes.
* [[hierarchy.value|Hierarchy-Layout#wiki-value]] - get or set the value accessor function.
* [[hierarchy.revalue|Hierarchy-Layout#wiki-revalue]] - recompute the hierarchy values.

### [[Histogram|Histogram-Layout]]

* [[d3.layout.histogram|Histogram-Layout#wiki-histogram]] - construct a new default histogram layout.
* [[histogram|Histogram-Layout#wiki-_histogram]] - compute the distribution of data using quantized bins.
* [[histogram.value|Histogram-Layout#wiki-value]] - get or set the value accessor function.
* [[histogram.range|Histogram-Layout#wiki-range]] - get or set the considered value range.
* [[histogram.bins|Histogram-Layout#wiki-bins]] - specify how values are organized into bins.
* [[histogram.frequency|Histogram-Layout#wiki-frequency]] - compute the distribution as counts or probabilities.

### [[Pack|Pack-Layout]]

* [[d3.layout.pack|Pack-Layout#wiki-pack]] - produce a hierarchical layout using recursive circle-packing.
* [[pack.sort|Pack-Layout#wiki-sort]] - control the order in which sibling nodes are traversed.
* [[pack.children|Pack-Layout#wiki-children]] - get or set the children accessor function.
* [[pack.nodes|Pack-Layout#wiki-nodes]] - compute the pack layout and return the array of nodes.
* [[pack.links|Pack-Layout#wiki-links]] - compute the parent-child links between tree nodes.
* [[pack.value|Pack-Layout#wiki-value]] - get or set the value accessor used to size circles.
* [[pack.size|Pack-Layout#wiki-size]] - specify the layout size in *x* and *y*.
* [[pack.padding|Pack-Layout#wiki-padding]] - specify the layout padding in (approximate) pixels.

### [[Partition|Partition-Layout]]

* [[d3.layout.partition|Partition-Layout#wiki-partition]] - recursively partition a node tree into a sunburst or icicle.
* [[partition.sort|Partition-Layout#wiki-sort]] - control the order in which sibling nodes are traversed.
* [[partition.children|Partition-Layout#wiki-children]] - get or set the children accessor function.
* [[partition.nodes|Partition-Layout#wiki-nodes]] - compute the partition layout and return the array of nodes.
* [[partition.links|Partition-Layout#wiki-links]] - compute the parent-child links between tree nodes.
* [[partition.value|Partition-Layout#wiki-value]] - get or set the value accessor used to size circles.
* [[partition.size|Partition-Layout#wiki-size]] - specify the layout size in *x* and *y*.

### [[Pie|Pie-Layout]]

* [[d3.layout.pie|Pie-Layout#wiki-pie]] - construct a new default pie layout.
* [[pie|Pie-Layout#wiki-_pie]] - compute the start and end angles for arcs in a pie or donut chart.
* [[pie.value|Pie-Layout#wiki-value]] - get or set the value accessor function.
* [[pie.sort|Pie-Layout#wiki-sort]] - control the clockwise order of pie slices.
* [[pie.startAngle|Pie-Layout#wiki-startAngle]] - get or set the overall start angle of the pie.
* [[pie.endAngle|Pie-Layout#wiki-endAngle]] - get or set the overall end angle of the pie.

### [[Stack|Stack-Layout]]

* [[d3.layout.stack|Stack-Layout#wiki-stack]] - construct a new default stack layout.
* [[stack|Stack-Layout#wiki-_stack]] - compute the baseline for each series in a stacked bar or area chart.
* [[stack.values|Stack-Layout#wiki-values]] - get or set the values accessor function per series.
* [[stack.order|Stack-Layout#wiki-order]] - control the order in which series are stacked.
* [[stack.offset|Stack-Layout#wiki-offset]] - specify the overall baseline algorithm.
* [[stack.x|Stack-Layout#wiki-x]] - get or set the *x*-dimension accessor function.
* [[stack.y|Stack-Layout#wiki-y]] - get or set the *y*-dimension accessor function.
* [[stack.out|Stack-Layout#wiki-out]] - get or set the output function for storing the baseline.

### [[Tree|Tree-Layout]]

* [[d3.layout.tree|Tree-Layout#wiki-tree]] - position a tree of nodes tidily.
* [[tree.sort|Tree-Layout#wiki-sort]] - control the order in which sibling nodes are traversed.
* [[tree.children|Tree-Layout#wiki-children]] - get or set the children accessor function.
* [[tree.nodes|Tree-Layout#wiki-nodes]] - compute the tree layout and return the array of nodes.
* [[tree.links|Tree-Layout#wiki-links]] - compute the parent-child links between tree nodes.
* [[tree.separation|Tree-Layout#wiki-separation]] - get or set the spacing function between neighboring nodes.
* [[tree.size|Tree-Layout#wiki-size]] - specify the layout size in *x* and *y*.

### [[Treemap|Treemap-Layout]]

* [[d3.layout.treemap|Treemap-Layout#wiki-treemap]] - use recursive spatial subdivision to display a tree of nodes.
* [[treemap.sort|Treemap-Layout#wiki-sort]] - control the order in which sibling nodes are traversed.
* [[treemap.children|Treemap-Layout#wiki-children]] - get or set the children accessor function.
* [[treemap.nodes|Treemap-Layout#wiki-nodes]] - compute the treemap layout and return the array of nodes.
* [[treemap.links|Treemap-Layout#wiki-links]] - compute the parent-child links between tree nodes.
* [[treemap.value|Treemap-Layout#wiki-value]] - get or set the value accessor used to size treemap cells.
* [[treemap.size|Treemap-Layout#wiki-size]] - specify the layout size in *x* and *y*.
* [[treemap.padding|Treemap-Layout#wiki-padding]] - specify the padding between a parent and its children.
* [[treemap.round|Treemap-Layout#wiki-round]] - enable or disable rounding to exact pixels.
* [[treemap.sticky|Treemap-Layout#wiki-sticky]] - make the layout sticky for stable updates.
* [treemap.mode](Treemap-Layout#wiki-mode) - change the treemap layout algorithm.

## [d3.geo (Geography)](Geo)

### [Paths](Geo-Paths)

* [d3.geo.path](Geo-Paths#wiki-path) - create a new geographic path generator.
* [path](Geo-Paths#wiki-_path) - project the specified feature and render it to the context.
* [path.projection](Geo-Paths#wiki-projection) - get or set the geographic projection.
* [path.context](Geo-Paths#wiki-context) - get or set the render context.
* [path.pointRadius](Geo-Paths#wiki-pointRadius) - get or set the radius to display point features.
* [path.area](Geo-Paths#wiki-area) - compute the projected area of a given feature.
* [path.centroid](Geo-Paths#wiki-centroid) - compute the projected centroid of a given feature.
* [path.bounds](Geo-Paths#wiki-bounds) - compute the projected bounds of a given feature.
* [d3.geo.greatArc](Geo-Paths#wiki-greatArc) - create a great arc path generator.
* [greatArc](Geo-Paths#wiki-_greatArc) - generate a piecewise great arc between two points as a LineString.
* [greatArc.distance](Geo-Paths#wiki-greatArc_distance) - computes the length of a great arc in radians.
* [greatArc.source](Geo-Paths#wiki-greatArc_source) - specify a source accessor.
* [greatArc.target](Geo-Paths#wiki-greatArc_target) - specify a target accessor.
* [greatArc.precision](Geo-Paths#wiki-greatArc_precision) - specify the precision of the piecewise arc.
* [d3.geo.circle](Geo-Paths#wiki-circle) - create a circle generator.
* [circle](Geo-Paths#wiki-_circle) - generate a piecewise circle as a Polygon. 
* [circle.origin](Geo-Paths#wiki-circle_origin) - specify the origin in latitude and longitude.
* [circle.angle](Geo-Paths#wiki-circle_angle) - specify the angular radius in degrees.
* [circle.precision](Geo-Paths#wiki-circle_precision) - specify the precision of the piecewise circle.
* [d3.geo.area](Geo-Paths#wiki-d3_geo_area) - compute the spherical area of a given feature.
* [d3.geo.centroid](Geo-Paths#wiki-d3_geo_centroid) - compute the spherical centroid of a given feature.
* [d3.geo.bounds](Geo-Paths#wiki-d3_geo_bounds) - compute the latitude-longitude bounding box for a given feature.
* [d3.geo.interpolate](Geo-Paths#wiki-d3_geo_interpolate) - interpolate between two points along a great arc.

### [[Projections|Geo-Projections]]

* [d3.geo.projection](Geo-Projections#wiki-projection) - create a standard projection from a raw projection.
* [projection](Geo-Projections#wiki-_projection) - project the specified location.
* [projection.invert](Geo-Projections#wiki-invert) - invert the projection for the specified point.
* [projection.rotate](Geo-Projections#wiki-rotate) - get or set the projection’s three-axis rotation.
* [projection.center](Geo-Projections#wiki-center) - get or set the projection’s center location.
* [projection.translate](Geo-Projections#wiki-translate) - get or set the projection’s translation position.
* [projection.scale](Geo-Projections#wiki-scale) - get or set the projection’s scale factor.
* [projection.clipAngle](Geo-Projections#wiki-clipAngle) - get or set the radius of the projection’s clip circle.
* [projection.precision](Geo-Projections#wiki-precision) - get or set the precision threshold for adaptive resampling.
* [projection.stream](Geo-Projections#wiki-stream) - wrap the specified stream listener, projecting input geometry.
* [d3.geo.projectionMutator](Geo-Projections#wiki-projectionMutator) - create a standard projection from a mutable raw projection.
* [d3.geo.albers](Geo-Projections#wiki-albers) - the Albers equal-area conic projection.
* [albers.parallels](Geo-Projections#wiki-albers_parallels) - get or set the projection's two standard parallels.
* [d3.geo.albersUsa](Geo-Projections#wiki-albersUsa) - a composite Albers projection for the United States.
* [d3.geo.azimuthalEqualArea](Geo-Projections#wiki-azimuthalEqualArea) - the azimuthal equal-area projection.
* [d3.geo.azimuthalEquidistant](Geo-Projections#wiki-azimuthalEquidistant) - the azimuthal equidistant projection.
* [d3.geo.equirectangular](Geo-Projections#wiki-equirectangular) - the equirectangular (plate carreé) projection.
* [d3.geo.gnomonic](Geo-Projections#wiki-gnomonic) - the gnomonic projection.
* [d3.geo.mercator](Geo-Projections#wiki-mercator) - the spherical Mercator projection.
* [d3.geo.orthographic](Geo-Projections#wiki-orthographic) - the azimuthal orthographic projection.
* [d3.geo.stereographic](Geo-Projections#wiki-stereographic) - the azimuthal stereographic projection.
* [d3.geo.albers.raw](Geo-Projections#wiki-albers_raw) - the raw Albers equal-area conic projection.
* [d3.geo.azimuthalEqualArea.raw](Geo-Projections#wiki-azimuthalEqualArea_raw) - the raw azimuthal equal-area projection.
* [d3.geo.azimuthalEquidistant.raw](Geo-Projections#wiki-azimuthalEquidistant_raw) - the azimuthal equidistant projection.
* [d3.geo.equirectangular.raw](Geo-Projections#wiki-equirectangular_raw) - the raw equirectangular (plate carrée) projection.
* [d3.geo.gnomonic.raw](Geo-Projections#wiki-gnomonic_raw) - the raw gnomonic projection.
* [d3.geo.mercator.raw](Geo-Projections#wiki-mercator_raw) - the raw Mercator projection.
* [d3.geo.orthographic.raw](Geo-Projections#wiki-orthographic_raw) - the raw azimuthal orthographic projection.
* [d3.geo.stereographic.raw](Geo-Projections#wiki-stereographic_raw) - the raw azimuthal stereographic projection.

### [Streams](Geo-Streams)

* [d3.geo.stream](Geo-Streams#d3_geo_stream) - convert a GeoJSON object to a geometry stream.
* [stream.point](Geo-Streams#point) - indicate an *x*, *y* (and optionally *z*) coordinate.
* [stream.lineStart](Geo-Streams#lineStart) - indicate the start of a line or ring.
* [stream.lineEnd](Geo-Streams#lineEnd) - indicate the end of a line or ring.
* [stream.polygonStart](Geo-Streams#polygonStart) - indicate the start of a polygon.
* [stream.polygonEnd](Geo-Streams#polygonEnd) - indicate the end of a polygon.
* [stream.sphere](Geo-Streams#sphere) - indicate a sphere.

## [d3.geom (Geometry)](Geometry)

### [[Voronoi|Voronoi-Geom]]

* [[d3.geom.voronoi|Voronoi-Geom#wiki-voronoi]] - compute the Voronoi diagram for the specified points.
* [[d3.geom.delaunay|Voronoi-Geom#wiki-delaunay]] - compute the Delaunay triangulation for the specified points.

### [[Quadtree|Quadtree-Geom]]

* [[d3.geom.quadtree|Quadtree-Geom#wiki-quadtree]] - constructs a quadtree for an array of points.
* [[quadtree.add|Quadtree-Geom#wiki-add]] - add a point to the quadtree.
* [[quadtree.visit|Quadtree-Geom#wiki-visit]] - recursively visit nodes in the quadtree.

### [[Polygon|Polygon-Geom]]

* [[d3.geom.polygon|Polygon-Geom#wiki-polygon]]
* [[polygon.area|Polygon-Geom#wiki-area]]
* [[polygon.centroid|Polygon-Geom#wiki-centroid]]
* [[polygon.clip|Polygon-Geom#wiki-clip]]

### [[Hull|Hull-Geom]]

* [[d3.geom.hull|Hull-Geom#wiki-hull]]

## [[d3.behavior (Behaviors)|Behaviors]]

### [[Drag|Drag-Behavior]]

* [[d3.behavior.drag|Drag-Behavior#wiki-drag]]
* [[drag.origin|Drag-Behavior#wiki-origin]]
* [[drag.on|Drag-Behavior#wiki-on]]

### [[Zoom|Zoom-Behavior]]

* [[d3.behavior.zoom|Zoom-Behavior#wiki-zoom]]
* [[zoom.on|Zoom-Behavior#wiki-on]]
* [[zoom.scale|Zoom-Behavior#wiki-scale]]
* [[zoom.translate|Zoom-Behavior#wiki-translate]]
* [[zoom.scaleExtent|Zoom-Behavior#wiki-scaleExtent]]
* [[zoom.x|Zoom-Behavior#wiki-x]]
* [[zoom.y|Zoom-Behavior#wiki-y]]