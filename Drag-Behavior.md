> [Wiki](Home) ▸ [[API Reference]] ▸ [[Behaviors]] ▸ **Drag Behavior**

This behavior automatically creates event listeners to handle drag gestures on an element. Both mouse events and touch events are supported.

<a name="drag" href="Drag-Behavior#wiki-drag">#</a> d3.behavior.<b>drag</b>()

Constructs a new drag behavior.

<a name="on" href="Drag-Behavior#wiki-on">#</a> drag.<b>on</b>(<i>type</i>, <i>listener</i>)

Registers the specified *listener* to receive events of the specified *type* from the drag behavior. The following events are supported:

* "dragstart": fired when a drag gesture is started.
* "drag": fired when the element is dragged. d3.event will contain "x" and "y" properties representing the current absolute drag coordinates of the element. It will also contain "dx" and "dy" properties representing the element's coordinates relative to its position at the beginning of the gesture.
* "dragend": fired when the drag gesture has finished.

<a name="origin" href="Drag-Behavior#wiki-origin">#</a> drag.<b>origin</b>([*origin*])

If *origin* is specified, sets the origin accessor to the specified function. If *origin* is not specified, returns the current origin accessor which defaults to null.

An **origin accessor** is used to determine the starting position (the “origin”) of the element being dragged; this allows the drag behavior to preserve the offset between the mouse position and the starting element position during drag. If the origin accessor is null, then the element position is set to the mouse position on drag; this can cause a noticeable jump on large elements. If an origin accessor is specified, the function is called on mousedown. The function is invoked in the same manner as other operator functions, being passed the current datum `d` and index `i`, with the `this` context as the clicked-on DOM element. To access the current event, use the global [d3.event](Selections#wiki-d3_event). The origin accessor must return an object with `x` and `y` properties representing the starting coordinates of the element being dragged.

Frequently the origin accessor is specified as `Object`, which is equivalent to the identity function: `function(d) { return d; }`. This is suitable when the datum bound to the dragged element is already an object with `x` and `y` attributes representing its current position. For example: <http://bl.ocks.org/1557377>