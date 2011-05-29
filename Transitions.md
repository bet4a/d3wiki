# Transitions

A transition is a special type of [[selection|Selections]] where the operators apply smoothly over time rather than instantaneously. You can derive a transition from a selection using the [[transition|Selections#transition]] operator, or by using the top-level [transition](#d3_transition) method followed by a subselect. While transitions generally support the same operators as selections (such as [attr](#attr) and [style](#style)), not all operators are supported; for example, you must append elements before a transition starts. (Though, note that a [remove](#remove) operator is provided for convenient removal of elements when the transition ends.)

Transitions may have per-element delays and durations, computed using functions of data similar to other operators. This makes it very convenient to stagger a transition for different elements, either based on data or index. For example, you can sort elements and then stagger the transition to make it easier to perceive individual elements reordering during the transition. For more details on these techniques, see [["Animated Transitions in Statistical Data Graphics"|http://vis.berkeley.edu/papers/animated_transitions/]] by Heer & Robertson.

D3 has many built-in interpolators to simplify the transitioning of arbitrary values. For instance, you can transition from the font string "500 12px sans-serif" to "300 42px sans-serif", and D3 will in find the numbers embedded within the string, interpolating both font size and weight automatically. You can even interpolate arbitrary nested objects and arrays, or SVG path data. However, D3 also supports custom interpolators should you find the build-in ones insufficient; you can specify a custom interpolator using the [attrTween](#attrTween) and [styleTween](#styleTween) operators. D3's interpolators also provide the basis for the [[scale|Scales]] module, and can be used independently from transitions; an interpolator is simple a function that maps a parametric value *t* in the domain [0,1] to a color, number or arbitrary value.

## Starting Transitions

d3.transition - start an animated transition.
transition.delay - specify per-element delay in milliseconds.
transition.duration - specify per-element duration in milliseconds.
transition.ease - specify transition easing function.

## Operating on Transitions

### Content

transition.attr - smoothly transition to the new attribute value.
transition.attrTween - smoothly transition between two attribute values.
transition.style - smoothly transition to the new style property value.
transition.styleTween - smoothly transition between two style property values.
transition.text - set the text content when the transition starts.
transition.remove - remove selected elements at the end of a transition.

### Subtransitions

transition.select - start a transition on a descendant element for each selected element.
transition.selectAll - start a transition on multiple descendants for each selected element.

### Control

transition.each - add a listener for transition end events.
transition.call - call a function passing in the current transition.

## Easing

d3.ease - customize transition timing.

## Interpolation

d3.interpolate - interpolate two values.
d3.interpolateNumber - interpolate two numbers.
d3.interpolateRound - interpolate two integers.
d3.interpolateString - interpolate two strings.
d3.interpolateRgb - interpolate two RGB colors.
d3.interpolateHsl - interpolate two HSL colors.
d3.interpolateArray - interpolate two arrays of values.
d3.interpolateObject - interpolate two arbitrary objects.
