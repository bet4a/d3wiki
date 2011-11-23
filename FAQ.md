D3 is a javascript library geared towards visualizations, animations and interactions.  Novice and expert users might find useful the answers provided here.

## How do I get started using D3? ##

The easiest way is to copy the following text into a file `bar.html` and play with it.

```html
<!doctype html>
<html>
  <head>    
    <meta http-equiv="Content-Type" content="text/html;charset=utf-8" />     
    <title>bar</title>    
    <script type="text/javascript" src="http://mbostock.github.com/d3/d3.js"></script>
    <style type="text/css">  
      #chart {
        width: 640px;
        height: 320px;   
        border: 1px solid lightgray;
        font-size: 12px;  
      }   
      #chart .bar {
        fill: steelblue;
      }          
      #chart .xaxis {
        stroke: black;
      }
    </style>
  </head>
<body> 
  <div id="chart"></div>
  <script type="text/javascript">

    var w = 640,
        h = 320,
        m = [ 15, 5, 15, 5 ], // top, right, bottom, left (ala css)
        data = [ { l: "Jan", v: 10 }, { l: "Feb", v: 12 }, { l: "Mar", v: 14 }, { l: "Apr", v: 16 } ];

    var x = d3.scale.ordinal().domain(d3.range(data.length))
          .rangeBands([0, w - m[1] - m[3]], 0.1),
        y = d3.scale.linear().domain([0, d3.max(data, function(d) { return d.v; })])
          .range([0, h - m[0] - m[2]]);
           
    var vis = d3.select("#chart")
      .append("svg")
        .attr("width", w)
        .attr("height", h)
      .append("g")
        .attr("transform", "translate(" + m[3] + "," + m[0] + ")");

    vis.selectAll("rect.bar")
        .data(data)
      .enter().append("rect")
        .attr("class", "bar")
        .attr("x", function(d, i) { return x(i); })
        .attr("y", function(d) { return h - m[0] - m[2] - y(d.v); })
        .attr("width", x.rangeBand())
        .attr("height", function(d) { return y(d.v); });
 
    vis.selectAll("text.value")
        .data(data)
      .enter().append("text")
        .attr("class", "value")
        .attr("x", function(d, i) { return x(i) + x.rangeBand() / 2; })
        .attr("y", function(d) { return h - m[0] - m[2] - y(d.v); }) 
        .attr("dy", -2)
        .attr("text-anchor", "middle")
        .text(function(d) { return d.v; });

    vis.selectAll("text.label")
        .data(data)
      .enter().append("text")
        .attr("class", "label")
        .attr("x", function(d, i) { return x(i) + x.rangeBand() / 2; })
        .attr("y", h - m[0] - m[2] - y(0)) 
        .attr("dy", 12)
        .attr("text-anchor", "middle")
        .text(function(d) { return d.l; });

    vis.append("line")
      .attr("class", "xaxis")
      .attr("x1", 0)
      .attr("x2", w - m[1] - m[3])
      .attr("y1", h - m[0] - m[2] - y(0))
      .attr("y2", h - m[0] - m[2] - y(0));  
  
  </script>
</body>
</html>
```

After you have this working download the library [here](https://github.com/mbostock/d3/archives/master) and setup your testing structure.

## Why are mouse events not firing on `<svg>` in Safari?

You need to add a background `<rect>` element that fills the area of interest e.g. with `fill="#fff"`. In Safari, mouse events will only fire on `<svg>` if the mouse is over a child element.