D3 3.0 is the first major release since 2.0 was released last August. Since 2.0.0, there have been 10 minor releases and 37 patch releases. 3.0 includes significant new features and improvements, but in accordance with [semantic versioning](http://semver.org/), this rare major release also includes several backwards incompatibilities. Major releases are needed to keep the API and the code lean by removing deprecated, broken or confusing functionality. This document guides you on how to upgrade from 2.x to 3.0.

## How to Upgrade

If you’re using the official hosted copy of D3, simply **replace d3.v2.min.js with d3.v3.min.js** in your script tag, like this:

```html
<script src="http://d3js.org/d3.v3.min.js"></script>
```

(There’s also a [d3.v3.js](http://d3js.org/d3.v3.js) for development.) Also, check that you have the DOCTYPE and charset set correctly on your HTML page:

```html
<!DOCTYPE html>
<meta charset="utf-8">
```

If you’d prefer to host your own copy of D3, download the [zipball](https://github.com/mbostock/d3/archive/3.0.zip) or clone the repository and pull out the contained d3.js and d3.min.js. Don’t copy-and-paste the JavaScript contents from your browser; that can corrupt UTF-8 characters.

## Requests

If you load external data via [d3.xhr](Requests), **change your callback function to take an additional `error` argument.** If an error occurs loading the resource, you can use the error argument to diagnose the problem, to retry, or to inform the user. Examples of errors include network issues (such as being offline), or missing files (404) or unavailable servers (503). This change makes it more obvious that requests can fall; the error argument is a nagging reminder that you should consider errors when loading resources. (It also means you can now distinguish between a successfully-loaded JSON file that contains `null` and an error.)

In 2.x, you might have written this:

```js
d3.json("my-data.json", function(data) {
  console.log("there are " + data.length + " elements in my dataset");
});
```

The equivalent 3.0 code looks like this:

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

This change adopts the standard {error, result} asynchronous callback convention established by Node.js which makes it familiar to JavaScript developers. Better yet, it means you can now use helpers for asynchronous JavaScript, such as [Queue.js](https://github.com/mbostock/queue). For example, if you wanted to load multiple resources in 2.x, you probably would have loaded them serially by nesting callbacks:

```js
d3.json("us-states.json", function(states) {
  d3.tsv("us-state-populations.tsv", function(statePopulations) {
    // display map here
  });
});
```

Loading resources serially is slow because it doesn’t maximize the user’s network connection. (Also, if one of the above requests fails, subsequent serialized requests will still continue because the error is ignored. This is likely wasteful.) It's better to parallelize those requests. You can do that manually in vanilla JavaScript, but it’s a pain since you need to track the number of outstanding requests to determine when all resources are available. It’s much easier to use Queue.js with 3.0:

```js
queue()
    .defer(d3.json, "us-states.json")
    .defer(d3.tsv, "us-state-populations.tsv")
    .await(ready);

function ready(error, states, statePopulations) {
  // display map here
}
```

There are a number of other (backwards-compatible) improvements to d3.xhr, such as the ability to listen for [progress events](http://bl.ocks.org/3750941) and set request headers. See the [API reference](Requests) for details.

## Transitions

D3’s transition subsystem has been significantly overhauled for 3.0 to make it easier to construct complex sequences of transitions. If you’re using transitions extensively, I also recommend reading [Working with Transitions](http://bost.ocks.org/mike/transition/).

The first change is that **[transition.attr](Transitions#wiki-attr), [transition.style](Transitions#wiki-style) and [transition.text](Transitions#wiki-text) now evaluate their property functions immediately**. In 2.x, these functions were evaluated asynchronously when the transition started, which was frequently confusing! Consider the following code:

```js
// First transition the line to the new data.
line.datum(newData).transition().attr("d", line);
    
// Then transition the y-axis.
y.domain(newDomain);
line.transition().delay(250).attr("d", line);
```

You might expect this code to first transition the line to the new data, and then transition to the new domain. In 2.x, however, this would not work because the first transition.attr would be evaluated *after* the y-scale’s domain changes. While deferred evaluation is occasionally what you want, immediate evaluation is much easier to understand and debug, so that’s what transitions do in 3.0. (The selection.attr, selection.style, and related methods have always used immediate evaluation for this reason.) This means you can now easily specify transitions that depend on external state, as in the above example showing [chained transitions of data and axes](http://bl.ocks.org/3903818). You can also create transitions within for loops without worrying about the dreaded [closures in loops problem](http://www.mennovanslooten.nl/blog/post/62).

The other big change is that **[transition.select](Transitions#wiki-select) and [transition.selectAll](Transitions#wiki-selectAll) now reselect existing transitions** rather than creating new transitions. This means that you can start a transition on a set of elements—say an axis—and then reselect a subset of those elements to customize the transition. This technique of customizing axes is called _postselection_, and in 3.0 you can use it for transitions as well as selections. For example, if you want to override the text-anchor for axis labels:

```js
svg.select(".x.axis").transition()
    .call(xAxis)
  .selectAll("text")
    .style("text-anchor", "start");
```

In 2.x, transition.select and transition.selectAll would create a new transition that would conflict with the existing transition. Like selections, transitions in 3.0 and now stored entirely in the DOM, and thus can be reselected. Related to this, **[transition.transition](Transitions#wiki-transition) now creates a new transition that is scheduled to start when the originating transition ends**. This makes it very easy to create chained transitions, say from [stacked to grouped bars](http://bl.ocks.org/3943967), without the hassle of listening for "end" events.

```js
rect.transition()
    .duration(500)
    .delay(function(d, i) { return i * 10; })
    .attr("x", function(d, i, j) { return x(d.x) + x.rangeBand() / n * j; })
    .attr("width", x.rangeBand() / n)
  .transition()
    .attr("y", function(d) { return y(d.y); })
    .attr("height", function(d) { return height - y(d.y); });
```

The rarely-used **d3.tween method has been removed**. This previously provided a way to override the interpolator used during a transition. Use transition.attrTween, transition.styleTween or transition.tween instead.

## Geo

D3 3.0 includes a fantastic new geographic projection system featuring [three-axis rotation](http://bl.ocks.org/3734273), [antemeridian cutting](http://bl.ocks.org/3788999) and [adaptive supersampling](http://bl.ocks.org/3795544). (And there’s also [TopoJSON](https://github.com/mbostock/topojson) for more efficient representation of geometry.) These changes are almost entirely backwards-compatible.

One gotcha you might encounter is that **d3.geo.path now observes the right-hand rule for polygons**. Geographic features are defined in spherical coordinates. Thus, given a small polygon that approximates a circle, we might assume that this polygon represents an island. However, an equally valid interpretation is that this polygon represents everything *but* the island; that is, the polygon of the sea surrounding the island. (See Jason’s [Geographic Clipping page](http://www.jasondavies.com/maps/clip/) for a variety of interesting examples.) In 2.x, it was not possible to represent polygons that were larger than a hemisphere. By applying the right-hand rule, sub-hemisphere polygons in 3.0 must have clockwise winding order. In your GeoJSON input has polygons in the wrong order, you’ll need to reverse them; you can also convert your GeoJSON to [TopoJSON](/mbostock/topojson), and this will happen automatically.

There is now a wide variety of geographic projections available for D3 3.0 in the [d3.geo.projection plugin](/d3/d3-plugins/tree/master/geo/projection). Correspondingly, **the rarely-used Bonne projection has been moved from the core library to the plugin**, and **the d3.geo.azimuthal projection has also been replaced with separate projections for each mode**: d3.geo.orthographic, d3.geo.azimuthalEqualArea, d3.geo.azimuthalEquidistant, d3.geo.stereographic and d3.geo.gnomonic. **The albers.origin method has also been replaced by the generic projection.rotate and projection.center methods.**

Lastly, **the alias d3.geo.greatCircle has been removed**; use d3.geo.circle instead. Also, did you know that you can now use d3.geo.circle to draw circles? This is an easy way to approximate [Tissot’s indicatrix](http://bl.ocks.org/4052873).

## Arrays

* Removed d3.{first,last}.
* Removed d3.split.

## Geom

* Moved d3.geom.contour to d3-plugins.
* Removed [x, y] input support for d3.geom.quadtree; use {x: x, y: y} instead.

## SVG

* Removed aliases d3.svg.{mouse,touches}; use d3.{mouse,touches} instead.

## Other Miscellany

* the main library is called d3.js in the repo, but still d3.v3.js on d3js.org
* examples are now hosted on bl.ocks.org, rather than the git repo
* d3.js should be served with utf-8; not a new feature, but important