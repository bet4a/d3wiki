Everything in D3 is scoped under the `d3` namespace. D3 is broken up into several modules so that you can pick and choose which features you need and minimize the weight. The default build of `d3.js` includes the *core*, *scale* and *svg* modules, at about 12KB [[uglified|https://github.com/mishoo/UglifyJS/]] and gzipped. You can edit the [[Makefile|https://github.com/mbostock/d3/blob/master/Makefile]] to produce a custom build that suites your needs. D3 does not introduce anything else in the global namespace, with the exception of two polyfills for nonstandard browsers: [[Date.now|https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Date/now]] and [[Object.create|https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object/create]].

D3 uses [[semantic versioning|http://semver.org]]. You can find the current version of D3 as `d3.version`.

## d3 (core)

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
* [[d3.ns|Selections#d3_ns]] - access or extend known XML namespaces.
* [[d3.functor|Selections#d3_functor]] - create a function that returns a constant.
* [[d3.rebind|Selections#d3_rebind]] - 

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
* [[d3.timer|Transitions#d3_timer]] - start a custom animation timer.
* [[d3.timer.flush|Transitions#d3_timer_flush]] - immediately execute any zero-delay timers.
* [[d3.interpolate|Transitions#d3_interpolate]] - interpolate two values.
* [[d3.interpolateNumber|Transitions#d3_interpolateNumber]] - interpolate two numbers.
* [[d3.interpolateRound|Transitions#d3_interpolateRound]] - interpolate two integers.
* [[d3.interpolateString|Transitions#d3_interpolateString]] - interpolate two strings.
* [[d3.interpolateRgb|Transitions#d3_interpolateRgb]] - interpolate two RGB colors.
* [[d3.interpolateHsl|Transitions#d3_interpolateHsl]] - interpolate two HSL colors.
* [[d3.interpolateArray|Transitions#d3_interpolateArray]] - interpolate two arrays of values.
* [[d3.interpolateObject|Transitions#d3_interpolateObject]] - interpolate two arbitrary objects.

### [[Working with Arrays|Arrays]]

* [[d3.ascending|Arrays#d3_ascending]] - compare two values for sorting.
* [[d3.descending|Arrays#d3_descending]] - compare two values for sorting.
* [[d3.min|Arrays#d3_min]] - find the minimum value in an array.
* [[d3.max|Arrays#d3_max]] - find the maximum value in an array.
* [[d3.bisect|Arrays#d3_bisect]] - 
* [[d3.bisectRight|Arrays#d3_bisectRight]] - 
* [[d3.bisectLeft|Arrays#d3_bisectLeft]] - 
* [[d3.permute|Arrays#d3_permute]] - 
* [[d3.zip|Arrays#d3_zip]] -
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

* [[d3.xhr|Requests#d3_xhr]] - request a resource using `XMLHttpRequest`.
* [[d3.text|Requests#d3_text]] - request a text file.
* [[d3.json|Requests#d3_json]] - request a JSON blob.
* [[d3.html|Requests#d3_html]] - request an HTML document fragment.
* [[d3.xml|Requests#d3_xml]] - request an XML document fragment.

Also see the [[CSV]] module.

### [[String Formatting|Formatting]]

* [[d3.format|Formatting#d3_format]] - format a number as a string.
* [[d3.requote|Formatting#d3_requote]] - 
* [[d3.round|Formatting#d3_round]] - 

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

### [[Internals]]

* [[d3.dispatch|Internals#d3_dispatch]] - create a custom event dispatcher.

## d3.scale

### [[Quantitative|Quantitative-Scales#quantitative]]

* [[d3.scale.linear|Quantitative-Scales#linear]] - construct a linear quantitative scale.
* [[linear.invert|Quantitative-Scales#linear_invert]] - get the domain value corresponding to a given range value.
* [[linear.domain|Quantitative-Scales#linear_domain]] - get or set the scale's input domain.
* [[linear.range|Quantitative-Scales#linear_range]] - get or set the scale's output range.
* [[linear.rangeRound|Quantitative-Scales#linear_rangeRound]] - set the scale's output range, and enable rounding.
* [[linear.interpolate|Quantitative-Scales#linear_interpolate]] - get or set the scale's output interpolator.
* [[linear.clamp|Quantitative-Scales#linear_clamp]] - enable or disable clamping of the output range.
* [[linear.ticks|Quantitative-Scales#linear_ticks]] - get representative values from the input domain.
* [[linear.tickFormat|Quantitative-Scales#linear_tickFormat]] - get a formatter for displaying tick values.
* [[d3.scale.sqrt|Quantitative-Scales#sqrt]] - construct a quantitative scale with a square root transform.
* [[d3.scale.pow|Quantitative-Scales#pow]] - construct a quantitative scale with an exponential transform.
* [[pow.invert|Quantitative-Scales#pow_invert]] - get the domain value corresponding to a given range value. 
* [[pow.domain|Quantitative-Scales#pow_domain]] - get or set the scale's input domain.
* [[pow.range|Quantitative-Scales#pow_range]] - get or set the scale's output range.
* [[pow.rangeRound|Quantitative-Scales#pow_rangeRound]] - set the scale's output range, and enable rounding.
* [[pow.interpolate|Quantitative-Scales#pow_interpolate]] - get or set the scale's output interpolator.
* [[pow.clamp|Quantitative-Scales#pow_clamp]] - enable or disable clamping of the output range.
* [[pow.ticks|Quantitative-Scales#pow_ticks]] - get representative values from the input domain.
* [[pow.tickFormat|Quantitative-Scales#pow_tickFormat]] - get a formatter for displaying tick values.
* [[pow.exponent|Quantitative-Scales#pow_exponent]] - get or set the exponent power.
* [[d3.scale.log|Quantitative-Scales#log]] - construct a quantitative scale with an logarithmic transform.
* [[log.invert|Quantitative-Scales#log_invert]] - get the domain value corresponding to a given range value. 
* [[log.domain|Quantitative-Scales#log_domain]] - get or set the scale's input domain.
* [[log.range|Quantitative-Scales#log_range]] - get or set the scale's output range.
* [[log.rangeRound|Quantitative-Scales#log_rangeRound]] - set the scale's output range, and enable rounding.
* [[log.interpolate|Quantitative-Scales#log_interpolate]] - get or set the scale's output interpolator.
* [[log.clamp|Quantitative-Scales#log_clamp]] - enable or disable clamping of the output range.
* [[log.ticks|Quantitative-Scales#log_ticks]] - get representative values from the input domain.
* [[log.tickFormat|Quantitative-Scales#log_tickFormat]] - get a formatter for displaying tick values.
* [[d3.scale.quantize|Quantitative-Scales#quantize]] - construct a linear quantitative scale with a discrete output range.
* [[quantize.domain|Quantitative-Scales#quantize_domain]] - get or set the scale's input domain.
* [[quantize.range|Quantitative-Scales#quantize_range]] - get or set the scale's output range (as discrete values).
* [[d3.scale.quantile|Quantitative-Scales#quantile]] - construct a quantitative scale mapping to quantiles.
* [[quantile.domain|Quantitative-Scales#quantile_domain]] - get or set the scale's input domain (as discrete values).
* [[quantile.range|Quantitative-Scales#quantile_range]] - get or set the scale's output range (as discrete values).
* [[quantile.quantiles|Quantitative-Scales#quantile_quantiles]] - get the scale's quantile bin thresholds.

### [[Ordinal|Ordinal-Scales#ordinal]]

* [[d3.scale.ordinal|Ordinal-Scales#ordinal]]
* [[ordinal.domain|Ordinal-Scales#ordinal_domain]]
* [[ordinal.range|Ordinal-Scales#ordinal_range]]
* [[ordinal.rangePoints|Ordinal-Scales#ordinal_rangePoints]]
* [[ordinal.rangeBands|Ordinal-Scales#ordinal_rangeBands]]
* [[ordinal.rangeRoundBands|Ordinal-Scales#ordinal_rangeRoundBands]]
* [[ordinal.rangeBand|Ordinal-Scales#ordinal_rangeBand]]
* [[d3.scale.category10|Ordinal-Scales#category10]]
* [[d3.scale.category20|Ordinal-Scales#category20]]
* [[d3.scale.category20b|Ordinal-Scales#category20b]]
* [[d3.scale.category20c|Ordinal-Scales#category20c]]

## d3.svg

### [[Events|SVG-Events]]

* [[d3.svg.mouse|SVG-Events#mouse]]
* [[d3.svg.touches|SVG-Events#touches]]

### [[Shapes|SVG-Shapes]]

* [[d3.svg.line|SVG-Shapes#line]]
* [[line.x|SVG-Shapes#line_x]]
* [[line.y|SVG-Shapes#line_y]]
* [[line.interpolate|SVG-Shapes#line_interpolate]]
* [[line.tension|SVG-Shapes#line_tension]]
* [[d3.svg.diagonal|SVG-Shapes#diagonal]]
* [[diagonal.source|SVG-Shapes#diagonal_source]]
* [[diagonal.target|SVG-Shapes#diagonal_target]]
* [[diagonal.projection|SVG-Shapes#diagonal_projection]]
* [[d3.svg.chord|SVG-Shapes#chord]]
* [[chord.radius|SVG-Shapes#chord_radius]]
* [[chord.source|SVG-Shapes#chord_source]]
* [[chord.target|SVG-Shapes#chord_target]]
* [[chord.startAngle|SVG-Shapes#chord_startAngle]]
* [[chord.endAngle|SVG-Shapes#chord_endAngle]]
* [[d3.svg.area|SVG-Shapes#area]]
* [[area.x|SVG-Shapes#area_x]]
* [[area.y0|SVG-Shapes#area_y0]]
* [[area.y1|SVG-Shapes#area_y1]]
* [[area.interpolate|SVG-Shapes#area_interpolate]]
* [[area.tension|SVG-Shapes#area_tension]]
* [[d3.svg.arc|SVG-Shapes#arc]]
* [[arc.innerRadius|SVG-Shapes#arc_innerRadius]]
* [[arc.outerRadius|SVG-Shapes#arc_outerRadius]]
* [[arc.startAngle|SVG-Shapes#arc_startAngle]]
* [[arc.endAngle|SVG-Shapes#arc_endAngle]]
* [[arc.centroid|SVG-Shapes#arc_centroid]]
* [[d3.svg.symbol|SVG-Shapes#symbol]]
* [[symbol.type|SVG-Shapes#symbol_type]]
* [[symbol.size|SVG-Shapes#symbol_size]]

## d3.layout

### [[Force|Layout-Force]]

* [[d3.layout.force|Layout-Force#force]]
* [[force.on|Layout-Force#on]]
* [[force.nodes|Layout-Force#nodes]]
* [[force.links|Layout-Force#links]]
* [[force.size|Layout-Force#size]]
* [[force.distance|Layout-Force#distance]]
* [[force.drag|Layout-Force#drag]]
* [[force.charge|Layout-Force#charge]]
* [[force.gravity|Layout-Force#gravity]]
* [[force.theta|Layout-Force#theta]]
* [[force.start|Layout-Force#start]]
* [[force.resume|Layout-Force#resume]]
* [[force.stop|Layout-Force#stop]]
* [[force.drag|Layout-Force#drag]]

### [[Stack|Layout-Stack]]

* [[d3.layout.stack|Layout-Stack#stack]]
* [[stack.values|Layout-Stack#values]]
* [[stack.order|Layout-Stack#order]]
* [[stack.offset|Layout-Stack#offset]]
* [[stack.x|Layout-Stack#x]]
* [[stack.y|Layout-Stack#y]]
* [[stack.out|Layout-Stack#out]]

### [[Treemap|Layout-Treemap]]

* [[d3.layout.treemap|Layout-Treemap#treemap]]
* [[treemap.sort|Layout-Treemap#sort]]
* [[treemap.children|Layout-Treemap#children]]
* [[treemap.value|Layout-Treemap#value]]
* [[treemap.size|Layout-Treemap#size]]
* [[treemap.round|Layout-Treemap#round]]
* [[treemap.sticky|Layout-Treemap#sticky]]

### [[Tree|Layout-Tree]]

* [[d3.layout.tree|Layout-Tree#tree]]
* [[tree.sort|Layout-Tree#sort]]
* [[tree.children|Layout-Tree#children]]
* [[tree.links|Layout-Tree#links]]
* [[tree.separation|Layout-Tree#separation]]
* [[tree.size|Layout-Tree#size]]

### [[Pie|Layout-Pie]]

* [[d3.layout.pie|Layout-Pie#pie]]
* [[pie.value|Layout-Pie#value]]
* [[pie.sort|Layout-Pie#sort]]
* [[pie.startAngle|Layout-Pie#startAngle]]
* [[pie.endAngle|Layout-Pie#endAngle]]

### [[Partition|Layout-Partition]]

* [[d3.layout.partition|Layout-Partition#partition]]
* [[partition.sort|Layout-Partition#sort]]
* [[partition.children|Layout-Partition#children]]
* [[partition.value|Layout-Partition#value]]
* [[partition.size|Layout-Partition#size]]

### [[Pack|Layout-Pack]]

* [[d3.layout.pack|Layout-Pack#pack]]
* [[pack.sort|Layout-Pack#sort]]
* [[pack.children|Layout-Pack#children]]
* [[pack.value|Layout-Pack#value]]
* [[pack.size|Layout-Pack#size]]

### [[Histogram|Layout-Histogram]]

* [[d3.layout.histogram|Layout-Histogram#histogram]]
* [[histogram.value|Layout-Histogram#value]]
* [[histogram.range|Layout-Histogram#range]]
* [[histogram.bins|Layout-Histogram#bins]]
* [[histogram.frequency|Layout-Histogram#frequency]]

### [[Hierarchy|Layout-Hierarchy]]

* [[d3.layout.hierarchy|Layout-Hierarchy#hierarchy]]
* [[hierarchy.sort|Layout-Hierarchy#sort]]
* [[hierarchy.children|Layout-Hierarchy#children]]
* [[hierarchy.value|Layout-Hierarchy#value]]
* [[hierarchy.revalue|Layout-Hierarchy#revalue]]

### [[Cluster|Layout-Cluster]]

* [[d3.layout.cluster|Layout-Cluster#cluster]]
* [[cluster.sort|Layout-Cluster#sort]]
* [[cluster.children|Layout-Cluster#children]]
* [[cluster.links|Layout-Cluster#links]]
* [[cluster.separation|Layout-Cluster#separation]]
* [[cluster.size|Layout-Cluster#size]]

### [[Chord|Layout-Chord]]

* [[d3.layout.chord|Layout-Chord#chord]]
* [[chord.matrix|Layout-Chord#matrix]]
* [[chord.padding|Layout-Chord#padding]]
* [[chord.sortGroups|Layout-Chord#sortGroups]]
* [[chord.sortSubgroups|Layout-Chord#sortSubgroups]]
* [[chord.sortChords|Layout-Chord#sortChords]]
* [[chord.chords|Layout-Chord#chords]]
* [[chord.groups|Layout-Chord#groups]]

## d3.chart

### [[Box|Chart-Box]]

* [[d3.chart.box|Chart-Box#box]]
* [[box.width|Chart-Box#width]]
* [[box.height|Chart-Box#height]]
* [[box.tickFormat|Chart-Box#tickFormat]]
* [[box.duration|Chart-Box#duration]]
* [[box.domain|Chart-Box#domain]]
* [[box.value|Chart-Box#value]]
* [[box.whiskers|Chart-Box#whiskers]]
* [[box.quartiles|Chart-Box#quartiles]]

### [[Bullet|Chart-Bullet]]

* [[d3.chart.bullet|Chart-Bullet#bullet]]
* [[bullet.orient|Chart-Bullet#orient]]
* [[bullet.ranges|Chart-Bullet#ranges]]
* [[bullet.markers|Chart-Bullet#markers]]
* [[bullet.measures|Chart-Bullet#measures]]
* [[bullet.width|Chart-Bullet#width]]
* [[bullet.height|Chart-Bullet#height]]
* [[bullet.tickFormat|Chart-Bullet#tickFormat]]
* [[bullet.duration|Chart-Bullet#duration]]

### [[QQ|Chart-QQ]]

* [[d3.chart.qq|Chart-QQ#qq]]
* [[qq.width|Chart-QQ#width]]
* [[qq.height|Chart-QQ#height]]
* [[qq.duration|Chart-QQ#duration]]
* [[qq.domain|Chart-QQ#domain]]
* [[qq.count|Chart-QQ#count]]
* [[qq.x|Chart-QQ#x]]
* [[qq.y|Chart-QQ#y]]
* [[qq.tickFormat|Chart-QQ#tickFormat]]

## d3.time

### [[Formatting|Time-Formatting]]

* [[d3.time.format|Time-Formatting#format]]
* [[format.parse|Time-Formatting#parse]]

## d3.behavior

### [[Zoom|Behavior-Zoom]]

* [[d3.behavior.zoom|Behavior-Zoom#zoom]]
* [[zoom.on|Behavior-Zoom#on]]

## d3.csv

### [[CSV]]

* [[d3.csv|CSV#csv]]
* [[d3.csv.parse|CSV#parse]]
* [[d3.csv.parseRows|CSV#parseRows]]
* [[d3.csv.format|CSV#format]]

## d3.geo

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

## d3.geom

### [[Voronoi|Geom-Voronoi]]

* [[d3.geom.voronoi|Geom-Voronoi#voronoi]]
* [[d3.geom.delaunay|Geom-Voronoi#delaunay]]

### [[Quadtree|Geom-Quadtree]]

* [[d3.geom.quadtree|Geom-Quadtree#quadtree]]
* [[quadtree.visit|Geom-Quadtree#visit]]

### [[Polygon|Geom-Polygon]]

* [[d3.geom.polygon|Geom-Polygon#polygon]]
* [[polygon.area|Geom-Polygon#area]]
* [[polygon.centroid|Geom-Polygon#centroid]]
* [[polygon.clip|Geom-Polygon#clip]]

### [[Hull|Geom-Hull]]

* [[d3.geom.hull|Geom-Hull#hull]]

### [[Contour|Geom-Contour]]

* [[d3.geom.contour|Geom-Contour#contour]]
