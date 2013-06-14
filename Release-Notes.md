> [Wiki](Home) ▸ **Release Notes**

Patch versions always include various bug fixes; see the full compare for details. For major and minor versions, new features are listed below.

## 3.2.0 - June 13, 2013

* Added d3.dsv to support generic delimiter-separated values (e.g., "|") beyond TSV & CSV.
* Added [selection.size](https://github.com/mbostock/d3/wiki/Selections#wiki-size) to count the number of selected elements.
* Added d3.xhr [responseType](https://github.com/mbostock/d3/wiki/Requests#wiki-responseType).
* Added d3.geom.quadtree [extent](https://github.com/mbostock/d3/wiki/Quadtree-Geom#wiki-extent) (deprecates size).
* Added d3.geom.voronoi [clipExtent](https://github.com/mbostock/d3/wiki/Voronoi-Geom#wiki-clipExtent) (deprecates size).
* Added d3.layout.{[tree](https://github.com/mbostock/d3/wiki/Tree-Layout#wiki-nodeSize),[cluster](https://github.com/mbostock/d3/wiki/Cluster-Layout#wiki-nodeSize)} [nodeSize](https://github.com/mbostock/d3/wiki/Tree-Layout#wiki-nodeSize) for fixed-size nodes.
* Added d3.layout.pack radius for explicit control of circle radius.
* Added *m* argument to d3.scale.{[pow](https://github.com/mbostock/d3/wiki/Quantitative-Scales#wiki-pow),[linear](https://github.com/mbostock/d3/wiki/Quantitative-Scales#wiki-linear)} [nice](https://github.com/mbostock/d3/wiki/Quantitative-Scales#wiki-linear_nice); controls nicing precision.
* Added d3.scale.{[threshold](https://github.com/mbostock/d3/wiki/Quantitative-Scales#wiki-threshold_invertExtent),[quantize](https://github.com/mbostock/d3/wiki/Quantitative-Scales#wiki-quantize_invertExtent)} [invertExtent](https://github.com/mbostock/d3/wiki/Quantitative-Scales#wiki-threshold_invertExtent) function.
* Added "step" interpolation to [d3.svg.line](https://github.com/mbostock/d3/wiki/SVG-Shapes#wiki-line_interpolate) and [d3.svg.area](https://github.com/mbostock/d3/wiki/SVG-Shapes#wiki-area_interpolate).
* Added d3.svg.brush [clamp](https://github.com/mbostock/d3/wiki/SVG-Controls#wiki-brush_clamp) to control extent clamping.
* Added support for parsing day-of-year, week-of-year, etc. in [d3.time.format](https://github.com/mbostock/d3/wiki/Time-Formatting).
* d3.xhr now uses XMLHttpRequest rather than XDomainRequest in IE10 for cross-origin requests.
* More accurate [d3.geo.area](https://github.com/mbostock/d3/wiki/Geo-Paths#wiki-d3_geo_area) implementation.
* Improved [d3.geo.centroid](https://github.com/mbostock/d3/wiki/Geo-Paths#wiki-d3_geo_centroid) implementation; now supports zero-extent features.
* Improved accuracy of geographic clipping and detection of polygon winding order.
* Fixed bug with missing selection.[call](https://github.com/mbostock/d3/wiki/Selections#wiki-enter) on enter selections.
* Fixed bug with [d3.mouse](https://github.com/mbostock/d3/wiki/Selections#wiki-d3_mouse) when default stylesheets apply padding, margin or borders.
* Fixed bug with [d3.behavior.zoom](https://github.com/mbostock/d3/wiki/Zoom-Behavior) and [d3.behavior.drag](https://github.com/mbostock/d3/wiki/Drag-Behavior) in regards to canceling mousedown.
* Fixed bug with [d3.geom.voronoi](https://github.com/mbostock/d3/wiki/Voronoi-Geom) and custom accessors.
* Fixed bug with [d3.layout.pack](https://github.com/mbostock/d3/wiki/Pack-Layout) with small-radius circles.
* Fixed bug with d3.scale.log [tickFormat](https://github.com/mbostock/d3/wiki/Quantitative-Scales#wiki-log_tickFormat); now accepts a string as the *format* argument.
* Fixed bug with [time intervals](https://github.com/mbostock/d3/wiki/Time-Intervals) in Firefox when using British Summer Time.

## 3.1.0 - March 21, 2013

See the [full 3.1 release notes](3.1) for details.

* Custom builds of D3 using [SMASH](https://github.com/mbostock/smash).
* Various [d3.geo](https://github.com/mbostock/d3/wiki/Geo) improvements, including viewport clipping and a better graticule.
* Polyfills for "mouseenter" and "mouseleave" events.
* Easier formatting and type conversion for [d3.csv](https://github.com/mbostock/d3/wiki/CSV#wiki-csv) and [d3.tsv](https://github.com/mbostock/d3/wiki/CSV#wiki-tsv).
* Configurable [base](https://github.com/mbostock/d3/wiki/Quantitative-Scales#wiki-log_base) on [log scales](https://github.com/mbostock/d3/wiki/Quantitative-Scales#wiki-log).
* New [d3.set](https://github.com/mbostock/d3/wiki/Arrays#wiki-d3_set) class (ES6 shim).
* Refactored [d3.geom](https://github.com/mbostock/d3/wiki/Geometry) to be more like [d3.layout](https://github.com/mbostock/d3/wiki/Layouts).

## 3.0.0 - December 21, 2012

Major release! See the [full 3.0 release notes](3.0) for all the details!

* d3.geo - dramatically better geographic projection system!
* d3.transition - easier sequenced transitions and easier debugging.
* d3.xhr - more customizable requests, including progress events and custom methods.
* Various bug fixes and performance improvements.

See [[Upgrading to 3.0]] for detailed information on how to migrate from 2.x to 3.0.

## 2.10.0 - August 9, 2012

* Added [multi-valued map](http://bl.ocks.org/3305515) support for selection.attr and similar methods.
* Added [L\*a\*b\* and HCL](http://bl.ocks.org/3014589) color spaces.
* Added [d3.tween](http://bl.ocks.org/3305854) for easier customization of transition interpolators.
* Added [d3.tsv](http://bl.ocks.org/3305937) for loading tab-separated values.
* Added static [localization for d3.time.format](http://bl.ocks.org/3306234), including fr_FR and ru_RU locales.
* Added a new quantitative scale: [d3.scale.threshold](http://bl.ocks.org/3306362).
* Added [outer padding](http://bl.ocks.org/3310560) support for d3.scale.ordinal’s rangeBands.
* Added [d3.layout.pack padding](http://bl.ocks.org/3007180) support.
* [Custom interpolators](http://bl.ocks.org/3310323) can now be used with d3.svg.line and d3.svg.area.
* Added new random generators for [log-normal](http://bl.ocks.org/3048166) and [Irwin–Hall](http://bl.ocks.org/3048450) distributions.
* Improved [d3.time.scale’s nice](http://bl.ocks.org/3306147).
* Fixed incorrect tangents with [monotone interpolation](http://bl.ocks.org/3310233).
* Simplified [transform interpolation](http://bl.ocks.org/3173784).

## 2.9.0 - April 15, 2012

* Added `defined` methods to d3.svg.line and d3.svg.area.

## 2.8.0 - February 24, 2012

* Added the selection.datum operator (deprecating selection.map), which is like selection.data but doesn't compute a data-join; it can be used to get or set the data bound to elements.
* Brush component can now take decorative resizers.
* Added d3.map class (similar to ES6's map collection) for easier management of string-value maps; this is used internally by transitions, event listeners, the nest operator, and many other components.
* Added d3.bisector for bisecting sorted arrays with an accessor.
* Exposed d3.selection.enter.prototype.
* Generalized d3.svg.mouse to support HTML elements, and renamed to d3.mouse.
* Added d3.scale.identity.
* Added axis.tickValues.
* Rewrite of d3.behavior.zoom.
* Added "start" and "end" events to force layout, along with force.tick and force.alpha for synchronous execution.
* Added a variety of new time interval methods.

## 2.7.0 - December 8, 2011

The filter method can now take a selector, such as filter(".foo"). A new order() method reorders document elements to match selection order; this is faster than sort() if your data is already in-order.

## 2.6.0 - November 23, 2011

Namespaces are now optional (in most cases)! Ordinal scale support for axes and brushes. Drag behavior supports configurable origin. Dispatchers can be used to access current listeners.

## 2.5.0 - November 04, 2011

Brush component. 2D transform transitions. Namespaced events for d3.dispatch. Extended ISO 8601. Extents for zoom behavior. Array extents.

## 2.4.0 - October 10, 2011

SI-prefix ("r") format. Multiple classes for the classed operator. Mean and median.

## 2.3.0 - September 27, 2011

Azimuthal and Bonne projections. Great arcs and great circle clipping. Variable log ticks.

## 2.2.0 - September 17, 2011

Equirectangular projection. Variable-strength charge for force layouts.

## 2.1.0 - August 29, 2011

Subtransitions (transition.transition). Great circles.

## 2.0.0 - August 23, 2011

### Enter and Update

The **enter-update** pattern has been simplified: the [enter](Selections#wiki-wiki-enter) selection now merges into the [update](Selections#wiki-wiki-data) selection when you append or insert. This new approach reduces code duplication between enter and update. Rather than applying operators to both the enter and update selection separately, you can now apply them to the update selection after entering the nodes.

For example, say you had a selection of circles and wanted to update their radii. Previously you had to call the [attr](Selections#wiki-wiki-attr) operator twice, once for enter and once for update:

```javascript
var circle = svg.selectAll("circle").data([data]);
circle.exit().remove();
circle.enter().append("svg:circle").attr("r", radius); // for enter
circle.attr("r", radius); // for update
```

In addition, if you wanted *circle* to refer to all the on-screen nodes (enter ∪ update) subsequently, you'd have to reselect as well to merge the enter and update selections:

```javascript
circle = svg.selectAll("circle"); // reselect
```

In 2.0.0, you can eliminate this duplicate code because entering nodes will add them to *both* the enter selection and the update selection simultaneously. Running operators on the update selection after enter will thus apply to both entering and updating nodes:

```javascript
var circle = svg.selectAll("circle").data([data]);
circle.exit().remove();
circle.enter().append("svg:circle"); // adds enter to update
circle.attr("r", radius); // for enter and update
```

Note: in the rare case that you want to run operators only on the updating nodes, you can run them on the update selection before entering new nodes. If you want to run operators only on the entering nodes, you can still do that (as before) by applying them to the enter selection.

### Selector Functions

The [select](Selections#wiki-wiki-select) and [selectAll](Selections#wiki-wiki-selectAll) operators can now take **selector functions**, in addition to selector strings such as "#id" and ".class". For example, if you want to select the first child of every element, you can now say:

```javascript
var children = g.select(function() { return this.firstChild; });
```

This also means that selection can dynamically create new elements, or reorder existing elements by re-inserting them into the DOM. This is an advanced feature, but you might find it useful for extending D3. For example, you could use XPath rather than selectors if you wanted.

### Transparent Transitions

Transitions are now **transparent** arrays of elements, and you can inspect them in the developer console just like selections. Each selected element is wrapped in an object that stores the delay and duration of the associated transition. (Recall that these values are computed on a per-element basis for staggered animations.) Internally, some of the timing logic that manages transitions has also been simplified, improving performance and fixing a few timing bugs.

The [each](Transitions#wiki-wiki-each) operator can now be called with one argument (a callback function), offering compatibility with the selection's [each](Selections#wiki-wiki-each) operator. Transitions now expose an [id](Transitions#wiki-wiki-id) property, which can be useful for debugging concurrent transitions; this identifier is inherited by subtransitions, fixing a bug with nested transitions.

**Sequenced** transitions are now also easier to implement, thanks to the transition's [transition](Transitions#wiki-transition) operator, which returns a copy of the current transition. The copy inherits the delay, duration, id and easing of the original transition. You can then modify the delay to sequence multiple transitions, without needing to listen for the "end" event. For example, here's how you would enter a circle, and then remove it after a couple seconds:

```javascript
svg.append("svg:circle")
    .attr("r", 1e-6)
  .transition()
    .ease(Math.sqrt)
    .attr("r", 4.5)
  .transition()
    .delay(2000)
    .attr("r", 1e-6)
    .remove();
```

You can also use this technique to use different easing functions for different tweens! For example, you could use "cubic-in-out" easing for position properties, and "linear" for color.

### Custom Tweens

A new, generic [tween](Transitions#wiki-wiki-tween) operator has been added, which is used internally by the other tweens (`style`, `attr`, *etc.*). You can use this operator directly if you want to define a custom tween as part of the transition; use this instead of listening for a transition "tick" event. For example, the `text` operator does not interpolate by default, but you can now interpolate text content by saying:

```javascript
selection.transition().tween("text", function() {
  var i = d3.interpolate(this.textContent, "yellow");
  return function(t) {
    this.textContent = i(t);
  };
});
```

You might want to write your tweens as reusable functions (say, closures) rather than the above example which hard-codes the transition to "yellow". See the built-in attr and style tweens for inspiration.

### Axes

A new **axis** component has been added to the [d3.svg](SVG-Shapes) module. The axis component makes it easy to add reference lines, ticks and labels to any visualization. This display of the axes is highly customizable, and best of all, the axes support smooth transitions automatically. See this [quick demo](http://bl.ocks.org/1166403) of axes used by an area chart. More documentation and examples for this component will be coming in the next few days.

### Extending and Overriding

Selection and transition are now defined using [prototype injection](http://perfectionkills.com/how-ecmascript-5-still-does-not-allow-to-subclass-an-array/) rather than direct extension. This improves performance and reduces memory overhead, as the majority of methods are now defined on a prototype rather than on each instance. Also, this makes the code cleaner as each operator is fully separable and defined in its own source file. This fixed a few bugs, such as the missing [empty](Selections#wiki-wiki-empty) operator on enter selections.

Prototype injection also means that selections and transitions can be extended and customized! You can now override the behavior of D3's core operators, or add your own. This may be particularly useful to provide compatibility with nonstandard browsers, or proprietary document object models. You can also use JavaScript's `instanceof` operator to see whether an object is a `d3.selection` or `d3.transition`.

### Tests

D3 now has an extensive test suite built with [Vows](http://vowsjs.org). As of the 2.0.0 release, we have 1,200+ tests and 90% coverage of the core library. More tests are under development. The tests are written to verify the behavior of each of D3's operators, and may be interesting to explore if you have questions about how D3 works, complementing the API reference.
