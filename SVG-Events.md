> [[API Reference]]

Standard event listeners can be registered (and unregistered) in D3 using the selection's [[on|Selections#on]] operator. While you can use the native event's [[pageX|https://developer.mozilla.org/en/DOM/event.pageX]] and [[pageY|https://developer.mozilla.org/en/DOM/event.pageY]], it is often more convenient to transform the event position to the local coordinate system of the container that received the event. For example, if you embed an SVG in the normal flow of your page, you may want the event position relative to the top-left corner of the SVG image. If your SVG contains transforms, you might also want to know the position of the event relative to those transforms. Use the [mouse](#mouse) operator for the standard mouse pointer, and use [touches](#touches) for multitouch events on iOS.

<a name="mouse" href="#mouse">#</a> d3.svg.<b>mouse</b>(<i>container</i>)

Returns the *x* and *y* coordinates of the current [[d3.event|Selections#d3_event]], relative to the specified *container*. The container must be an SVG container element, such as an [[svg:g|http://www.w3.org/TR/SVG/struct.html#Groups]] or [[svg:svg|http://www.w3.org/TR/SVG/struct.html#SVGElement]]. The coordinates are returned as a two-element array [*x*, *y*].

<a name="touches" href="#touches">#</a> d3.svg.<b>touches</b>(<i>container</i>)

Returns the *x* and *y* coordinates of each touch associated with the current d3.event, based on the [[touches|http://developer.apple.com/library/safari/documentation/UserExperience/Reference/TouchEventClassReference/TouchEvent/TouchEvent.html#//apple_ref/javascript/instp/TouchEvent/touches]] attribute, relative to the specified *container*. The container must be an SVG container element, such as an svg:g or svg:svg. The coordinates are returned as an array of two-element arrays [[*x1*, *y1*], [*x2*, *y2*], …].