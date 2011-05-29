# Transitions

> [[API Reference|API-Reference]]

A transition is a special type of [[selection|Selections]] where the operators apply smoothly over time rather than instantaneously. You can derive a transition from a selection using the [[transition|Selections#transition]] operator, or by using the top-level [d3.transition](#d3_transition) method followed by a subselect. While transitions generally support the same operators as selections (such as [attr](#attr) and [style](#style)), not all operators are yet supported; for example, you must append elements before a transition starts. A [remove](#remove) operator is provided for convenient removal of elements when the transition ends.

Transitions may have per-element delays and durations, computed using functions of data similar to other operators. This makes it easy to stagger a transition for different elements, either based on data or index. For example, you can sort elements and then stagger the transition for better perception of element reordering during the transition. For more details on these techniques, see [["Animated Transitions in Statistical Data Graphics"|http://vis.berkeley.edu/papers/animated_transitions/]] by Heer & Robertson.

D3 has many built-in interpolators to simplify the transitioning of arbitrary values. For instance, you can transition from the font string "500 12px sans-serif" to "300 42px sans-serif", and D3 will in find the numbers embedded within the string, interpolating both font size and weight automatically. You can even interpolate arbitrary nested objects and arrays or SVG path data. D3 also allows custom interpolators should you find the built-in ones insufficient; you can specify a custom interpolator using the [attrTween](#attrTween) and [styleTween](#styleTween) operators. D3's interpolators also provide the basis for the [[scale|Scales]] module, and can be used independently from transitions; an interpolator is a function that maps a parametric value *t* in the domain [0,1] to a color, number or arbitrary value.

Only one transition may be active on a given element at a given time. However, you may schedule multiple transitions on the same element; provided they are staggered in time, each transition will run in sequence. Furthermore, if a newer transition runs on a given element, it implicitly cancels any older transitions, including any that were scheduled but not yet run. This allows new transitions, such as those in response to a new user event, to supersede older transitions, even if those older transitions are staged or have staggered delays. Multi-stage transitions (transitions that are created during the "end" event of an earlier transition) are considered the same "age" as the original transition; internally this is implemented using monotonically-increasing unique IDs, which are inherited when multi-stage transitions are created.

## Starting Transitions

Transitions are typically created using the [[transition|Selections#transition]] operator on an existing selection. Transitions start automatically upon creation, based on the designated delay which defaults to zero; however, note that a zero-delay transition actually starts after a minimal (<10ms) delay, pending the first timer callback.

<a name="d3_transition" href="#d3_transition">#</a> d3.<b>transition</b>()

Create an animated transition. This is equivalent to saying `d3.select(document).transition()`. This method is used rarely, as it is typically easier to derive a transition from an existing selection, rather than deriving a selection from an existing transition.

<a name="delay" href="#delay">#</a> transition.<b>delay</b>(<i>value</i>)

Specifies per-element delay *value* in milliseconds. If *value* is a constant, then all elements are given the same delay; otherwise, if *value* is a function, then the function is evaluated for each selected element (in order), being passed the current datum `d` and the current index `i`, with the `this` context as the current DOM element. The function's return value is then used to set each element's delay.

Setting the delay to be a multiple of the index `i` is a convenient way to stagger transitions for elements. You can also compute the delay as a function of the data, thereby creating a data-driven animation.

<a name="duration" href="#duration">#</a> transition.<b>duration</b>(<i>value</i>)

Specifies per-element duration *value* in milliseconds. If *value* is a constant, then all elements are given the same duration; otherwise, if *value* is a function, then the function is evaluated for each selected element (in order), being passed the current datum `d` and the current index `i`, with the `this` context as the current DOM element. The function's return value is then used to set each element's duration.

<a name="ease" href="#ease">#</a> transition.<b>ease</b>(<i>value</i>[, <i>arguments</i>])

Specifies the transition easing function. If *value* is a function, it is used to ease the current parametric timing value *t* in the range [0,1]; otherwise, *value* is assumed to be a string and the arguments are passed to the [d3.ease][#d3_ease] method to generate an easing function.

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

## Timers

<a name="d3_timer" href="#d3_timer">#</a> d3.<b>timer</b>(<i>function</i>)

Start a custom animation timer.

<a name="d3_timer_flush" href="#d3_timer_flush">#</a> d3.timer.<b>flush</b>()

Immediately execute any zero-delay timers. Normally, zero-delay transitions are executed after an instantaneous delay. However, this can sometimes cause a brief flicker if the browser renders the page twice: once at the end of the first event loop, then again immediately on the first timer callback. By flushing the timer queue at the end of the first event loop, you can run any zero-delay transitions immediately and avoid the flicker.

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
