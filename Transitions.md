# Transitions

> [[API Reference|API-Reference]]

A transition is a special type of [[selection|Selections]] where the operators apply smoothly over time rather than instantaneously. You can derive a transition from a selection using the [[transition|Selections#transition]] operator, or by using the top-level [d3.transition](#d3_transition) method followed by a subselect. While transitions generally support the same operators as selections (such as [attr](#attr) and [style](#style)), not all operators are yet supported; for example, you must append elements before a transition starts. A [remove](#remove) operator is provided for convenient removal of elements when the transition ends.

Transitions may have per-element delays and durations, computed using functions of data similar to other operators. This makes it easy to stagger a transition for different elements, either based on data or index. For example, you can sort elements and then stagger the transition for better perception of element reordering during the transition. For more details on these techniques, see [["Animated Transitions in Statistical Data Graphics"|http://vis.berkeley.edu/papers/animated_transitions/]] by Heer & Robertson.

D3 has many built-in interpolators to simplify the transitioning of arbitrary values. For instance, you can transition from the font string "500 12px sans-serif" to "300 42px sans-serif", and D3 will in find the numbers embedded within the string, interpolating both font size and weight automatically. You can even interpolate arbitrary nested objects and arrays or SVG path data. D3 also allows custom interpolators should you find the built-in ones insufficient; you can specify a custom interpolator using the [attrTween](#attrTween) and [styleTween](#styleTween) operators. D3's interpolators also provide the basis for the [[scale|Scales]] module, and can be used independently from transitions; an interpolator is a function that maps a parametric value *t* in the domain [0,1] to a color, number or arbitrary value.

## Starting Transitions

<a name="d3_transition" href="#d3_transition">#</a> d3.<b>transition</b>()

Start an animated transition.

<a name="delay" href="#delay">#</a> transition.<b>delay</b>(<i>value</i>)

Specify per-element delay in milliseconds.

<a name="duration" href="#duration">#</a> transition.<b>duration</b>(<i>value</i>)

Specify per-element duration in milliseconds.

<a name="ease" href="#ease">#</a> transition.<b>ease</b>(<i>value</i>)

Specify transition easing function.

## Operating on Transitions

### Content

<a name="attr" href="#attr">#</a> transition.<b>attr</b>(<i>name</i>, <i>value</i>)

Smoothly transition to the new attribute value.

<a name="attrTween" href="#attrTween">#</a> transition.<b>attrTween</b>(<i>name</i>, <i>tween</i>)

Smoothly transition between two attribute values.

<a name="style" href="#style">#</a> transition.<b>style</b>(<i>name</i>, <i>value</i>[, <i>priority</i>])

Smoothly transition to the new style property value.

<a name="styleTween" href="#styleTween">#</a> transition.<b>styleTween</b>(<i>name</i>, <i>tween</i>[, <i>priority</i>])

Smoothly transition between two style property values.

<a name="text" href="#text">#</a> transition.<b>text</b>(<i>value</i>)

Set the text content when the transition starts.

<a name="remove" href="#remove">#</a> transition.<b>remove</b>()

Remove selected elements at the end of a transition. If the transition is cancelled, the selected elements will not be removed.

### Subtransitions

<a name="select" href="#select">#</a> transition.<b>select</b>(<i>selector</i>)

Start a transition on a descendant element for each selected element. Inherits easing, duration and delay.

<a name="selectAll" href="#selectAll">#</a> transition.<b>selectAll</b>(<i>selector</i>)

Start a transition on multiple descendants for each selected element. Inherits easing, duration and delay.

### Control

<a name="each" href="#each">#</a> transition.<b>each</b>(<i>type</i>, <i>listener</i>)

Add a listener for transition events. Currently only supports "end" events. There is no way to remove the event listener. And, this operator has the same name as the selection [[each|Selections#each]] operator, which is somewhat confusing. It should probably be renamed to "on" or "onEach".

<a name="call" href="#call">#</a> transition.<b>call</b>(<i>function</i>)

Call a function passing in the current transition.

## Easing

<a name="d3_ease" href="#d3_ease">#</a> d3.<b>ease</b>(<i>name</i>[, <i>arguments…</i>])

Customize transition timing.

## Interpolation

<a name="d3_interpolate" href="#d3_interpolate">#</a> d3.<b>interpolate</b>(<i>a</i>, <i>b</i>)

Interpolate two values.

<a name="d3_interpolateNumber" href="#d3_interpolateNumber">#</a> d3.<b>interpolateNumber</b>(<i>a</i>, <i>b</i>)

Interpolate two numbers.

<a name="d3_interpolateRound" href="#d3_interpolateRound">#</a> d3.<b>interpolateRound</b>(<i>a</i>, <i>b</i>)

Interpolate two integers.

<a name="d3_interpolateString" href="#d3_interpolateString">#</a> d3.<b>interpolateString</b>(<i>a</i>, <i>b</i>)

Interpolate two strings.

<a name="d3_interpolateRgb" href="#d3_interpolateRgb">#</a> d3.<b>interpolateRgb</b>(<i>a</i>, <i>b</i>)

Interpolate two colors in RGB space.

<a name="d3_interpolateHsl" href="#d3_interpolateHsl">#</a> d3.<b>interpolateHsl</b>(<i>a</i>, <i>b</i>)

Interpolate two colors in HSL space. The resulting interpolator still returns an RGB color string for browser compatibility, however.

<a name="d3_interpolateArray" href="#d3_interpolateArray">#</a> d3.<b>interpolateArray</b>(<i>a</i>, <i>b</i>)

Interpolate two arrays of values.

<a name="d3_interpolateObject" href="#d3_interpolateObject">#</a> d3.<b>interpolateObject</b>(<i>a</i>, <i>b</i>)

Interpolate two arbitrary objects.
