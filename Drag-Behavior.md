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

If specified, sets the *origin* accessor function to the specified value. This function should return an object with "x" and "y" properties specifying the starting coordinates of the element being dragged. If not specified, returns the current accessor function, which defaults to null.

This is typically used because an element's position doesn't match the mouse position exactly, depending on where it was clicked. By default, the current mouse position is used, but this can make the element jump e.g. if you drag a <rect> by clicking on its center, this could cause it to jump since it is typically positioned using its top-left corner. This is also useful for enforcing constraints i.e. if you have constrained a position to be within certain boundaries, then that will be respected.

Example demonstrating use of *origin* and position constraints on multiple elements.