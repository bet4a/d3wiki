> [[API Reference]]

SVG has a number of built-in simple shapes, such as axis-aligned rectangles and circles. For greater flexibility, you can use SVG's [[path|http://www.w3.org/TR/SVG/paths.html#PathElement]] element in conjunction with D3's path data generators. If you're familiar with Protovis, you'll note that D3's path generators are similar to Protovis marks.

## Built-in Shapes

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

    <svg:text text-anchor="start">left-align, bottom-baseline</svg:text>
    <svg:text text-anchor="middle">center-align, bottom-baseline</svg:text>
    <svg:text text-anchor="end">right-align, bottom-baseline</svg:text>
    <svg:text dy=".35em" text-anchor="start">left-align, middle-baseline</svg:text>
    <svg:text dy=".35em" text-anchor="middle">center-align, middle-baseline</svg:text>
    <svg:text dy=".35em" text-anchor="end">right-align, middle-baseline</svg:text>
    <svg:text dy=".71em" text-anchor="start">left-align, top-baseline</svg:text>
    <svg:text dy=".71em" text-anchor="middle">center-align, top-baseline</svg:text>
    <svg:text dy=".71em" text-anchor="end">right-align, top-baseline</svg:text>

It's possible that there is a better way to specify the text baseline using SVG's [[baseline alignment properties|http://www.w3.org/TR/SVG/text.html#BaselineAlignmentProperties]], but these don't seem to be widely supported by browsers. Lastly, the font color is typically specified using the *fill* style (you can also use *stroke*), and the font is controlled using the *font*, *font-family*, *font-size* and related styles. Some browsers also support CSS3 properties, such as *text-shadow*.

## Path Shapes

<a name="svg_path" href="#svg_path">#</a> svg:<b>path</b>

<a name="line" href="#line">#</a> d3.svg.<b>line</b>()

![line](line.png)

<a name="line_x" href="#line_x">#</a> line.<b>x</b>([<i>x</i>])

<a name="line_y" href="#line_y">#</a> line.<b>y</b>([<i>y</i>])

<a name="line_interpolate" href="#line_interpolate">#</a> line.<b>interpolate</b>([<i>interpolate</i>])

<a name="line_tension" href="#line_tension">#</a> line.<b>tension</b>([<i>tension</i>])

<a name="area" href="#area">#</a> d3.svg.<b>area</b>()

![area](area.png)

<a name="area_x" href="#area_x">#</a> area.<b>x</b>([<i>x</i>])

<a name="area_y0" href="#area_y0">#</a> area.<b>y0</b>([<i>y0</i>])

<a name="area_y1" href="#area_y1">#</a> area.<b>y1</b>([<i>y1</i>])

<a name="area_interpolate" href="#area_interpolate">#</a> area.<b>interpolate</b>([<i>interpolate</i>])

<a name="area_tension" href="#area_tension">#</a> area.<b>tension</b>([<i>tension</i>])

<a name="arc" href="#arc">#</a> d3.svg.<b>arc</b>()

![arc](arc.png)

<a name="arc_innerRadius" href="#arc_innerRadius">#</a> arc.<b>innerRadius</b>([<i>radius</i>])

<a name="arc_outerRadius" href="#arc_outerRadius">#</a> arc.<b>outerRadius</b>([<i>radius</i>])

<a name="arc_startAngle" href="#arc_startAngle">#</a> arc.<b>startAngle</b>([<i>angle</i>])

<a name="arc_endAngle" href="#arc_endAngle">#</a> arc.<b>endAngle</b>([<i>angle</i>])

<a name="arc_centroid" href="#arc_centroid">#</a> arc.<b>centroid</b>()

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