> [[API Reference]]

D3 has a variety of internal methods that may be useful if you are implementing your own layout or chart template.

## Functions

<a name="functor" href="#functor">#</a> d3.<b>functor</b>(<i>value</i>)

If the specified *value* is a function, returns the specified value. Otherwise, returns a function that returns the specified value. This method is used internally as a lazy way of upcasting constant values to functions, in cases where a property may be specified either as a function or a constant. For example, many D3 layouts allow properties to be specified this way, and it simplifies the implementation if we automatically convert constant values to functions.

<a name="rebind" href="#rebind">#</a> d3.<b>rebind</b>(<i>object</i>, <i>method</i>)

## Events

<a name="d3_dispatch" href="#d3_dispatch">#</a> d3.<b>dispatch</b>(<i>types…</i>)

<a name="dispatch_add" href="#dispatch_add">#</a> dispatch.<b>add</b>(<i>listener</i>)

<a name="dispatch_remove" href="#dispatch_remove">#</a> dispatch.<b>remove</b>(<i>listener</i>)

<a name="dispatch_dispatch" href="#dispatch_dispatch">#</a> dispatch.<b>dispatch</b>(<i>arguments…</i>)