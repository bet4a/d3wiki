> [[API Reference]]

SVG has a number of built-in simple shapes, such as axis-aligned rectangles and circles. For greater flexibility, you can use SVG's [[path|http://www.w3.org/TR/SVG/paths.html#PathElement]] element in conjunction with D3's path data generators. If you're familiar with Protovis, you'll note that D3's path generators are similar to Protovis marks.

## SVG Elements

All SVG shapes can be transformed using the [[transform|http://www.w3.org/TR/SVG/coords.html#TransformAttribute]] attribute. You can apply the transform either to the shape directly, or to a containing [[g|http://www.w3.org/TR/SVG/struct.html#Groups]] element. Thus, when a shape is defined as "axis-aligned", that merely means axis-aligned within the local coordinate system; you can still rotate and otherwise transform the shape. Shapes can be filled and stroked using the [[fill|http://www.w3.org/TR/SVG/painting.html#FillProperties]] and [[stroke|http://www.w3.org/TR/SVG/painting.html#StrokeProperties]] styles. (You can also use the attributes of the same name, but styles are recommended as they are compatible with external stylesheets.)

<a name="svg_rect" href="#svg_rect">#</a> svg:<b>rect</b> x="0" y="0" width="0" height="0" rx="0" ry="0"

The [[rect|http://www.w3.org/TR/SVG/shapes.html#RectElement]] element defines an axis-aligned rectangle. The top-left corner of the rectangle is positioned using the *x* and *y* attributes, while its size is specified using *width* and *height*. A rounded rectangle can be produced using the optional *rx* and *ry* attributes.

<a name="svg_circle" href="#svg_circle">#</a> svg:<b>circle</b> cx="0" cy="0" r="0"

The [[circle|http://www.w3.org/TR/SVG/shapes.html#CircleElement]] element defines a circle based on a center point and a radius. The center is positioned using the *cx* and *cy* attributes, while the radius is specified using the *r* attribute.

<a name="svg_ellipse" href="#svg_ellipse">#</a> svg:<b>ellipse</b> cx="0" cy="0" rx="0" ry="0"

The [[ellipse|http://www.w3.org/TR/SVG/shapes.html#EllipseElement]] element defines an axis-aligned ellipse based on a center point and two radii. The center is positioned using the *cx* and *cy* attributes, while the radii are specified using the *rx* and *ry* attributes.

<a name="svg_line" href="#svg_line">#</a> svg:<b>line</b> x1="0" y1="0" x2="0" y2="0"

The [[line|http://www.w3.org/TR/SVG/shapes.html#LineElement]] element defines a line segment that starts at one point and ends at another. The first point is specified using the *x1* and *x2* attributes, while the second point is specified using the *x2* and *y2* attributes. The line element is a popular choice for drawing rules, reference lines, axes and tick marks.

<a name="svg_polyline" href="#svg_polyline">#</a> svg:<b>polyline</b> points=""

The [[polyline|http://www.w3.org/TR/SVG/shapes.html#PolylineElement]] element defines a set of connected straight line segments. Typically, polyline elements define open shapes. The points that make up the polyline are specified using the *points* attribute. Note: in D3, it is typically more convenient and flexible to use the [d3.svg.line](#line) path generator in conjunction with a path element.

<a name="svg_polygon" href="#svg_polygon">#</a> svg:<b>polygon</b> points=""

The [[polygon|http://www.w3.org/TR/SVG/shapes.html#PolygonElement]] element defines a closed shape consisting of a set of connected straight line segments. The points that make up the polygon are specified using the *points* attribute. Note: in D3, it is typically more convenient and flexible to use the [d3.svg.line](#line) path generator in conjunction with a path element. The line can be closed using the [[closepath|http://www.w3.org/TR/SVG/paths.html#PathDataClosePathCommand]] "Z" command.

<a name="svg_text" href="#svg_text">#</a> svg:<b>text</b> x="0" y="0" dx="0" dy="0" text-anchor="start"

The [[text|http://www.w3.org/TR/SVG/text.html#TextElement]] element defines a graphics element consisting of text. The text content of the text element (see the [[text|Selections#text]] operator) define the characters to be rendered. The anchor position of the text element is controlled using the *x* and *y* attributes; additionally, the text can be offset from the anchor using *dx* and *dy* attributes. This offset is particularly convenient for controlling the text margin and baseline, as you can use "em" units which are relative to the font size. The horizontal text alignment is controlling using the *text-anchor* attribute. Here are a few examples:

```xml
<svg:text text-anchor="start">left-align, bottom-baseline</svg:text>
<svg:text text-anchor="middle">center-align, bottom-baseline</svg:text>
<svg:text text-anchor="end">right-align, bottom-baseline</svg:text>
<svg:text dy=".35em" text-anchor="start">left-align, middle-baseline</svg:text>
<svg:text dy=".35em" text-anchor="middle">center-align, middle-baseline</svg:text>
<svg:text dy=".35em" text-anchor="end">right-align, middle-baseline</svg:text>
<svg:text dy=".71em" text-anchor="start">left-align, top-baseline</svg:text>
<svg:text dy=".71em" text-anchor="middle">center-align, top-baseline</svg:text>
<svg:text dy=".71em" text-anchor="end">right-align, top-baseline</svg:text>
```

It's possible that there is a better way to specify the text baseline using SVG's [[baseline alignment properties|http://www.w3.org/TR/SVG/text.html#BaselineAlignmentProperties]], but these don't seem to be widely supported by browsers. Lastly, the font color is typically specified using the *fill* style (you can also use *stroke*), and the font is controlled using the *font*, *font-family*, *font-size* and related styles. Some browsers also support CSS3 properties, such as *text-shadow*.

<a name="svg_path" href="#svg_path">#</a> svg:<b>path</b> d="" transform=""

The [[path|http://www.w3.org/TR/SVG/paths.html#PathElement]] element represents the outline of a shape which can be filled, stroked, used as a clipping path, or any combination of the three. The *d* attribute defines the path data, which is a [[mini-language|http://www.w3.org/TR/SVG/paths.html#PathData]] of path commands, such as *moveto* (M), *lineto* (L) and *closepath* (Z). The path element is a generalization of all other shapes in SVG, and can be used to draw nearly anything!

## Path Data Generators

To simplify the construction of the *d* attribute for path elements, D3 includes a number of helper classes for generating path data. If you're familiar with [[Protovis|http://vis.stanford.edu/protovis/]], you'll find that these path generators are similar to Protovis mark types: each generator is a function of data. So, if you data is a sequence of *xy* coordinates, you can define accessor functions that the path generators use to produce path data. For example, you might define a line generator:

```javascript
var line = d3.svg.line()
    .x(function(d) { return d.x; })
    .y(function(d) { return d.y; })
    .interpolate("basis");
```

Then later on, you can use this function to set the *d* attribute:

```javascript
g.append("svg:path")
    .attr("d", line);
```

Whatever data is bound to `g` (in this example) will be passed to the `line` instance. Thus, the data must be specified as an array. For element element in the data array, the *x*- and *y*-accessor functions are used to pull out the control point coordinates.

A path generator, such as that returned by d3.svg.line, is both an object and a function. That is: you can call the generator like any other function, and the generator has additional methods that change its behavior. Like other classes in D3, path generators follow the method chaining pattern where setter methods return the generator itself, allowing multiple setters to be invoked in a concise statement.

<a name="line" href="#line">#</a> d3.svg.<b>line</b>()

Constructs a new line generator with the default *x*- and *y*-accessor functions (that assume the input data is a two-element array of numbers; see below for details), and linear interpolation. The input to the generator is always an array of data elements for which to generate a line. The output is a open piecewise linear curve, or polyline, as in a line chart:

![line](line.png)

By changing the interpolation, you can also generate splines and step functions. Also, don't be afraid to tack on additional path commands at the end. For example, if you want to generate a closed path, append a closepath (Z) command:

```javascript
g.append("svg:path")
    .attr("d", function(d) { return line(d) + "Z"; });
```

The line generator is designed to work in conjunction with the [area](#area) generator. For example, when producing an area chart, you might use an area generator with a fill style, and a line generator with a stroke style to emphasize the top edge of the area. Since the line generator is only used the set the *d* attribute, you can control the appearance of the line using standard SVG styles and attributes, such as *fill*, *stroke* and *stroke-width*.

<a name="line_x" href="#line_x">#</a> line.<b>x</b>([<i>x</i>])

If *x* is specified, sets the *x*-accessor to the specified function or constant. This accessor is invoked for each element in the data array passed to the line generator. The default accessor assumes that each input element is a two-element array of numbers:

```javascript
function x(d) {
  return d[0];
}
```

Typically, an *x*-accessor is specified because the input data is in a different format, or because you want to apply a [[scale|Quantitative Scales]]. For example, if your data is specified as an object with `x` and `y` attributes, rather than a tuple, you might dereference these attributes and apply the scales simultaneously:

```javascript
var x = d3.scale.linear().range([0, w]),
    y = d3.scale.linear().range([h, 0]);

var line = d3.svg.line()
    .x(function(d) { return x(d.x); })
    .y(function(d) { return y(d.y); });
```

The *x*-accessor is invoked in the same manner as other value functions in D3. The *this* context of the function is the current element in the selection. (Technically, the same *this* context that invokes the line function; however, in the common case that the line generator is passed to the [[attr|Selections#attr]] operator, the *this* context will be the associated DOM element.) The function is passed two arguments, the current datum (d) and the current index (i). In this context, the index is the index into the array of control points, rather than the index of the current element in the selection. The *x*-accessor is invoked exactly once per datum, in the order specified by the data array. Thus, it is possible to specify a nondeterministic accessor, such as a random number generator. It is also possible to specify the *x*-accessor as a constant rather than a function, in which case all points will have the same *x*-coordinate.

If *x* is not specified, returns the current *x*-accessor.

<a name="line_y" href="#line_y">#</a> line.<b>y</b>([<i>y</i>])

If *y* is specified, sets the *y*-accessor to the specified function or constant. This accessor is invoked for each element in the data array passed to the line generator. The default accessor assumes that each input element is a two-element array of numbers:

```javascript
function y(d) {
  return d[1];
}
```

For an example of how to specify a *y*-accessor, see the similar [x](#line_x) accessor. Note that, like most other graphics libraries, SVG uses the top-left corner as the origin. Thus, higher values of *y* are lower on the screen. In math and visualizations, we often want the origin in the bottom-left corner instead; one easy way to accomplish this is to invert the range of the *y*-scale by using range([h, 0]) instead of range([0, h]).

If *y* is not specified, returns the current *y*-accessor.

<a name="line_interpolate" href="#line_interpolate">#</a> line.<b>interpolate</b>([<i>interpolate</i>])

If *interpolate* is specified, sets the interpolation mode to the specified string. The following modes are supported:

* linear - piecewise linear segments, as in a polyline.
* step-before - alternate between vertical and horizontal segments, as in a step function.
* step-after - alternate between horizontal and vertical segments, as in a step function.
* basis - a [B-spline](http://en.wikipedia.org/wiki/B-spline), with control point duplication on the ends.
* basis-open - an open B-spline; may not intersect the start or end.
* basis-closed - a closed B-spline, as in a loop.
* cardinal - a [Cardinal spline](http://en.wikipedia.org/wiki/Cubic_Hermite_spline#Cardinal_spline), with control point duplication on the ends.
* cardinal-open - an open Cardinal spline; may not intersect the start or end, but will intersect other control points.
* cardinal-closed - a closed Cardinal spline, as in a loop.
* monotone - [cubic interpolation](http://en.wikipedia.org/wiki/Monotone_cubic_interpolation) that preserves monotonicity in *y*.

The behavior of some of these interpolation modes may be further customized by specifying a [tension](#line_tension).

If *interpolate* is not specified, returns the current interpolation mode.

<a name="line_tension" href="#line_tension">#</a> line.<b>tension</b>([<i>tension</i>])

If *tension* is specified, sets the Cardinal spline interpolation tension to the specified number in the range [0, 1]. The tension only affects the Cardinal interpolation modes: cardinal, cardinal-open and cardinal-closed. The default tension is 0.7. In some sense, this can be interpreted as the length of the tangent; 1 will yield all zero tangents, and 0 yields a [Catmull-Rom spline](http://en.wikipedia.org/wiki/Cubic_Hermite_spline#Catmull.E2.80.93Rom_spline). If *tension* is not specified, returns the current tension.

Note that the tension must be specified as a constant, rather than a function, as it is constant for the entirety of the line. However, it is still possible to generate multiple lines with different tensions using the same generator. For example:

```javascript
svg.selectAll("path")
    .data([0, 0.2, 0.4, 0.6, 0.8, 1])
  .enter().append("svg:path")
    .attr("d", function(d) { return line.tension(d)(data); });
```

In this example (see the [live version](http://bl.ocks.org/1016220)), the tension is set before each invocation of the line generator, thus resulting in lines with the same data but different paths.

<a name="area" href="#area">#</a> d3.svg.<b>area</b>()

Constructs a new area generator with the default *x*-, *y0*- and *y1*-accessor functions (that assume the input data is a two-element array of numbers; see below for details), and linear interpolation. The input to the generator is always an array of data elements for which to generate a line. The output is a closed piecewise linear curve, or polygon, as in an area chart:

![area](area.png)

Conceptually, the polygon is formed using two [lines](#line): the top line is formed using the *x*- and *y1*-accessor functions, and proceeds from left-to-right; the bottom line is added to this line, using the *x*- and *y0*-accessor functions, and proceeds from right-to-left. By setting the [transform](http://www.w3.org/TR/SVG/coords.html#TransformAttribute) attribute to rotate the path element by 90 degrees, you can also generate vertical areas. By changing the interpolation, you can also generate splines and step functions.

The area generator is designed to work in conjunction with the [line](#line) generator. For example, when producing an area chart, you might use an area generator with a fill style, and a line generator with a stroke style to emphasize the top edge of the area. Since the area generator is only used the set the *d* attribute, you can control the appearance of the area using standard SVG styles and attributes, such as *fill*.

To create [streamgraphs](http://mbostock.github.com/d3/ex/stream.html) (stacked area charts), use the [stack](Layout-Stack) layout. This layout sets the y0 attribute for each value in a series, which can be used from the *y0*- and *y1*-accessors. Note that each series must have the same number of values per series, and each value must have the same *x*-coordinate; if you have missing data or inconsistent *x*-coordinates per series, you must resample and interpolate your data before computing the stacked layout.

<a name="area_x" href="#area_x">#</a> area.<b>x</b>([<i>x</i>])

If *x* is specified, sets the *x*-accessor to the specified function or constant. This accessor is invoked for each element in the data array passed to the area generator. The default accessor assumes that each input element is a two-element array of numbers:

```javascript
function x(d) {
  return d[0];
}
```

Typically, an *x*-accessor is specified because the input data is in a different format, or because you want to apply a [[scale|Quantitative Scales]]. For example, if your data is specified as an object with `x` and `y` attributes, rather than a tuple, you might dereference these attributes and apply the scales simultaneously:

```javascript
var x = d3.scale.linear().range([0, w]),
    y = d3.scale.linear().range([h, 0]);

var area = d3.svg.area()
    .x(function(d) { return x(d.x); })
    .y0(h)
    .y1(function(d) { return y(d.y); });
```

The *x*-accessor is invoked in the same manner as other value functions in D3. The *this* context of the function is the current element in the selection. (Technically, the same *this* context that invokes the area function; however, in the common case that the area generator is passed to the [[attr|Selections#attr]] operator, the *this* context will be the associated DOM element.) The function is passed two arguments, the current datum (d) and the current index (i). In this context, the index is the index into the array of control points, rather than the index of the current element in the selection. The *x*-accessor is invoked exactly once per datum, in the order specified by the data array. Thus, it is possible to specify a nondeterministic accessor, such as a random number generator. It is also possible to specify the *x*-accessor as a constant rather than a function, in which case all points will have the same *x*-coordinate.

If *x* is not specified, returns the current *x*-accessor.

<a name="area_y0" href="#area_y0">#</a> area.<b>y0</b>([<i>y0</i>])

If *y0* is specified, sets the *y0*-accessor to the specified function or constant. This accessor is invoked for each element in the data array passed to the area generator. The default accessor is the constant zero, thus using a fixed baseline at *y* = 0. For an example of how to specify a *y0*-accessor, see the similar [x](#area_x) accessor. If *y0* is not specified, returns the current *y0*-accessor.

<a name="area_y1" href="#area_y1">#</a> area.<b>y1</b>([<i>y1</i>])

If *y1* is specified, sets the *y1*-accessor to the specified function or constant. This accessor is invoked for each element in the data array passed to the area generator. The default accessor assumes that each input element is a two-element array of numbers:

```javascript
function y1(d) {
  return d[1];
}
```

For an example of how to specify a *y1*-accessor, see the similar [x](#area_x) accessor. If *y1* is not specified, returns the current *y1*-accessor.

<a name="area_interpolate" href="#area_interpolate">#</a> area.<b>interpolate</b>([<i>interpolate</i>])

If *interpolate* is specified, sets the interpolation mode to the specified string. The following modes are supported:

* linear - piecewise linear segments, as in a polyline.
* step-before - alternate between vertical and horizontal segments, as in a step function.
* step-after - alternate between horizontal and vertical segments, as in a step function.
* basis - a [B-spline](http://en.wikipedia.org/wiki/B-spline), with control point duplication on the ends.
* basis-open - an open B-spline; may not intersect the start or end.
* cardinal - a [Cardinal spline](http://en.wikipedia.org/wiki/Cubic_Hermite_spline#Cardinal_spline), with control point duplication on the ends.
* cardinal-open - an open Cardinal spline; may not intersect the start or end, but will intersect other control points.
* monotone - [cubic interpolation](http://en.wikipedia.org/wiki/Monotone_cubic_interpolation) that preserves monotonicity in *y*.

The behavior of some of these interpolation modes may be further customized by specifying a [tension](#area_tension). Technically, the basis-closed and cardinal-closed interpolation modes are also supported, but these make more sense in the context of a line rather than an area.

If *interpolate* is not specified, returns the current interpolation mode.

<a name="area_tension" href="#area_tension">#</a> area.<b>tension</b>([<i>tension</i>])

If *tension* is specified, sets the Cardinal spline interpolation tension to the specified number in the range [0, 1]. The tension only affects the Cardinal interpolation modes: cardinal, cardinal-open and cardinal-closed. The default tension is 0.7. In some sense, this can be interpreted as the length of the tangent; 1 will yield all zero tangents, and 0 yields a [Catmull-Rom spline](http://en.wikipedia.org/wiki/Cubic_Hermite_spline#Catmull.E2.80.93Rom_spline). If *tension* is not specified, returns the current tension. Note that the tension must be specified as a constant, rather than a function, as it is constant for the entirety of the area.

<a name="arc" href="#arc">#</a> d3.svg.<b>arc</b>()

Constructs a new arc generator with the default *innerRadius*-, *outerRadius*-, *startAngle*- and *endAngle*-accessor functions (that assume the input data is an object with named attributes matching the accessors; see below for details). When the default accessors assume that the arc dimensions are all specified dynamically, it is very common to set one or more of the dimensions as a constant, such as setting the inner radius to zero for a pie chart. The input to the generator is always a single element for which to generate an arc. The output is a closed solid arc, as in a pie or donut chart:

![arc](arc.png)

In fact, four forms are possible: a [circle](http://en.wikipedia.org/wiki/Circle) (when the inner radius is zero and the angular span is greater than or equal to 2π), a [circular sector](http://en.wikipedia.org/wiki/Circular_sector) (when the inner radius is zero and the angular span is less than 2π), an [annulus](http://en.wikipedia.org/wiki/Annulus_(mathematics\)) (when the inner radius is non-zero and the angular span is greater than or equal to 2π), and an annular sector (when the inner radius is non-zero and the angular span is less than 2π).

<a name="arc_innerRadius" href="#arc_innerRadius">#</a> arc.<b>innerRadius</b>([<i>radius</i>])

If *radius* is specified, sets the *innerRadius*-accessor to the specified function or constant. This accessor is invoked on the argument passed to the arc generator. The default accessor assumes that the input data is an object with suitably-named attributes:

```javascript
function innerRadius(d) {
  return d.innerRadius;
}
```

Typically, a *innerRadius*-accessor is specified because the input data is in a different format, because you want to apply a [[scale|Quantitative Scales]], or because you want to specify a constant inner radius for a donut chart.

The *innerRadius*-accessor is invoked in the same manner as other value functions in D3. The *this* context of the function is the current element in the selection. (Technically, the same *this* context that invokes the arc function; however, in the common case that the arc generator is passed to the [[attr|Selections#attr]] operator, the *this* context will be the associated DOM element.) The function is passed two arguments, the current datum (d) and the current index (i). It is also possible to specify the *innerRadius*-accessor as a constant rather than a function.

If *radius* is not specified, returns the current *innerRadius*-accessor.

<a name="arc_outerRadius" href="#arc_outerRadius">#</a> arc.<b>outerRadius</b>([<i>radius</i>])

If *radius* is specified, sets the *outerRadius*-accessor to the specified function or constant. This accessor is invoked on the argument passed to the arc generator. The default accessor assumes that the input data is an object with suitably-named attributes:

```javascript
function outerRadius(d) {
  return d.outerRadius;
}
```

Typically, a *outerRadius*-accessor is specified because the input data is in a different format, because you want to apply a [[scale|Quantitative Scales]], or because you want to specify a constant inner radius for a donut chart.

The *outerRadius*-accessor is invoked in the same manner as other value functions in D3. The function is passed two arguments, the current datum (d) and the current index (i). It is also possible to specify the *outerRadius*-accessor as a constant rather than a function.

If *radius* is not specified, returns the current *outerRadius*-accessor.

<a name="arc_startAngle" href="#arc_startAngle">#</a> arc.<b>startAngle</b>([<i>angle</i>])

If *angle* is specified, sets the *startAngle*-accessor to the specified function or constant. Angles are specified in [radians](http://en.wikipedia.org/wiki/Radian), even though SVG typically uses degrees. This accessor is invoked on the argument passed to the arc generator. The default accessor assumes that the input data is an object with suitably-named attributes:

```javascript
function startAngle(d) {
  return d.startAngle;
}
```

For constructing pie or donut charts, you will need to compute the start angle of each arc as the end angle of the previous arc. This can be done very conveniently using the [pie](Layout-Pie) layout, which is similar to the [stack](Layout-Stack) layout; given a set of input data, the pie layout will construct arc objects with startAngle and endAngle attributes that you can use with the default arc accessors.

The *startAngle*-accessor is invoked in the same manner as other value functions in D3. The function is passed two arguments, the current datum (d) and the current index (i). It is also possible to specify the *startAngle*-accessor as a constant rather than a function.

If *angle* is not specified, returns the current *startAngle*-accessor.

<a name="arc_endAngle" href="#arc_endAngle">#</a> arc.<b>endAngle</b>([<i>angle</i>])

If *angle* is specified, sets the *endAngle*-accessor to the specified function or constant. Angles are specified in [radians](http://en.wikipedia.org/wiki/Radian), even though SVG typically uses degrees. This accessor is invoked on the argument passed to the arc generator. The default accessor assumes that the input data is an object with suitably-named attributes:

```javascript
function endAngle(d) {
  return d.endAngle;
}
```

For constructing pie or donut charts, you will need to compute the end angle of each arc as offset from the start angle. This can be done very conveniently using the [pie](Layout-Pie) layout, which is similar to the [stack](Layout-Stack) layout; given a set of input data, the pie layout will construct arc objects with startAngle and endAngle attributes that you can use with the default arc accessors.

The *endAngle*-accessor is invoked in the same manner as other value functions in D3. The function is passed two arguments, the current datum (d) and the current index (i). It is also possible to specify the *endAngle*-accessor as a constant rather than a function.

If *angle* is not specified, returns the current *startAngle*-accessor.

<a name="arc_centroid" href="#arc_centroid">#</a> arc.<b>centroid</b>(<i>arguments…</i>)

Computes the centroid of the arc that would be generated from the specified input *arguments*; typically, the arguments are the current datum (d), and optionally the current index (i). The centroid is defined as the midpoint in polar coordinates of the inner and outer radius, and the start and end angle. This provides a convenient location for arc labels. For example:

```javascript
arcs.append("svg:text")
    .attr("transform", function(d) { return "translate(" + arc.centroid(d) + ")"; })
    .attr("dy", ".35em")
    .attr("text-anchor", "middle")
    .text(function(d) { return d.value; });
```

Alternatively, you can use SVG's transform attribute to rotate text into position, though you may need to convert radians back into degrees. Yet another possibility is to use a [textPath](http://www.w3.org/TR/SVG/text.html#TextPathElement) element to curve the label along the path of the arc!

<a name="symbol" href="#symbol">#</a> d3.svg.<b>symbol</b>()

![symbol](symbol.png)

<a name="symbol_type" href="#symbol_type">#</a> symbol.<b>type</b>([<i>type</i>])

<a name="symbol_size" href="#symbol_size">#</a> symbol.<b>size</b>([<i>size</i>])

<a name="chord" href="#chord">#</a> d3.svg.<b>chord</b>()

![chord](chord.png)

<a name="chord_radius" href="#chord_radius">#</a> chord.<b>radius</b>([<i>radius</i>])

<a name="chord_startAngle" href="#chord_startAngle">#</a> chord.<b>startAngle</b>([<i>angle</i>])

<a name="chord_endAngle" href="#chord_endAngle">#</a> chord.<b>endAngle</b>([<i>angle</i>])

<a name="chord_source" href="#chord_source">#</a> chord.<b>source</b>([<i>source</i>])

<a name="chord_target" href="#chord_target">#</a> chord.<b>target</b>([<i>target</i>])

<a name="diagonal" href="#diagonal">#</a> d3.svg.<b>diagonal</b>()

![diagonal](diagonal.png)

<a name="diagonal_source" href="#diagonal_source">#</a> diagonal.<b>source</b>([<i>source</i>])

<a name="diagonal_target" href="#diagonal_target">#</a> diagonal.<b>target</b>([<i>target</i>])