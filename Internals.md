> [[API Reference]]

<a name="functor" href="#functor">#</a> d3.<b>functor</b>(<i>value</i>)

If the specified *value* is a function, returns the specified value. Otherwise, returns a function that returns the specified value. This method is used internally as a lazy way of upcasting constant values to functions, in cases where a property may be specified either as a function or a constant. For example, many D3 layouts allow properties to be specified this way, and it simplifies the implementation if we automatically convert constant values to functions.
