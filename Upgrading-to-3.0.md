D3 3.0 is the first major release since 2.0 was released last August. Since 2.0.0, there have been 10 minor releases and 37 patch releases. 3.0 includes significant new features and improvements, but in accordance with [semantic versioning](http://semver.org/), this major release also includes several backwards incompatibilities. This document guides you on how to upgrade from 2.x to 3.0.

## Requests

If your visualization loads external data via [d3.xhr](Requests), you’ll need to change your callback function. In 2.x, you would have written code like this:

```js
d3.json("my-data.json", function(data) {
  console.log("there are " + data.length + " elements in my dataset");
});
```

**In 3.0, the callback function now takes an additional argument, `error`.** If an error occurs fetching the requested resource, the error argument will contain information that you can use to diagnose the problem or inform the user, such as whether the file is missing or the server is unavailable. The second argument contains the contents of the resource, as before. The simplest fix is therefore to add "error, ":

```js
d3.json("my-data.json", function(error, data) {
  console.log("there are " + data.length + " elements in my dataset");
});
```

You might prefer to handle errors, too:

```js
d3.json("my-data.json", function(error, data) {
  if (error) return console.log("there was an error loading the data: " + error);
  console.log("there are " + data.length + " elements in my dataset");
});
```

The reason for this change is two-fold. First, it adopts the standard {error, result} asynchronous callback convention established by Node.js which makes it familiar to JavaScript developers. Better yet, it means you can use helpers for asynchronous JavaScript, such as [Queue.js](https://github.com/mbostock/queue). For example, say you wanted to load two resources for a map visualization, a GeoJSON file "us-states.json" and a data file "us-state-populations.tsv". In 2.x, you probably would have loaded these serially by nesting callbacks:

```js
d3.json("us-states.json", function(states) {
  d3.tsv("us-state-populations.tsv", function(statePopulations) {
    // display map here
  });
});
```

Loading resources serially is slow! It's better to parallelize those requests, which is now easy:

```js
queue()
    .defer(d3.json, "us-states.json")
    .defer(d3.tsv, "us-state-populations.tsv")
    .await(ready);

function ready(error, states, statePopulations) {
  // display map here
}
```

The last reason this change was made is to make it more obvious that these requests can fall. That first argument, error, is a nagging reminder that you might want to handle errors when loading resources by displaying a suitable notification to your users or retrying the request. It also means you can now distinguish between a successfully-loaded JSON file that contains `null` and an error.

There are a number of other backwards-compatible improvements to d3.xhr, such as the ability to listen for [progress events](http://bl.ocks.org/3750941) and set request headers. See the [API reference](Requests) for details.

## Transitions

D3’s transition subsystem has been significantly overhauled for 3.0 to make it easier to construct complex sequences of transitions. You’re not likely to notice these changes unless you’re using transitions extensively. And if you are, I highly recommend reading [Working with Transitions](http://bost.ocks.org/mike/transition/).

The first change is that **[transition.attr](Transitions#wiki-attr), [transition.style](Transitions#wiki-style) and [transition.text](Transitions#wiki-text) now evaluate their property functions immediately**. This makes them behave just like their selection equivalents. However, in 2.x, these functions were evaluated asynchronously when the transition started! For example, consider the following code:

```js
// First transition the line to the new data.
line.datum(newData).transition().attr("d", line);
    
// Then transition the y-axis.
y.domain(newDomain);
line.transition().delay(250).attr("d", line);
```

You might expect this code to first transition the line to the new data, and then transition to the new domain. In 2.x, however, this would not work because the first transition.attr would not be evaluated until *after* the y-scale’s domain changes. ([WAT!](https://www.destroyallsoftware.com/talks/wat)) While deferred evaluation is occasionally what you want, immediate evaluation is much easier to understand and debug, so that’s what transitions do in 3.0. This means you can now easily specify transitions that depend on external state, as in the above example showing [chained transitions of data and axes](http://bl.ocks.org/3903818).

The other big change is that **[transition.select](Transitions#wiki-select) and [transition.selectAll](Transitions#wiki-selectAll) now reselect existing transitions** rather than creating new transitions. This means that you can start a transition on a set of elements—say an axis—and then reselect a subset of those elements to customize the transition. In 2.x, transition.select would create a new transition that would conflict with the existing transition. Like selections, transitions in 3.0 and now stored entirely in the DOM, and thus can be reselected.

Related to reselect, **[transition.transition](Transitions#wiki-transition) now creates a new transition that is scheduled to start when the originating transition ends**. This makes it very easy to create chained transitions, say from [stacked to grouped bars](http://bl.ocks.org/3943967), without the hassle of listening for "end" events.

## Geo

D3 3.0 includes a fantastic new geographic projection system featuring [three-axis rotation](http://bl.ocks.org/3734273), [antemeridian cutting](http://bl.ocks.org/3788999) and [adaptive supersampling](http://bl.ocks.org/3795544). (And there’s also [TopoJSON](https://github.com/mbostock/topojson) for more efficient representation of geometry.) These changes are mostly backwards-compatible, but one gotcha you might encounter is that **d3.geo.path now observes the right-hand rule for polygons**. Geographic features are defined in spherical coordinates. Thus, given a small polygon that approximates a circle, we might assume that this polygon represents an island. However, an equally valid interpretation is that this polygon represents everything *but* the island; that is, the polygon of the sea surrounding the island. In 2.x, it was not possible to represent polygons that were larger than a hemisphere. By applying the right-hand rule, sub-hemisphere polygons in 3.0 must have clockwise winding order. In your GeoJSON input has polygons in the wrong order, you’ll need to reverse them; you can also convert your GeoJSON to [TopoJSON](/mbostock/topojson), and this will happen automatically.

There is now a wide variety of geographic projections available for D3 3.0 in the [d3.geo.projection plugin](/d3/d3-plugins/tree/master/geo/projection). Correspondingly, **the rarely-used Bonne projection has been moved from the core library to the plugin**, and **the d3.geo.azimuthal projection has also been replaced with separate projections for each mode**: d3.geo.orthographic, d3.geo.azimuthalEqualArea, d3.geo.azimuthalEquidistant, d3.geo.stereographic and d3.geo.gnomonic. **The albers.origin method has also been replaced by the generic projection.rotate and projection.center methods.**

Lastly, **the alias d3.geo.greatCircle has been removed**; use d3.geo.circle instead. Also, did you know that you can now use d3.geo.circle to draw circles? This is an easy way to approximate [Tissot’s indicatrix](http://bl.ocks.org/4052873).

## Why These Changes Were Made

Most changes to D3 are carefully designed to be backwards-compatible, which makes it easier to upgrade. If you’ve been linking to the official [d3.v2.js](http://d3js.org/d3.v2.js), you’ve been getting bug fixes, performance improvements, and new features automatically. Unfortunately, not all changes can be made backwards-compatible; periodically, these potentially disruptive changes are needed to keep the API and the code lean by removing deprecated, broken or confusing functionality.