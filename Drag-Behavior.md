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

If specified, sets the *origin* accessor function to the specified value. This function should return a two-element array specifying the starting coordinates of the element being dragged. If not specified, returns the current accessor function, which defaults to null. 