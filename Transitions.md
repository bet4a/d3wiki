# Transitions

> [[API Reference|API-Reference]]

A transition is a special type of [[selection|Selections]] where the operators apply smoothly over time rather than instantaneously. You derive a transition from a selection using the [[transition|Selections#transition]] operator. While transitions generally support the same operators as selections (such as [attr](#attr) and [style](#style)), not all operators are supported; for example, you must append elements before a transition starts. A [remove](#remove) operator is provided for convenient removal of elements when the transition ends.

Transitions may have per-element delays and durations, computed using functions of data similar to other operators. This makes it easy to stagger a transition for different elements, either based on data or index. For example, you can sort elements and then stagger the transition for better perception of element reordering during the transition. For more details on these techniques, see [["Animated Transitions in Statistical Data Graphics"|http://vis.berkeley.edu/papers/animated_transitions/]] by Heer & Robertson.

D3 has many built-in interpolators to simplify the transitioning of arbitrary values. For instance, you can transition from the font string "500 12px sans-serif" to "300 42px sans-serif", and D3 will in find the numbers embedded within the string, interpolating both font size and weight automatically. You can even interpolate arbitrary nested objects and arrays or SVG path data. D3 allows custom interpolators should you find the built-in ones insufficient, using the [attrTween](#attrTween) and [styleTween](#styleTween) operators. D3's interpolators provide the basis for [[scales|Scales]] and can be used outside of transitions; an interpolator is a function that maps a parametric value *t* in the domain [0,1] to a color, number or arbitrary value.

Only one transition may be *active* on a given element at a given time. However, multiple transitions may be *scheduled* on the same element; provided they are staggered in time, each transition will run in sequence. If a newer transition runs on a given element, it implicitly cancels any older transitions, including any that were scheduled but not yet run. This allows new transitions, such as those in response to a new user event, to supersede older transitions even if those older transitions are staged or have staggered delays. Multi-stage transitions (transitions that are created during the "end" event of an earlier transition) are considered the same "age" as the original transition; internally this is tracked by monotonically-increasing unique IDs which are inherited when multi-stage transitions are created.

## Starting Transitions

Transitions are created using the [[transition|Selections#transition]] operator on a selection. Transitions start automatically upon creation after a delay which defaults to zero; however, note that a zero-delay transition actually starts after a minimal (<10ms) delay, pending the first timer callback. Transitions have a default duration of 250ms.

<a name="d3_transition" href="#d3_transition">#</a> d3.<b>transition</b>()

Create an animated transition. This is equivalent to `d3.select(document).transition()`. This method is used rarely, as it is typically easier to derive a transition from an existing selection, rather than deriving a selection from an existing transition.

<a name="delay" href="#delay">#</a> transition.<b>delay</b>(<i>delay</i>)

Specifies the transition *delay* in milliseconds. If *delay* is a constant, then all elements are given the same delay; otherwise, if *delay* is a function, then the function is evaluated for each selected element (in order), being passed the current datum `d` and the current index `i`, with the `this` context as the current DOM element. The function's return value is then used to set each element's delay. The default delay is 0.

Setting the delay to be a multiple of the index `i` is a convenient way to stagger transitions for elements. For example, if you used a fixed duration of *duration*, and have *n* elements in the current selection, you can stagger the transition over 2 \* *duration* by saying:

```javascript
.delay(function(d, i) { return i / n * duration; })
```

You may also compute the delay as a function of the data, thereby creating a data-driven animation.

<a name="duration" href="#duration">#</a> transition.<b>duration</b>(<i>duration</i>)

Specifies per-element *duration* in milliseconds. If *duration* is a constant, then all elements are given the same duration; otherwise, if *duration* is a function, then the function is evaluated for each selected element (in order), being passed the current datum `d` and the current index `i`, with the `this` context as the current DOM element. The function's return value is then used to set each element's duration. The default duration is 250ms.

<a name="ease" href="#ease">#</a> transition.<b>ease</b>(<i>value</i>[, <i>arguments</i>])

Specifies the transition [[easing function|http://www.robertpenner.com/easing/]]. If *value* is a function, it is used to ease the current parametric timing value *t* in the range [0,1]; otherwise, *value* is assumed to be a string and the arguments are passed to the [d3.ease](#d3_ease) method to generate an easing function. The default easing function is "cubic-in-out". Note that it is not possible to customize the easing function per-element or per-attribute; however, if you use the "linear" easing function, you can apply custom easing inside your interpolator using [attrTween](#attrTween) or [styleTween](#styleTween).

## Operating on Transitions

### Content

<a name="attr" href="#attr">#</a> transition.<b>attr</b>(<i>name</i>, <i>value</i>)

Transitions the value of the attribute with the specified *name* to the specified *value*. The starting value of the transition is the current attribute value, and the ending value is the specified *value*.  If *value* is a constant, then all elements are transitioned to the same attribute value; otherwise, if *value* is a function, then the function is evaluated for each selected element (in order) as the element starts transitioning, being passed the current datum `d` and the current index `i`, with the `this` context as the current DOM element. The function's return value is then used to transition each element's attribute. Null values are not supported; if you want to remove the attribute after the transition finishes, listen to the [end](#each) event.

An interpolator is selected automatically based on the ending value. If the ending value is a number, the starting value is coerced to a number and [interpolateNumber](#interpolateNumber) is used. If the ending value is a string, a check is performed to see if the string represents a color of the form `/^(#|rgb\(|hsl\()/`, or one of the [[CSS named colors|http://www.w3.org/TR/SVG/types.html#ColorKeywords]]; if so, the starting value is coerced to an RGB color and [interpolateRgb](#interpolateRgb) is used. Otherwise, [interpolateString](#interpolateString) is used, which interpolates numbers embedded within strings.

<a name="attrTween" href="#attrTween">#</a> transition.<b>attrTween</b>(<i>name</i>, <i>tween</i>)

Transitions the value of the attribute with the specified *name* according to the specified *tween* function. The starting and ending value of the transition are determined by *tween*; the *tween* function is invoked when the transition starts on each element, being passed the current datum `d`, the current index `i` and the current attribute value `a`, with the `this` context as the current DOM element. The return value of *tween* must be an interpolator: a function that maps a parametric value *t* in the domain [0,1] to a color, number or arbitrary value.

For example, the attr operator is built on top of the attrTween operator. The tween function used by the attr operator depends on whether the end value is a function or a constant. If the end value is a function:

```javascript
function tween(d, i, a) {
  return d3.interpolate(a, String(value.call(this, d, i)));
}
```

Otherwise, if the end value is a constant:

```javascript
function tween(d, i, a) {
  return d3.interpolate(a, String(value));
}
```

The attrTween operator is used when you need a custom interpolator, such as one that understands the semantics of SVG path data. One common technique is *dataspace interpolation*, where [interpolateObject](#interpolateObject) is used to interpolate two data values, and the result of this interpolation is then used (say, with a [[shape|SVG-Shapes]]) to compute the new attribute value. Use the attr operator for the simpler common case where an interpolator can be automatically derived from the current attribute value to the desired end value.

<a name="style" href="#style">#</a> transition.<b>style</b>(<i>name</i>, <i>value</i>[, <i>priority</i>])

Transitions the value of the CSS style property with the specified *name* to the specified *value*. An optional *priority* may also be specified, either as null or the string "important" (without the exclamation point). The starting value of the transition is the current computed style property value, and the ending value is the specified *value*.  If *value* is a constant, then all elements are transitioned to the same style property value; otherwise, if *value* is a function, then the function is evaluated for each selected element (in order) as the element starts transitioning, being passed the current datum `d` and the current index `i`, with the `this` context as the current DOM element. The function's return value is then used to transition each element's style property. Null values are not supported; if you want to remove the style property after the transition finishes, listen to the [end](#each) event.

An interpolator is selected automatically based on the ending value. If the ending value is a number, the starting value is coerced to a number and [interpolateNumber](#interpolateNumber) is used. If the ending value is a string, a check is performed to see if the string represents a color of the form `/^(#|rgb\(|hsl\()/`, or one of the [[CSS named colors|http://www.w3.org/TR/SVG/types.html#ColorKeywords]]; if so, the starting value is coerced to an RGB color and [interpolateRgb](#interpolateRgb) is used. Otherwise, [interpolateString](#interpolateString) is used, which interpolates numbers embedded within strings.

Note that the computed starting value may be different than the value that was previously set, particularly if the style property was set using a shorthand property (such as the "font" style, which is shorthand for "font-size", "font-face", etc.).

<a name="styleTween" href="#styleTween">#</a> transition.<b>styleTween</b>(<i>name</i>, <i>tween</i>[, <i>priority</i>])

Transitions the value of the CSS style property with the specified *name* according to the specified *tween* function. An optional *priority* may also be specified, either as null or the string "important" (without the exclamation point). The starting and ending value of the transition are determined by *tween*; the *tween* function is invoked when the transition starts on each element, being passed the current datum `d`, the current index `i` and the current attribute value `a`, with the `this` context as the current DOM element. The return value of *tween* must be an interpolator: a function that maps a parametric value *t* in the domain [0,1] to a color, number or arbitrary value.

For example, the style operator is built on top of the styleTween operator. The tween function used by the style operator depends on whether the end value is a function or a constant. If the end value is a function:

```javascript
function tween(d, i, a) {
  return d3.interpolate(a, String(value.call(this, d, i)));
}
```

Otherwise, if the end value is a constant:

```javascript
function tween(d, i, a) {
  return d3.interpolate(a, String(value));
}
```

The styleTween operator is used when you need a custom interpolator, such as one that understands the semantics of CSS3 transforms. Use the style operator for the simpler common case where an interpolator can be automatically derived from the current computed style property value to the desired end value.

<a name="text" href="#text">#</a> transition.<b>text</b>(<i>value</i>)

The `text` operator is based on the [[textContent|http://www.w3.org/TR/DOM-Level-3-Core/core.html#Node3-textContent]] property; setting the text content will replace any existing child elements.

Set the text content to the specified value on all selected elements when the transition starts. If *value* is a constant, then all elements are given the same text content; otherwise, if *value* is a function, then the function is evaluated for each selected element (in order) as the element starts transitioning, being passed the current datum `d` and the current index `i`, with the `this` context as the current DOM element. The function's return value is then used to set each element's text content. A null value will clear the content.

<a name="remove" href="#remove">#</a> transition.<b>remove</b>()

Remove the selected elements at the end of a transition. If a newer transition is scheduled on any of the selected elements, these elements will not be removed; however, the "end" event will still be dispatched.

### Subtransitions

Transitions may be derived from existing transitions, in a similar manner to subselections. Subtransitions inherit easing, duration and delay from the parent transition.

<a name="select" href="#select">#</a> transition.<b>select</b>(<i>selector</i>)

For each element in the current transition, selects the first descendant element that matches the specified *selector* string. If no element matches the specified selector for the current element, the element at the current index will be null in the returned selection; operators (with the exception of [data](#data)) automatically skip null elements, thereby preserving the index of the existing selection. If the current element has associated data, this data is inherited by the returned subselection, and automatically bound to the newly selected elements. If multiple elements match the selector, only the first matching element in document traversal order will be selected.

This method is approximately equivalent to:

```javascript
selection.select(selector).transition()
```

where *selection* is the current transition's underlying selection. In addition, the returned new transition inherits easing, duration and delay from the current transition.

<a name="selectAll" href="#selectAll">#</a> transition.<b>selectAll</b>(<i>selector</i>)

For each element in the current transition, selects descendant elements that match the specified *selector* string. The returned selection is grouped by the ancestor node in the current selection. If no element matches the specified selector for the current element, the group at the current index will be empty in the returned selection. The subselection does not inherit data from the current selection; however, if data was previously bound to the selected elements, that data will be available to operators.

This method is approximately equivalent to:

```javascript
selection.selectAll(selector).transition()
```

where *selection* is the current transition's underlying selection. In addition, the returned new transition inherits easing, duration and delay from the current transition. The duration and delay for each subelement is inherited from the duration and delay of the parent element in the current transition.

### Control

<a name="each" href="#each">#</a> transition.<b>each</b>(<i>type</i>, <i>listener</i>)

Add a listener for transition events, supporting both "start" and "end" events. The listener will be invoked for each individual element in the transition, even if the transition has a constant delay and duration. The start event can be used to trigger an instantaneous change as each element starts to transition. The end event can be used to initiate multi-stage transitions by selecting the current element, `this`, and deriving a new transition. Any transitions created during the end event will inherit the current transition ID, and thus will not override a newer transition that was previously scheduled.

Note: there is currently no way to remove listeners. And, this operator has the same name as the selection [[each|Selections#each]] operator, which is somewhat confusing. It should probably be renamed; see [[#168|https://github.com/mbostock/d3/issues/168]].

<a name="call" href="#call">#</a> transition.<b>call</b>(<i>function</i>[, <i>arguments…</i>])

Invokes the specified *function* once, passing in the current transition along with any optional *arguments*. The call operator always returns the current transition, regardless of the return value of the specified function. The call operator is identical to invoking a function by hand; but it makes it easier to use method chaining. For example, say we want to set a number of attributes the same way in a number of different places. So we take the code and wrap it in a reusable function:

```javascript
function foo(transition) {
  transition
      .attr("name1", "value1")
      .attr("name2", "value2");
}
```

Now, we can say this:

```javascript
foo(d3.selectAll("div").transition())
```

Or equivalently:

```javascript
d3.selectAll("div").transition().call(foo);
```

In many cases, it is possible to call the same function *foo* on both transitions and selections, due to identical methods on both selections and transitions! The `this` context of the called function is also the current transition. This is slightly redundant with the first argument, which we might fix in the future.

## Easing

<a name="d3_ease" href="#d3_ease">#</a> d3.<b>ease</b>(<i>type</i>[, <i>arguments…</i>])

Returns a built-in easing function of the specified *type*, with any optional *arguments*. An easing function takes the current parameterized time value *t* in the domain [0,1], and maps it to another value in a similar range; it is typically used to set transition [easing](#ease). The following easing types are supported:

* linear - the identity function, *t*.
* poly(k) - raises *t* to the specified power *k* (e.g., 3).
* quad - equivalent to poly(2).
* cubic - equivalent to poly(3).
* sin - applies the trigonometric function *sin*.
* exp - raises 2 to a power based on *t*.
* circle - the quarter circle.
* elastic(a, p) - simulates an elastic band; may extend slightly beyond 0 and 1.
* back(s) - simulates backing into a parking space.
* bounce - simulates a bouncy collision.

These built-in types may be extended using a variety of modes:

* in - the identity function.
* out - reverses the easing direction to [1,0].
* in-out - copies and mirrors the easing function from [0,.5] and [.5,1].
* out-in - copies and mirrors the easing function from [1,.5] and [.5,0].

The default easing function is "cubic-in-out" which provides suitable [[slow-in slow-out|http://en.wikipedia.org/wiki/12_basic_principles_of_animation#Slow_in_and_slow_out]] animation.

## Timers

D3 internally maintains an efficient timer queue so that thousands of timers can be processed concurrently with minimal overhead; in addition, this timer queue guarantees consistent timing of animations when concurrent or staged transitions are scheduled. If your browser supports it, the timer queue will use [[requestAnimationFrame|http://paulirish.com/2011/requestanimationframe-for-smart-animating/]] for fluid and efficient animation. The timer queue is also smart about using setTimeout when there is a long delay before the next scheduled event.

<a name="d3_timer" href="#d3_timer">#</a> d3.<b>timer</b>(<i>function</i>)

Start a custom animation timer, invoking the specified *function* repeatedly until it returns true. There is no way to cancel the timer after it starts, so make sure your timer function returns true when done!

<a name="d3_timer_flush" href="#d3_timer_flush">#</a> d3.timer.<b>flush</b>()

Immediately execute any zero-delay timers. Normally, zero-delay transitions are executed after an instantaneous delay (<10ms). This can cause a brief flicker if the browser renders the page twice: once at the end of the first event loop, then again immediately on the first timer callback. By flushing the timer queue at the end of the first event loop, you can run any zero-delay transitions immediately and avoid the flicker.

## Interpolation

D3 has many built-in interpolators to simplify the transitioning of arbitrary values; an interpolator is a function that maps a parametric value *t* in the domain [0,1] to a color, number or arbitrary value.

<a name="d3_interpolate" href="#d3_interpolate">#</a> d3.<b>interpolate</b>(<i>a</i>, <i>b</i>)

Returns the default interpolator between the two values *a* and *b*. The type of interpolator is based on the type of the end value *b*. If *b* is a number, *a* is coerced to a number and [interpolateNumber](#interpolateNumber) is used. If *b* is a string, a check is performed to see if *b* represents a color of the form `/^(#|rgb\(|hsl\()/`, or one of the [[CSS named colors|http://www.w3.org/TR/SVG/types.html#ColorKeywords]]; if *b* is a color, *a* is coerced to an RGB color and [interpolateRgb](#interpolateRgb) is used. Otherwise, [interpolateString](#interpolateString) is used, which interpolates numbers embedded within strings. The behavior of this default interpolator may be extended to support additional types by pushing custom interpolators onto the [d3.interpolators](#d3_interpolators) array.

<a name="d3_interpolateNumber" href="#d3_interpolateNumber">#</a> d3.<b>interpolateNumber</b>(<i>a</i>, <i>b</i>)

Returns a numeric interpolator between the two numbers *a* and *b*. The returned interpolator is equivalent to:

```javascript
function interpolate(t) {
  return a * (1 - t) + b * t;
}
```

Caution: avoid interpolating to or from the number zero when the interpolator is used to generate a string (such as with [attr](#attr)). Very small values, when stringified, may be converted to scientific notation and cause a temporarily invalid attribute or style property value. For example, the number 0.0000001 is converted to the string "1e-7". This is particularly noticeable when interpolating opacity values. To avoid scientific notation, start or end the transition at 1e-6, which is the smallest value that is not stringified in exponential notation.

<a name="d3_interpolateRound" href="#d3_interpolateRound">#</a> d3.<b>interpolateRound</b>(<i>a</i>, <i>b</i>)

Returns a numeric interpolator between the two numbers *a* and *b*; the interpolator is similar to [interpolateNumber](#interpolateNumber), except it will round the resulting value to the nearest integer.

<a name="d3_interpolateString" href="#d3_interpolateString">#</a> d3.<b>interpolateString</b>(<i>a</i>, <i>b</i>)

Returns a string interpolator between the two strings *a* and *b*. The string interpolator finds numbers embedded in *a* and *b*, where each number is of the form:

```javascript
/[-+]?(?:\d+\.\d+|\d+\.|\.\d+|\d+)(?:[eE][-]?\d+)?/
```

For each number embedded in *b*, the interpolator will attempt to find a corresponding number in *a*. If a corresponding number is found, a numeric interpolator is created using [interpolateNumber](#interpolateNumber). The remaining parts of the string *b* are used as a template: the static parts of the string *b* remain constant for the interpolation, with the interpolated numeric values embedded in the template. For example, if *a* is "300 12px sans-serif", and *b* is "500 36px Comic-Sans", two embedded numbers are found. The remaining static parts of the string are a space between the two numbers (" "), and the suffix ("px Comic-Sans"). The result of the interpolator at *t* = .5 is "400 24px Comic-Sans".

<a name="d3_interpolateRgb" href="#d3_interpolateRgb">#</a> d3.<b>interpolateRgb</b>(<i>a</i>, <i>b</i>)

Returns an RGB color space interpolator between the two colors *a* and *b*. The colors *a* and *b* need not be in RGB, but they will be converted to RGB using [[d3.rgb|Colors#d3_rgb]]. The red, green and blue channels are interpolated linearly in a manner equivalent to [interpolateRound](#interpolateRound), as fractional channel values are not allowed. The return value of the interpolator is always a string representing the RGB color, such as "rgb(255,0,0)" for red.

<a name="d3_interpolateHsl" href="#d3_interpolateHsl">#</a> d3.<b>interpolateHsl</b>(<i>a</i>, <i>b</i>)

Returns an HSL color space interpolator between the two colors *a* and *b*. The colors *a* and *b* need not be in HSL, but they will be converted to HSL using [[d3.hsl|Colors#d3_hsl]]. The hue, saturation and lightness are interpolated linearly in a manner equivalent to [interpolateNumber](#interpolateNumber). (Thus, the shortest path between the start and end hue is not necessarily used.) The return value of the interpolator is always a string representing the RGB color, such as "#ff0000" for red; an RGB color string is returned for browser compatibility, as not all browsers support HSL colors in CSS.

<a name="d3_interpolateArray" href="#d3_interpolateArray">#</a> d3.<b>interpolateArray</b>(<i>a</i>, <i>b</i>)

Returns an array interpolator between the two arrays *a* and *b*. Internally, an array template is created that is the same length in *b*. For each element in *b*, if there exists a corresponding element in *a*, a generic interpolator is created for the two elements using [interpolate](#interpolate). If there is no such element, the static value from *b* is used in the template. Then, for the given parameter *t*, the template's embedded interpolators are evaluated. The updated array template is then returned. For example, if *a* is the array [0, 1] and *b* is the array [1, 10, 100], then the result of the interpolator for *t* = .5 is the array [.5, 5.5, 100].

Note: no defensive copy of the template array is created; modifications of the returned array may adversely affect subsequent evaluation of the interpolator. No copy is made because interpolators should be fast, as they are part of the inner loop of animation.

<a name="d3_interpolateObject" href="#d3_interpolateObject">#</a> d3.<b>interpolateObject</b>(<i>a</i>, <i>b</i>)

Returns an object interpolator between the two objects *a* and *b*. Internally, an object template is created that has the same properties as *b*. For each property in *b*, if there exists a corresponding property in *a*, a generic interpolator is created for the two elements using [interpolate](#interpolate). If there is no such property, the static value from *b* is used in the template. Then, for the given parameter *t*, the template's embedded interpolators are evaluated and the updated object template is then returned. For example, if *a* is the object {x: 0, y: 1} and *b* is the object {x: 1, y: 10, z: 100}, the result of the interpolator for *t* = .5 is the object {x: .5, y: 5.5, z: 100}.

Object interpolation is particularly useful for *dataspace interpolation*, where data is interpolated rather than attribute values. For example, you can interpolate an object which describes an arc in a pie chart, and then use [[d3.svg.arc|SVG-Shapes#arc]] to compute the new SVG path data.

Note: no defensive copy of the template object is created; modifications of the returned object may adversely affect subsequent evaluation of the interpolator. No copy is made because interpolators should be fast, as they are part of the inner loop of animation.

<a name="d3_interpolators" href="#d3_interpolators">#</a> d3.<b>interpolators</b>

The array of built-in interpolator factories, as used by [d3.interpolate](#d3_interpolate). Additional interpolator factories may be pushed onto the end of this array. Each factory may return an interpolator, if it supports interpolating the two specified input values; otherwise, the factory should return a falsey value and other interpolators will be tried. The initial value of this array, in the order of evaluation, is:

* interpolateNumber - if the type is number.
* interpolateRgb - if the type is a color.
* interpolateString - if the type is a string.
* interpolateArray - if the type is an array.
* interpolateObject - as a last resort.

For example, to register a custom interpolator that formats dollars and cents, you might say:

```javascript
d3.interpolators.push(function(a, b) {
  var re = /^\$([0-9,.]+)$/, ma, mb, f = d3.format(",.02f");
  if ((ma = re.exec(a)) && (mb = re.exec(b))) {
    a = parseFloat(ma[1]);
    b = parseFloat(mb[1]) - a;
    return function(t) {
      return "$" + f(a + b * t);
    };
  }
});
```

Then, d3.interpolate("$20", "$10")(1/3) returns $16.67.