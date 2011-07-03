Everything in D3 is scoped under the `d3` namespace. D3 is broken up into several modules so that you can pick and choose which features you need and minimize the weight. The default build of `d3.js` includes the *core*, *scale* and *svg* modules, at about 12KB [[uglified|https://github.com/mishoo/UglifyJS/]] and gzipped. You can edit the [[Makefile|https://github.com/mbostock/d3/blob/master/Makefile]] to produce a custom build that suits your needs. D3 does not introduce anything else in the global namespace, with the exception of two polyfills for nonstandard browsers: [[Date.now|https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Date/now]] and [[Object.create|https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object/create]].

D3 uses [[semantic versioning|http://semver.org]]. You can find the current version of D3 as `d3.version`.

## [d3 (core)](Core)

### [[Selections]]

* [[d3.select|Selections#d3_select]] - select an element from the current document.
* [[d3.selectAll|Selections#d3_selectAll]] - select multiple elements from the current document.
* [[selection.attr|Selections#attr]] - get or set attribute values.
* [[selection.classed|Selections#classed]] - add or remove CSS classes.
* [[selection.style|Selections#style]] - get or set style properties.
* [[selection.property|Selections#property]] - get or set raw properties.
* [[selection.text|Selections#text]] - get or set text content.
* [[selection.html|Selections#html]] - get or set inner HTML content.
* [[selection.append|Selections#append]] - create and append new elements.
* [[selection.insert|Selections#insert]] - create and insert new elements before existing elements.
* [[selection.remove|Selections#remove]] - remove elements from the document.
* [[selection.data|Selections#data]] - bind data to elements, and compute a relational join.
* [[selection.enter|Selections#enter]] - returns placeholders for missing elements.
* [[selection.exit|Selections#exit]] - returns elements that are no longer needed.
* [[selection.filter|Selections#filter]] - filter a selection based on data.
* [[selection.map|Selections#map]] - modify the data associated with the selected elements.
* [[selection.sort|Selections#sort]] - sort elements in the document based on data.
* [[selection.on|Selections#on]] - add or remove event listeners for interaction.
* [[selection.transition|Selections#transition]] - start a transition on the selected elements.
* [[selection.each|Selections#each]] - call a function for each selected element.
* [[selection.call|Selections#call]] - call a function passing in the current selection.
* [[selection.empty|Selections#empty]] - returns true if the selection is empty.
* [[selection.node|Selections#node]] - access the first node in a selection.
* [[selection.select|Selections#select]] - subselect a descendant element for each selected element.
* [[selection.selectAll|Selections#selectAll]] - subselect multiple descendants for each selected element.
* [[d3.event|Selections#d3_event]] - access the current user event for interaction.

### [[Transitions]]

* [[d3.transition|Transitions#d3_transition]] - start an animated transition.
* [[transition.delay|Transitions#delay]] - specify per-element delay in milliseconds.
* [[transition.duration|Transitions#duration]] - specify per-element duration in milliseconds.
* [[transition.ease|Transitions#ease]] - specify transition easing function.
* [[transition.attr|Transitions#attr]] - smoothly transition to the new attribute value.
* [[transition.attrTween|Transitions#attrTween]] - smoothly transition between two attribute values.
* [[transition.style|Transitions#style]] - smoothly transition to the new style property value.
* [[transition.styleTween|Transitions#styleTween]] - smoothly transition between two style property values.
* [[transition.text|Transitions#text]] - set the text content when the transition starts.
* [[transition.select|Transitions#select]] - start a transition on a descendant element for each selected element.
* [[transition.selectAll|Transitions#selectAll]] - start a transition on multiple descendants for each selected element.
* [[transition.remove|Transitions#remove]] - remove selected elements at the end of a transition.
* [[transition.each|Transitions#each]] - add a listener for transition end events.
* [[transition.call|Transitions#call]] - call a function passing in the current transition.
* [[d3.ease|Transitions#d3_ease]] - customize transition timing.
* [[ease|Transitions#_ease]] - a parametric easing function.
* [[d3.timer|Transitions#d3_timer]] - start a custom animation timer.
* [[d3.timer.flush|Transitions#d3_timer_flush]] - immediately execute any zero-delay timers.
* [[d3.interpolate|Transitions#d3_interpolate]] - interpolate two values.
* [[interpolate|Transitions#_interpolate]] - a parametric interpolation function.
* [[d3.interpolateNumber|Transitions#d3_interpolateNumber]] - interpolate two numbers.
* [[d3.interpolateRound|Transitions#d3_interpolateRound]] - interpolate two integers.
* [[d3.interpolateString|Transitions#d3_interpolateString]] - interpolate two strings.
* [[d3.interpolateRgb|Transitions#d3_interpolateRgb]] - interpolate two RGB colors.
* [[d3.interpolateHsl|Transitions#d3_interpolateHsl]] - interpolate two HSL colors.
* [[d3.interpolateArray|Transitions#d3_interpolateArray]] - interpolate two arrays of values.
* [[d3.interpolateObject|Transitions#d3_interpolateObject]] - interpolate two arbitrary objects.
* [[d3.interpolators|Transitions#d3_interpolators]] - register a custom interpolator.

### [[Working with Arrays|Arrays]]

* [[d3.ascending|Arrays#d3_ascending]] - compare two values for sorting.
* [[d3.descending|Arrays#d3_descending]] - compare two values for sorting.
* [[d3.min|Arrays#d3_min]] - find the minimum value in an array.
* [[d3.max|Arrays#d3_max]] - find the maximum value in an array.
* [[d3.sum|Arrays#d3_sum]] - compute the sum of an array of numbers.
* [[d3.bisect|Arrays#d3_bisect]] - search for a value in a sorted array.
* [[d3.bisectRight|Arrays#d3_bisectRight]] - search for a value in a sorted array.
* [[d3.bisectLeft|Arrays#d3_bisectLeft]] - search for a value in a sorted array.
* [[d3.first|Arrays#d3_first]] - find the lowest element in an array.
* [[d3.last|Arrays#d3_last]] - find the highest element in an array.
* [[d3.permute|Arrays#d3_permute]] - reorder an array of elements according to an array of indexes.
* [[d3.zip|Arrays#d3_zip]] - transpose an array of arrays.
* [[d3.keys|Arrays#d3_keys]] - list the keys of an associative array.
* [[d3.values|Arrays#d3_values]] - list the values of an associated array.
* [[d3.entries|Arrays#d3_entries]] - list the key-value entries of an associative array.
* [[d3.split|Arrays#d3_split]] - split an array into multiple arrays.
* [[d3.merge|Arrays#d3_merge]] - merge multiple arrays into one array.
* [[d3.range|Arrays#d3_range]] - generate a range of numeric values.
* [[d3.nest|Arrays#d3_nest]] - group array elements hierarchically.
* [[nest.key|Arrays#nest_key]] - add a level to the nest hierarchy.
* [[nest.sortKeys|Arrays#nest_sortKeys]] - sort the current nest level by key.
* [[nest.sortValues|Arrays#nest_sortValues]] - sort the leaf nest level by value.
* [[nest.rollup|Arrays#nest_rollup]] - specify a rollup function for leaf values.
* [[nest.map|Arrays#nest_map]] - evaluate the nest operator, returning an associative array.
* [[nest.entries|Arrays#nest_entries]] - evaluate the nest operator, returning an array of key-values tuples.

### [[Loading External Resources|Requests]]

* [[d3.xhr|Requests#d3_xhr]] - request a resource using XMLHttpRequest.
* [[d3.text|Requests#d3_text]] - request a text file.
* [[d3.json|Requests#d3_json]] - request a JSON blob.
* [[d3.html|Requests#d3_html]] - request an HTML document fragment.
* [[d3.xml|Requests#d3_xml]] - request an XML document fragment.

### [[String Formatting|Formatting]]

* [[d3.format|Formatting#d3_format]] - format a number as a string.
* [[d3.requote|Formatting#d3_requote]] - quote a string for use in a regular expression.
* [[d3.round|Formatting#d3_round]] - rounds a value to some digits after the decimal point.

### [[Time Formatting (d3.time)|Time-Formatting]]

* [[d3.time.format|Time-Formatting#format]] - create a new local time formatter for a given specifier.
* [[format|Time-Formatting#_format]] - format a date into a string.
* [[format.parse|Time-Formatting#parse]] - parse a string into a date.
* [[d3.time.format.utc|Time-Formatting#format_utc]] - create a new UTC time formatter for a given specifier.
* [[d3.time.format.iso|Time-Formatting#format_iso]] - the ISO 8601 UTC time formatter.

### [[CSV Formatting (d3.csv)|CSV]]

* [[d3.csv|CSV#csv]] - request a comma-separated values (CSV) file.
* [[d3.csv.parse|CSV#parse]] - parse a CSV string into objects using the header row.
* [[d3.csv.parseRows|CSV#parseRows]] - parse a CSV string into tuples, ignoring the header row.
* [[d3.csv.format|CSV#format]] - format an array of tuples into a CSV string.

### [[Colors]]

* [[d3.rgb|Colors#d3_rgb]] - specify a color in RGB space.
* [[rgb.brighter|Colors#rgb_brighter]] - increase RGB channels by some exponential factor (gamma).
* [[rgb.darker|Colors#rgb_darker]] - decrease RGB channels by some exponential factor (gamma).
* [[rgb.hsl|Colors#rgb_hsl]] - convert from RGB to HSL.
* [[rgb.toString|Colors#rgb_toString]] - convert an RGB color to a string.
* [[d3.hsl|Colors#d3_hsl]] - specify a color in HSL space.
* [[hsl.brighter|Colors#hsl_brighter]] - increase lightness by some exponential factor (gamma).
* [[hsl.darker|Colors#hsl_darker]] - decrease lightness by some exponential factor (gamma).
* [[hsl.rgb|Colors#hsl_rgb]] - convert from HSL to RGB.
* [[hsl.toString|Colors#hsl_toString]] - convert an HSL color to a string.

### [[Namespaces]]

* [[d3.ns.prefix|Namespaces#prefix]] - access or extend known XML namespaces.
* [[d3.ns.qualify|Namespaces#qualify]] - qualify a prefixed name, such as "xlink:href".

### [[Internals]]

* [[d3.functor|Internals#d3_functor]] - create a function that returns a constant.
* [[d3.rebind|Internals#d3_rebind]] - rebind an inherited getter/setter method to a subclass.
* [[d3.dispatch|Internals#d3_dispatch]] - create a custom event dispatcher.
* [[dispatch.add|Internals#dispatch_add]] - register an event listener.
* [[dispatch.remove|Internals#dispatch_remove]] - unregister an event listener.
* [[dispatch.dispatch|Internals#dispatch_dispatch]] - dispatch an event to registered listeners.

## [d3.scale (Scales)](Scales)

### [[Quantitative|Quantitative-Scales#quantitative]]

* [[d3.scale.linear|Quantitative-Scales#linear]] - construct a linear quantitative scale.
* [[linear|Quantitative-Scales#_linear]] - get the range value corresponding to a given domain value.
* [[linear.invert|Quantitative-Scales#linear_invert]] - get the domain value corresponding to a given range value.
* [[linear.domain|Quantitative-Scales#linear_domain]] - get or set the scale's input domain.
* [[linear.range|Quantitative-Scales#linear_range]] - get or set the scale's output range.
* [[linear.rangeRound|Quantitative-Scales#linear_rangeRound]] - set the scale's output range, and enable rounding.
* [[linear.interpolate|Quantitative-Scales#linear_interpolate]] - get or set the scale's output interpolator.
* [[linear.clamp|Quantitative-Scales#linear_clamp]] - enable or disable clamping of the output range.
* [[linear.nice|Quantitative-Scales#linear_nice]] - extend the scale domain to nice round numbers.
* [[linear.ticks|Quantitative-Scales#linear_ticks]] - get representative values from the input domain.
* [[linear.tickFormat|Quantitative-Scales#linear_tickFormat]] - get a formatter for displaying tick values.
* [[d3.scale.sqrt|Quantitative-Scales#sqrt]] - construct a quantitative scale with a square root transform.
* [[d3.scale.pow|Quantitative-Scales#pow]] - construct a quantitative scale with an exponential transform.
* [[pow|Quantitative-Scales#_pow]] - get the range value corresponding to a given domain value.
* [[pow.invert|Quantitative-Scales#pow_invert]] - get the domain value corresponding to a given range value. 
* [[pow.domain|Quantitative-Scales#pow_domain]] - get or set the scale's input domain.
* [[pow.range|Quantitative-Scales#pow_range]] - get or set the scale's output range.
* [[pow.rangeRound|Quantitative-Scales#pow_rangeRound]] - set the scale's output range, and enable rounding.
* [[pow.interpolate|Quantitative-Scales#pow_interpolate]] - get or set the scale's output interpolator.
* [[pow.clamp|Quantitative-Scales#pow_clamp]] - enable or disable clamping of the output range.
* [[pow.nice|Quantitative-Scales#pow_nice]] - extend the scale domain to nice round numbers.
* [[pow.ticks|Quantitative-Scales#pow_ticks]] - get representative values from the input domain.
* [[pow.tickFormat|Quantitative-Scales#pow_tickFormat]] - get a formatter for displaying tick values.
* [[pow.exponent|Quantitative-Scales#pow_exponent]] - get or set the exponent power.
* [[d3.scale.log|Quantitative-Scales#log]] - construct a quantitative scale with an logarithmic transform.
* [[log|Quantitative-Scales#_log]] - get the range value corresponding to a given domain value.
* [[log.invert|Quantitative-Scales#log_invert]] - get the domain value corresponding to a given range value. 
* [[log.domain|Quantitative-Scales#log_domain]] - get or set the scale's input domain.
* [[log.range|Quantitative-Scales#log_range]] - get or set the scale's output range.
* [[log.rangeRound|Quantitative-Scales#log_rangeRound]] - set the scale's output range, and enable rounding.
* [[log.interpolate|Quantitative-Scales#log_interpolate]] - get or set the scale's output interpolator.
* [[log.clamp|Quantitative-Scales#log_clamp]] - enable or disable clamping of the output range.
* [[log.nice|Quantitative-Scales#log_nice]] - extend the scale domain to nice powers of ten.
* [[log.ticks|Quantitative-Scales#log_ticks]] - get representative values from the input domain.
* [[log.tickFormat|Quantitative-Scales#log_tickFormat]] - get a formatter for displaying tick values.
* [[d3.scale.quantize|Quantitative-Scales#quantize]] - construct a linear quantitative scale with a discrete output range.
* [[quantize|Quantitative-Scales#_quantize]] - get the range value corresponding to a given domain value.
* [[quantize.domain|Quantitative-Scales#quantize_domain]] - get or set the scale's input domain.
* [[quantize.range|Quantitative-Scales#quantize_range]] - get or set the scale's output range (as discrete values).
* [[d3.scale.quantile|Quantitative-Scales#quantile]] - construct a quantitative scale mapping to quantiles.
* [[quantile|Quantitative-Scales#_quantile]] - get the range value corresponding to a given domain value.
* [[quantile.domain|Quantitative-Scales#quantile_domain]] - get or set the scale's input domain (as discrete values).
* [[quantile.range|Quantitative-Scales#quantile_range]] - get or set the scale's output range (as discrete values).
* [[quantile.quantiles|Quantitative-Scales#quantile_quantiles]] - get the scale's quantile bin thresholds.

### [[Ordinal|Ordinal-Scales#ordinal]]

* [[d3.scale.ordinal|Ordinal-Scales#ordinal]] - construct an ordinal scale.
* [[ordinal|Ordinal-Scales#_ordinal]] - get the range value corresponding to a given domain value.
* [[ordinal.domain|Ordinal-Scales#ordinal_domain]] - get or set the scale's input domain.
* [[ordinal.range|Ordinal-Scales#ordinal_range]] - get or set the scale's output range.
* [[ordinal.rangePoints|Ordinal-Scales#ordinal_rangePoints]] - divide a continuous output range for discrete points.
* [[ordinal.rangeBands|Ordinal-Scales#ordinal_rangeBands]] - divide a continuous output range for discrete bands.
* [[ordinal.rangeRoundBands|Ordinal-Scales#ordinal_rangeRoundBands]] - divide a continuous output range for discrete bands.
* [[ordinal.rangeBand|Ordinal-Scales#ordinal_rangeBand]] - get the discrete range band width.
* [[d3.scale.category10|Ordinal-Scales#category10]] - construct an ordinal scale with ten categorical colors.
* [[d3.scale.category20|Ordinal-Scales#category20]] - construct an ordinal scale with twenty categorical colors.
* [[d3.scale.category20b|Ordinal-Scales#category20b]] - construct an ordinal scale with twenty categorical colors.
* [[d3.scale.category20c|Ordinal-Scales#category20c]] - construct an ordinal scale with twenty categorical colors.

## [d3.svg (SVG)](SVG)

### [[Shapes|SVG-Shapes]]

* [[d3.svg.line|SVG-Shapes#line]] - create a new line generator.
* [[line|SVG-Shapes#_line]] - generate a piecewise linear curve, as in a line chart.
* [[line.x|SVG-Shapes#line_x]] - get or set the *x*-coordinate accessor.
* [[line.y|SVG-Shapes#line_y]] - get or set the *y*-coordinate accessor.
* [[line.interpolate|SVG-Shapes#line_interpolate]] - get or set the interpolation mode.
* [[line.tension|SVG-Shapes#line_tension]] - get or set the cardinal spline tension.
* [[d3.svg.line.radial|SVG-Shapes#line_radial]] - create a new radial line generator.
* [[line|SVG-Shapes#_line_radial]] - generate a piecewise linear curve, as in a polar line chart.
* [[line.radius|SVG-Shapes#line_radial_radius]] - get or set the *radius* accessor.
* [[line.angle|SVG-Shapes#line_radial_angle]] - get or set the *angle* accessor.
* [[d3.svg.area|SVG-Shapes#area]] - create a new area generator.
* [[area|SVG-Shapes#_area]] - generate a piecewise linear area, as in an area chart.
* [[area.x|SVG-Shapes#area_x]] - get or set the *x*-coordinate accessors.
* [[area.x0|SVG-Shapes#area_x0]] - get or set the *x0*-coordinate (baseline) accessor.
* [[area.x1|SVG-Shapes#area_x1]] - get or set the *x1*-coordinate (topline) accessor.
* [[area.y|SVG-Shapes#area_y]] - get or set the *y*-coordinate accessors.
* [[area.y0|SVG-Shapes#area_y0]] - get or set the *y0*-coordinate (baseline) accessor.
* [[area.y1|SVG-Shapes#area_y1]] - get or set the *y1*-coordinate (topline) accessor.
* [[area.interpolate|SVG-Shapes#area_interpolate]] - get or set the interpolation mode.
* [[area.tension|SVG-Shapes#area_tension]] - get or set the cardinal spline tension.
* [[d3.svg.area.radial|SVG-Shapes#area_radial]] - create a new area generator.
* [[area|SVG-Shapes#_area_radial]] - generate a piecewise linear area, as in a polar area chart.
* [[area.radius|SVG-Shapes#area_radial_radius]] - get or set the *radius* accessors.
* [[area.innerRadius|SVG-Shapes#area_radial_innerRadius]] - get or set the inner *radius* (baseline) accessor.
* [[area.outerRadius|SVG-Shapes#area_radial_outerRadius]] - get or set the outer *radius* (topline) accessor.
* [[area.angle|SVG-Shapes#area_radial_angle]] - get or set the *angle* accessors.
* [[area.startAngle|SVG-Shapes#area_radial_startAngle]] - get or set the *angle* (baseline) accessor.
* [[area.endAngle|SVG-Shapes#area_radial_endAngle]] - get or set the *angle* (topline) accessor.
* [[d3.svg.arc|SVG-Shapes#arc]] - create a new arc generator.
* [[arc|SVG-Shapes#_arc]] - generate a solid arc, as in a pie or donut chart.
* [[arc.innerRadius|SVG-Shapes#arc_innerRadius]] - get or set the inner radius accessor.
* [[arc.outerRadius|SVG-Shapes#arc_outerRadius]] - get or set the outer radius accessor.
* [[arc.startAngle|SVG-Shapes#arc_startAngle]] - get or set the start angle accessor.
* [[arc.endAngle|SVG-Shapes#arc_endAngle]] - get or set the end angle accessor.
* [[arc.centroid|SVG-Shapes#arc_centroid]] - compute the arc centroid.
* [[d3.svg.symbol|SVG-Shapes#symbol]] - create a new symbol generator.
* [[symbol|SVG-Shapes#_symbol]] - generate categorical symbols, as in a scatterplot.
* [[symbol.type|SVG-Shapes#symbol_type]] - get or set the symbol type accessor.
* [[symbol.size|SVG-Shapes#symbol_size]] - get or set the symbol size (in square pixels) accessor.
* [[d3.svg.chord|SVG-Shapes#chord]] - create a new chord generator.
* [[chord|SVG-Shapes#_chord]] - generate a quadratic Bézier connecting two arcs, as in a chord diagram.
* [[chord.radius|SVG-Shapes#chord_radius]] - get or set the arc radius accessor.
* [[chord.startAngle|SVG-Shapes#chord_startAngle]] - get or set the arc start angle accessor.
* [[chord.endAngle|SVG-Shapes#chord_endAngle]] - get or set the arc end angle accessor.
* [[chord.source|SVG-Shapes#chord_source]] - get or set the source arc accessor.
* [[chord.target|SVG-Shapes#chord_target]] - get or set the target arc accessor.
* [[d3.svg.diagonal|SVG-Shapes#diagonal]] - create a new diagonal generator.
* [[diagonal|SVG-Shapes#_diagonal]] - generate a two-dimensional Bézier connector, as in a node-link diagram.
* [[diagonal.source|SVG-Shapes#diagonal_source]] - get or set the source point accessor.
* [[diagonal.target|SVG-Shapes#diagonal_target]] - get or set the target point accessor.
* [[diagonal.projection|SVG-Shapes#diagonal_projection]] - get or set an optional point transform.
* [[d3.svg.diagonal.radial|SVG-Shapes#diagonal_radial]] - create a new diagonal generator.
* [[diagonal|SVG-Shapes#_diagonal_radial]] - generate a two-dimensional Bézier connector, as in a node-link diagram.

### [[Events|SVG-Events]]

* [[d3.svg.mouse|SVG-Events#mouse]] - gets the mouse position relative to a specified container.
* [[d3.svg.touches|SVG-Events#touches]] - gets the touch positions relative to a specified container.

## [d3.layout (Layouts)](Layouts)

### [[Bundle|Bundle-Layout]]

* [[d3.layout.bundle|Bundle-Layout#bundle]] - construct a new default bundle layout.
* [[bundle|Bundle-Layout#_bundle]] - apply Holten's *hierarchical bundling* algorithm to edges.

### [[Chord|Chord-Layout]]

* [[d3.layout.chord|Chord-Layout#chord]] - produce a chord diagram from a matrix of relationships.
* [[chord.matrix|Chord-Layout#matrix]] - get or set the matrix data backing the layout.
* [[chord.padding|Chord-Layout#padding]] - get or set the angular padding between chord segments.
* [[chord.sortGroups|Chord-Layout#sortGroups]] - get or set the comparator function for groups.
* [[chord.sortSubgroups|Chord-Layout#sortSubgroups]] - get or set the comparator function for subgroups.
* [[chord.sortChords|Chord-Layout#sortChords]] - get or set the comparator function for chords (z-order).
* [[chord.chords|Chord-Layout#chords]] - retrieve the computed chord angles.
* [[chord.groups|Chord-Layout#groups]] - retrieve the computed group angles.

### [[Cluster|Cluster-Layout]]

* [[d3.layout.cluster|Cluster-Layout#cluster]] - cluster entities into a dendrogram.
* [[cluster.sort|Cluster-Layout#sort]] - get or set the comparator function for sibling nodes.
* [[cluster.children|Cluster-Layout#children]] - get or set the accessor function for child nodes.
* [[cluster.nodes|Cluster-Layout#nodes]] - compute the cluster layout and return the array of nodes.
* [[cluster.links|Cluster-Layout#links]] - compute the parent-child links between tree nodes.
* [[cluster.separation|Cluster-Layout#separation]] - get or set the spacing function between neighboring nodes.
* [[cluster.size|Cluster-Layout#size]] - get or set the layout size in *x* and *y*.

### [[Force|Force-Layout]]

* [[d3.layout.force|Force-Layout#force]] - position linked nodes using physical simulation.
* [[force.on|Force-Layout#on]] - listen to updates in the computed layout positions.
* [[force.nodes|Force-Layout#nodes]] - get or set the array of nodes to layout.
* [[force.links|Force-Layout#links]] - get or set the array of links between nodes.
* [[force.size|Force-Layout#size]] - get or set the layout size in *x* and *y*.
* [[force.distance|Force-Layout#distance]] - get or set the link distance.
* [[force.friction|Force-Layout#friction]] - get or set the friction coefficient.
* [[force.charge|Force-Layout#charge]] - get or set the charge strength.
* [[force.gravity|Force-Layout#gravity]] - get or set the gravity strength.
* [[force.theta|Force-Layout#theta]] - get or set the accuracy of the charge interaction.
* [[force.start|Force-Layout#start]] - start or restart the simulation when the nodes change.
* [[force.resume|Force-Layout#resume]] - reheat the cooling parameter and restart simulation.
* [[force.stop|Force-Layout#stop]] - immediately terminate the simulation.
* [[force.drag|Force-Layout#drag]] - bind a behavior to nodes to allow interactive dragging.

### [[Hierarchy|Hierarchy-Layout]]

* [[d3.layout.hierarchy|Hierarchy-Layout#hierarchy]] - derive a custom hierarchical layout implementation.
* [[hierarchy.sort|Hierarchy-Layout#sort]] - get or set the comparator function for sibling nodes.
* [[hierarchy.children|Hierarchy-Layout#children]] - get or set the accessor function for child nodes.
* [[hierarchy.nodes|Hierarchy-Layout#nodes]] - compute the layout and return the array of nodes.
* [[hierarchy.links|Hierarchy-Layout#links]] - compute the parent-child links between tree nodes.
* [[hierarchy.value|Hierarchy-Layout#value]] - get or set the value accessor function.
* [[hierarchy.revalue|Hierarchy-Layout#revalue]] - recompute the hierarchy values.

### [[Histogram|Histogram-Layout]]

* [[d3.layout.histogram|Histogram-Layout#histogram]] - construct a new default histogram layout.
* [[histogram|Histogram-Layout#_histogram]] - compute the distribution of data using quantized bins.
* [[histogram.value|Histogram-Layout#value]] - get or set the value accessor function.
* [[histogram.range|Histogram-Layout#range]] - get or set the considered value range.
* [[histogram.bins|Histogram-Layout#bins]] - specify how values are organized into bins.
* [[histogram.frequency|Histogram-Layout#frequency]] - compute the distribution as counts or probabilities.

### [[Pack|Pack-Layout]]

* [[d3.layout.pack|Pack-Layout#pack]] - produce a hierarchical layout using recursive circle-packing.
* [[pack.sort|Pack-Layout#sort]] - control the order in which sibling nodes are traversed.
* [[pack.children|Pack-Layout#children]] - get or set the children accessor function.
* [[pack.nodes|Pack-Layout#nodes]] - compute the pack layout and return the array of nodes.
* [[pack.links|Pack-Layout#links]] - compute the parent-child links between tree nodes.
* [[pack.value|Pack-Layout#value]] - get or set the value accessor used to size circles.
* [[pack.size|Pack-Layout#size]] - specify the layout size in *x* and *y*.

### [[Partition|Partition-Layout]]

* [[d3.layout.partition|Partition-Layout#partition]] - recursively partition a node tree into a sunburst or icicle.
* [[partition.sort|Partition-Layout#sort]] - control the order in which sibling nodes are traversed.
* [[partition.children|Partition-Layout#children]] - get or set the children accessor function.
* [[partition.nodes|Partition-Layout#nodes]] - compute the partition layout and return the array of nodes.
* [[partition.links|Partition-Layout#links]] - compute the parent-child links between tree nodes.
* [[partition.value|Partition-Layout#value]] - get or set the value accessor used to size circles.
* [[partition.size|Partition-Layout#size]] - specify the layout size in *x* and *y*.

### [[Pie|Pie-Layout]]

* [[d3.layout.pie|Pie-Layout#pie]] - construct a new default pie layout.
* [[pie|Pie-Layout#_pie]] - compute the start and end angles for arcs in a pie or donut chart.
* [[pie.value|Pie-Layout#value]] - get or set the value accessor function.
* [[pie.sort|Pie-Layout#sort]] - control the clockwise order of pie slices.
* [[pie.startAngle|Pie-Layout#startAngle]] - get or set the overall start angle of the pie.
* [[pie.endAngle|Pie-Layout#endAngle]] - get or set the overall end angle of the pie.

### [[Stack|Stack-Layout]]

* [[d3.layout.stack|Stack-Layout#stack]] - construct a new default stack layout.
* [[stack|Stack-Layout#_stack]] - compute the baseline for each series in a stacked bar or area chart.
* [[stack.values|Stack-Layout#values]] - get or set the values accessor function per series.
* [[stack.order|Stack-Layout#order]] - control the order in which series are stacked.
* [[stack.offset|Stack-Layout#offset]] - specify the overall baseline algorithm.
* [[stack.x|Stack-Layout#x]] - get or set the *x*-dimension accessor function.
* [[stack.y|Stack-Layout#y]] - get or set the *y*-dimension accessor function.
* [[stack.out|Stack-Layout#out]] - get or set the output function for storing the baseline.

### [[Tree|Tree-Layout]]

* [[d3.layout.tree|Tree-Layout#tree]] - position a tree of nodes tidily.
* [[tree.sort|Tree-Layout#sort]] - control the order in which sibling nodes are traversed.
* [[tree.children|Tree-Layout#children]] - get or set the children accessor function.
* [[tree.nodes|Tree-Layout#nodes]] - compute the tree layout and return the array of nodes.
* [[tree.links|Tree-Layout#links]] - compute the parent-child links between tree nodes.
* [[tree.separation|Tree-Layout#separation]] - get or set the spacing function between neighboring nodes.
* [[tree.size|Tree-Layout#size]] - specify the layout size in *x* and *y*.

### [[Treemap|Treemap-Layout]]

* [[d3.layout.treemap|Treemap-Layout#treemap]] - use recursive spatial subdivision to display a tree of nodes.
* [[treemap.sort|Treemap-Layout#sort]] - control the order in which sibling nodes are traversed.
* [[treemap.children|Treemap-Layout#children]] - get or set the children accessor function.
* [[treemap.nodes|Treemap-Layout#nodes]] - compute the treemap layout and return the array of nodes.
* [[treemap.links|Treemap-Layout#links]] - compute the parent-child links between tree nodes.
* [[treemap.value|Treemap-Layout#value]] - get or set the value accessor used to size treemap cells.
* [[treemap.size|Treemap-Layout#size]] - specify the layout size in *x* and *y*.
* [[treemap.round|Treemap-Layout#round]] - enable or disable rounding to exact pixels.
* [[treemap.sticky|Treemap-Layout#sticky]] - make the layout sticky for stable updates.

## [[d3.geo (Geography)|Geo]]

### [[Paths|Geo-Paths]]

* [[d3.geo.path|Geo-Paths#path]]
* [[path.projection|Geo-Paths#projection]]
* [[path.area|Geo-Paths#area]]
* [[path.centroid|Geo-Paths#centroid]]
* [[path.pointRadius|Geo-Paths#pointRadius]]
* [[d3.geo.bounds|Geo-Paths#bounds]]

### [[Projections|Geo-Projections]]

* [[d3.geo.mercator|Geo-Projections#mercator]]
* [[mercator.scale|Geo-Projections#mercator_scale]]
* [[mercator.translate|Geo-Projections#mercator_translate]]
* [[d3.geo.albers|Geo-Projections#albers]]
* [[albers.origin|Geo-Projections#albers_origin]]
* [[albers.parallels|Geo-Projections#albers_parallels]]
* [[albers.scale|Geo-Projections#albers_scale]]
* [[albers.translate|Geo-Projections#albers_translate]]
* [[d3.geo.albersUsa|Geo-Projections#albersUsa]]
* [[albersUsa.scale|Geo-Projections#albersUsa_scale]]
* [[albersUsa.translate|Geo-Projections#albersUsa_translate]]
* [[d3.geo.azimuthal|Geo-Projections#azimuthal]]
* [[azimuthal.mode|Geo-Projections#azimuthal_mode]]
* [[azimuthal.origin|Geo-Projections#azimuthal_origin]]
* [[azimuthal.scale|Geo-Projections#azimuthal_scale]]
* [[azimuthal.translate|Geo-Projections#azimuthal_translate]]

## [[d3.geom (Geometry)|Geom]]

### [[Voronoi|Voronoi-Geom]]

* [[d3.geom.voronoi|Voronoi-Geom#voronoi]]
* [[d3.geom.delaunay|Voronoi-Geom#delaunay]]

### [[Quadtree|Quadtree-Geom]]

* [[d3.geom.quadtree|Quadtree-Geom#quadtree]]
* [[quadtree.visit|Quadtree-Geom#visit]]

### [[Polygon|Polygon-Geom]]

* [[d3.geom.polygon|Polygon-Geom#polygon]]
* [[polygon.area|Polygon-Geom#area]]
* [[polygon.centroid|Polygon-Geom#centroid]]
* [[polygon.clip|Polygon-Geom#clip]]

### [[Hull|Hull-Geom]]

* [[d3.geom.hull|Hull-Geom#hull]]

### [[Contour|Contour-Geom]]

* [[d3.geom.contour|Contour-Geom#contour]]

## [[d3.chart (Charts)|Charts]]

### [[Box|Box-Chart]]

* [[d3.chart.box|Box-Chart#box]]
* [[box.width|Box-Chart#width]]
* [[box.height|Box-Chart#height]]
* [[box.tickFormat|Box-Chart#tickFormat]]
* [[box.duration|Box-Chart#duration]]
* [[box.domain|Box-Chart#domain]]
* [[box.value|Box-Chart#value]]
* [[box.whiskers|Box-Chart#whiskers]]
* [[box.quartiles|Box-Chart#quartiles]]

### [[Bullet|Bullet-Chart]]

* [[d3.chart.bullet|Bullet-Chart#bullet]]
* [[bullet.orient|Bullet-Chart#orient]]
* [[bullet.ranges|Bullet-Chart#ranges]]
* [[bullet.markers|Bullet-Chart#markers]]
* [[bullet.measures|Bullet-Chart#measures]]
* [[bullet.width|Bullet-Chart#width]]
* [[bullet.height|Bullet-Chart#height]]
* [[bullet.tickFormat|Bullet-Chart#tickFormat]]
* [[bullet.duration|Bullet-Chart#duration]]

### [[Horizon|Horizon-Chart]]

* [[d3.chart.horizon|Horizon-Chart#horizon]]
* [[horizon.duration|Horizon-Chart#duration]]
* [[horizon.bands|Horizon-Chart#bands]]
* [[horizon.mode|Horizon-Chart#mode]]
* [[horizon.colors|Horizon-Chart#colors]]
* [[horizon.interpolate|Horizon-Chart#interpolate]]
* [[horizon.x|Horizon-Charts#x]]
* [[horizon.y|Horizon-Charts#y]]
* [[horizon.width|Horizon-Charts#width]]
* [[horizon.height|Horizon-Charts#height]]

### [[QQ|QQ-Chart]]

* [[d3.chart.qq|QQ-Chart#qq]]
* [[qq.width|QQ-Chart#width]]
* [[qq.height|QQ-Chart#height]]
* [[qq.duration|QQ-Chart#duration]]
* [[qq.domain|QQ-Chart#domain]]
* [[qq.count|QQ-Chart#count]]
* [[qq.x|QQ-Chart#x]]
* [[qq.y|QQ-Chart#y]]
* [[qq.tickFormat|QQ-Chart#tickFormat]]

## [[d3.behavior (Behaviors)|Behaviors]]

### [[Zoom|Zoom-Behavior]]

* [[d3.behavior.zoom|Zoom-Behavior#zoom]]
* [[zoom.on|Zoom-Behavior#on]]
