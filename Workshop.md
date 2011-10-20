# Workshop

## Website

- <http://mbostock.github.com/d3>
- examples, tutorials
- github website: issues, wiki, api reference
- workshop outline

## d3 core

DOM manipulation.

### developer console

- ⌥⌘J
- inspect, $0
- d3
- d3.version

### top-level selections

- d3.select("tag")
- d3.select(".class")
- d3.select("#id")
- d3.selectAll("tag")
- inspect selections in the console, [0][0]
- selection.node()

### creating and removing individual elements

- selection.append = appendChild
- selection.insert = insertBefore
- selection.remove = removeChild

### modifying elements (constant values)

- selection.attr = setAttribute
- selection.style = style.setProperty
- selection.classed = classList.add or classList.remove
- selection.property = direct assignment
- selection.text = textContent
- selection.html = innerHTML

### basic transitions

- transition.attr
- transition.style
- transition.delay
- transition.duration
- transition.ease: cubic-in-out, elastic, bounce

### a note about interpolation

- d3.interpolate
- d3.interpolateNumber
- d3.interpolateString
- d3.interpolateRgb
- d3.interpolateHsl
- d3.rgb and d3.hsl, brighter, darker
- later on: interpolateArray, interpolateObject

### interaction

- selection.on

```javascript
var svg = d3.select("body").text(null).append("svg:svg")
    .attr("width", 960)
    .attr("height", 500);

svg.append("svg:rect")
    .attr("width", "100%")
    .attr("height", "100%")
    .style("fill", "white");
```

```javascript
svg.on("mousemove", function() {
  console.log("Hello, mouse!");
});
```

```javascript
svg.on("mousemove", function() {
  console.log("Hello: " + this);
});
```

- d3.event

```javascript
svg.on("mousemove", function() {
  console.log("Hello: " + d3.event);
});
```

- d3.svg.mouse

```javascript
svg.on("mousemove", function() {
  console.log("Hello: " + d3.svg.mouse(this));
});
```

```javascript
var circle = svg.append("svg:circle")
    .attr("r", 24)
    .style("fill", "brown");

svg.on("mousemove", function() {
  var m = d3.svg.mouse(this);
  circle
      .attr("cx", m[0])
      .attr("cy", m[1]);
});
```

```javascript
var circle = svg.append("svg:circle")
    .attr("r", 24)
    .style("fill", "brown");

svg.on("mousemove", function() {
  var m0 = [+circle.attr("cx"), +circle.attr("cy")],
      m1 = d3.svg.mouse(this);
  circle
      .attr("cx", m0[0] + (m1[0] - m0[0]) * .2)
      .attr("cy", m0[1] + (m1[1] - m0[1]) * .2);
});
```

```javascript
svg.on("mousemove", function() {
  var mouse = d3.svg.mouse(this);
  svg.append("svg:circle")
      .attr("cx", mouse[0])
      .attr("cy", mouse[1])
      .attr("r", 0)
      .style("fill", "none")
      .style("stroke", "red")
      .style("stroke-opacity", 1)
      .style("stroke-width", 1.5)
    .transition()
      .duration(2000)
      .ease(Math.sqrt)
      .attr("r", 120)
      .style("stroke", "blue")
      .style("stroke-opacity", 0)
      .remove();
});
```

### modifying elements (function values)

- d, i, this
- return value

```javascript
for (var i = 0; i < 10; i++) svg.append("svg:circle");
var circle = svg.selectAll("circle");
```

### data binding (generalized selection)

- array literals
- d3.range
- update selection
- enter selection (more data than elements)
- exit selection (fewer data than elements)
- data key function
- three little circles
- enter transition
- exit transition
- enter+update

## installing

- text editor (TextWrangler)
- download tarball or git clone (you can later github fork)
- local http server for testing (python)
- or, -–allow-file-access-from-files
- or, <https://gist.github.com/1300016>

```
$ open -a Google\ Chrome --args --allow-file-access-from-files
```
<http://www.chromium.org/developers/how-tos/run-chromium-with-flags>

## working with data

- xhr: json, csv, text, xml, html
- array extras: sort, filter, map, reduce
- basic statistics: min, max, sum, mean, median, quantile
- converting objects to arrays: d3.values, d3.keys, d3.entries
- nest
- parsing times
- type coercion

## working with shapes

- line
- area
- arc
- symbol
- line.radial, area.radial

## scales

### quantitative scales

- linear
- log
- pow
- quantile
- quantize
- time

### ordinal scales

- ordinal
- category*

### displaying ticks and axes

- axis component

## geographic data

## force layouts

## hierarchical layouts
