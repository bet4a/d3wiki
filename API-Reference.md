Everything in D3 is scoped under the `d3` namespace. D3 is broken up into several modules so that you can pick and choose which features you need and minimize the weight. The default build of `d3.js` includes the *core*, *scale* and *svg* modules, at about 12KB uglified and gzipped. However, you can edit the [[Makefile|https://github.com/mbostock/d3/blob/master/Makefile]] to produce a custom build that suites your needs. D3 does not introduce anything else in the global namespace. However, for nonstandard browsers we do register polyfills for [[Date.now|https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Date/now]] and [[Object.create|https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object/create]].

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
* [[d3.ns|Selections#d3_ns]] - access or extend known XML namespaces.
* [[d3.functor|Selections#d3_functor]] - create a function that returns a constant.

### [[Transitions]]

* [[d3.transition|Transitions#d3_transition]] - start an animated transition.
* [[d3.ease|Transitions#d3_ease]] - customize transition timing.
* [[d3.interpolate|Transitions#d3_interpolate]] - interpolate two values.
* [[d3.interpolateNumber|Transitions#d3_interpolateNumber]] - interpolate two numbers.
* [[d3.interpolateRound|Transitions#d3_interpolateRound]] - interpolate two integers.
* [[d3.interpolateString|Transitions#d3_interpolateString]] - interpolate two strings.
* [[d3.interpolateRgb|Transitions#d3_interpolateRgb]] - interpolate two RGB colors.
* [[d3.interpolateHsl|Transitions#d3_interpolateHsl]] - interpolate two HSL colors.
* [[d3.interpolateArray|Transitions#d3_interpolateArray]] - interpolate two arrays of values.
* [[d3.interpolateObject|Transitions#d3_interpolateObject]] - interpolate two arbitrary objects.

### Events

* [[d3.dispatch|Events#d3_dispatch]] - create a custom event dispatcher.
* [[d3.event|Events#d3_event]] - access the current user event for interaction.

### Working with Arrays

* [[d3.ascending|Arrays#d3_ascending]] - compare two values for sorting.
* [[d3.descending|Arrays#d3_descending]] - compare two values for sorting.
* [[d3.min|Arrays#d3_min]] - find the minimum value in an array.
* [[d3.max|Arrays#d3_max]] - find the maximum value in an array.
* [[d3.keys|Arrays#d3_keys]] - list the keys of an associative array.
* [[d3.values|Arrays#d3_values]] - list the values of an associated array.
* [[d3.entries|Arrays#d3_entries]] - list the key-value entries of an associative array.
* [[d3.split|Arrays#d3_split]] - split an array into multiple arrays.
* [[d3.merge|Arrays#d3_merge]] - merge multiple arrays into one array.
* [[d3.range|Arrays#d3_range]] - generate a range of numeric values.
* [[d3.nest|Arrays#d3_nest]] - group array elements hierarchically.

### Loading External Resources

* [[d3.xhr|Resources#d3_xhr]] - load a resource using `XMLHttpRequest`.
* [[d3.text|Resources#d3_text]] - load a text file.
* [[d3.json|Resources#d3_json]] - load a JSON blob.
* [[d3.html|Resources#d3_html]] - load an HTML document fragment.
* [[d3.xml|Resources#d3_xml]] - load an XML document fragment.

Also see the `csv` module.

### Number Formatting

* d3.format

### Colors

* d3.rgb
* d3.hsl

## d3.behavior

## d3.chart

## d3.csv

## d3.geo

## d3.geom

## d3.layout

## d3.scale

## d3.svg

## d3.time
