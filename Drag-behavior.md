> [[API Reference]] ▸ [[Behavior]]

The drag behavior makes it possible to interactively drag an element with the mouse. 

<a name="drag" href="Drag-behavior#wiki-drag">#</a> d3.behavior.<b>drag</b>()

Constructs a new drag behavior.

```javascript
var drag = d3.behavior.drag()
    .on("drag", ondrag)
    .on("dragstart", ondragstart)
    .on("dragend", ondragend)
```


<a name="on" href="Drag-behavior#wiki-on">#</a> drag.<b>on</b>(<i>type</i>, <i>listener</i>)

Registers the specified *listener* to receive events of the specified *type*. Currently, "drag", "dragstart" and "dragend" events are supported. 

Listen to drag events to update the displayed positions of elements. For example, if you initially display a rectangle like so:

```javascript
var rect = vis.selectAll("rect")
    .data([{"x":0, "y":0}])
  .enter().append("svg:rect")
    .attr("width", 100)
    .attr("height", 100)
    .attr("fill", "#f00")
    .call(drag)

```

You can update it's position on drag:

```javascript
var ondrag = function(d,i) {
   d.x += d3.events.dx;
   d.y += d3.events.dy;
   d3.select(this).attr("transform", "translate(" + [d.x, d.y] + ")");
});
```

In this case, we've stored the coordinate used to translate our rectangle as data and update it directly by how much the mouse has moved.


Implementation note: the mousemove and mouseup event listeners are registered on the current window, such that when the user starts dragging an element, they can continue to drag the element even if the mouse leaves the window. Each event listener uses the "drag" namespace, so as to avoid collision with other event listeners you may wish to bind to nodes or to the window. If an element is moved by the drag behavior, the subsequent click event that would be triggered by the final mouseup is captured and stopped from propagating. This allows you to register click event handlers on elements that will only be triggered if elements are clicked *without* dragging.


An example which also shows how to ignore mouse events on text is given here
http://bl.ocks.org/1378144