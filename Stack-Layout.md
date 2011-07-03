> [[API Reference]] ▸ [[Layouts]]

The stack layout takes a two-dimensional array of data and computes a baseline; the baseline is then propagated to the above layers, so as to produce a stacked graph. Several baseline algorithms are supported, along with sorting heuristics to improve perception, as described in [“Stacked Graphs – Geometry & Aesthetics”](http://www.leebyron.com/else/streamgraph/download.php?file=stackedgraphs_byron_wattenberg.pdf) by Byron & Wattenberg.

![stack](stack.png)

The stack layout operates in an arbitrary two-dimensional *x* and *y* coordinate space, as with other layouts, including [tree](Tree-Layout). Thus, layers can be stacked vertically, horizontally, or even [radially](http://hint.fm/projects/flickr/). While the "zero" offset is the default, a streamgraph can be generated using the "wiggle" offset, which attempts to minimize change in slope weighted by layer thickness.

In the simplest case, the layer data can be specified as a two-dimensional array of numbers. The *y* and *x* accessors are used to define the thickness of each layer at the given position, respectively. With the exception of the "expand" offset, the stack layout does not perform any automatic scaling of data. To simplify scaling, use this layout in conjunction with a [linear scale](Quantitative-Scales#linear) or similar. The stack layout currently requires that the layers are homogenous: each must contain the same number of values at the same *x*-coordinates. If your data is not so regular, you will need to reinterpolate the data before computing the stack.

<a name="stack" href="#stack">#</a> d3.layout.<b>stack</b>()

<a name="_stack" href="#_stack">#</a> <b>stack</b>(<i>layers</i>[, <i>index</i>])

<a name="values" href="#values">#</a> stack.<b>values</b>([<i>accessor</i>])

<a name="order" href="#order">#</a> stack.<b>order</b>([<i>order</i>])

* inside-out - 
* reverse -
* default -

<a name="offset" href="#offset">#</a> stack.<b>offset</b>([<i>offset</i>])

* silhouette -
* wiggle -
* expand -
* zero -

<a name="x" href="#x">#</a> stack.<b>x</b>([<i>x</i>])

<a name="y" href="#y">#</a> stack.<b>y</b>([<i>y</i>])

<a name="out" href="#out">#</a> stack.<b>out</b>([<i>out</i>])
