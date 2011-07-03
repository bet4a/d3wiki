> [[API Reference]] ▸ [[Layouts]]

The stack layout takes a two-dimensional array of data and computes a baseline; the baseline is then propagated to the above layers, so as to produce a stacked graph. Several baseline algorithms are supported, along with sorting heuristics to improve perception, as described in [“Stacked Graphs—Geometry & Aesthetics”](http://www.leebyron.com/else/streamgraph/download.php?file=stackedgraphs_byron_wattenberg.pdf) by Byron & Wattenberg.

![stack](stack.png)

The stack layout operates in an arbitrary two-dimensional *x* and *y* coordinate space, as with other layouts, including [tree](Tree-Layout). Thus, layers can be stacked vertically, horizontally, or even [radially](http://hint.fm/projects/flickr/). While the "zero" offset is the default, a streamgraph can be generated using the "wiggle" offset, which attempts to minimize change in slope weighted by layer thickness.

In the simplest case, the layer data can be specified as a two-dimensional array of numbers. The *y* and *x* accessors are used to define the thickness of each layer at the given position, respectively. With the exception of the "expand" offset, the stack layout does not perform any automatic scaling of data. To simplify scaling, use this layout in conjunction with a [linear scale](Quantitative-Scales#linear) or similar. The stack layout currently requires that the layers are homogenous: each must contain the same number of values at the same *x*-coordinates. If your data is not so regular, you will need to reinterpolate the data before computing the stack.

<a name="stack" href="#stack">#</a> d3.layout.<b>stack</b>()

Construct a new default layout.

<a name="_stack" href="#_stack">#</a> <b>stack</b>(<i>layers</i>[, <i>index</i>])

Compute the *y*-coordinate baseline for each series (layer) in *layers*, and then propagate that baseline to the other layers.

<a name="values" href="#values">#</a> stack.<b>values</b>([<i>accessor</i>])

Specifies how to extract values from the associated element in *layers*; *accessor* is a function which is invoked on each input layer passed to [stack](#_stack), equivalent to calling *layers.map(accessor)* before computing the stack layout. The default values function is the built-in [Object](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object), which is similar to the identity function. If *accessor* is not specified, returns the current values accessor.

<a name="offset" href="#offset">#</a> stack.<b>offset</b>([<i>offset</i>])

If *offset* is specified, sets the stack offset algorithm to the specified value. If *offset* is not specified, returns the current offset algorithm. The following string values are supported:

* silhouette -
* wiggle -
* expand -
* zero -

In addition to a string, *offset* may be specified as a function. The input to the offset function is the layer data, converted to a standardized representation: a two-dimensional array of values, where each value is represented as a two-element array [*x*, *y*]. The return value of the offset function must be an array of values which represents the *y*-coordinates of the baseline. For example, the default "zero" offset is implemented as:

```javascript
function offset(data) {
  var j = -1,
      m = data[0].length,
      y0 = [];
  while (++j < m) y0[j] = 0;
  return y0;
}
```

<a name="order" href="#order">#</a> stack.<b>order</b>([<i>order</i>])

If *order* is specified, sets the stack order to the specified value. If *order* is not specified, returns the current order. The following string values are supported:

* inside-out - 
* reverse -
* default -

In addition to a string, *order* may be specified as a function. The input to the order function is the layer data, converted to the standardized representation: a two-dimensional array of values, where each value is represented as a two-element array [*x*, *y*]. The return value of the order function must be an array of indexes which represents the layer order. For example, the default order is implemented as:

```javascript
function order(data) {
  return d3.range(data.length);
}
```

See also [d3.range](Arrays#d3_range).

<a name="x" href="#x">#</a> stack.<b>x</b>([<i>x</i>])

```javascript
function x(d) {
  return d.x;
}
```

<a name="y" href="#y">#</a> stack.<b>y</b>([<i>y</i>])

```javascript
function y(d) {
  return d.y;
}
```

<a name="out" href="#out">#</a> stack.<b>out</b>([<i>out</i>])

```javascript
function out(d, y0, y) {
  d.y0 = y0;
  d.y = y;
}
```
