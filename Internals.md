> [Wiki](Home) ▸ [[API Reference]] ▸ [[Core]] ▸ **Internals**

D3 has a few internal methods defined in the core module that are re-used by other modules; these are not considered part of the public API and should be used with caution outside of D3 as they are not guaranteed to remain backwards-compatible.

## Functions

<a name="functor" href="Internals#wiki-functor">#</a> d3.<b>functor</b>(<i>value</i>)

If the specified *value* is a function, returns the specified value. Otherwise, returns a function that returns the specified value. This method is used internally as a lazy way of upcasting constant values to functions, in cases where a property may be specified either as a function or a constant. For example, many D3 layouts allow properties to be specified this way, and it simplifies the implementation if we automatically convert constant values to functions.

<a name="rebind" href="Internals#wiki-rebind">#</a> d3.<b>rebind</b>(<i>target</i>, <i>source</i>, <i>names…</i>)

Copies the methods with the specified *names* from *source* to *target*, and returns *target*. If a method is called with no arguments, it is invoked and its return value is returned (“getter” mode). If the method is called with arguments, it is invoked and *target* is returned (“setter” mode). The rebind operator allows inherited methods (mix-ins) to be rebound to a subclass on a different object.

## Events

D3 uses a dispatcher to handle custom events.

<a name="d3_dispatch" href="Internals#wiki-d3_dispatch">#</a> d3.<b>dispatch</b>(<i>types…</i>)

Creates a new dispatcher object for the specified *types*. Each argument is a string representing the name of the event type, such as "zoom" or "change". The returned object is an associative array; each type name is associated with a dispatch object. For example, if you wanted to create an event dispatcher for "start" and "end" events, you can say:

```javascript
var dispatch = d3.dispatch("start", "end");
```

Then, you can access the dispatchers for the different event types as `event.start` and `event.end`. For example, you might add an event listener:

```javascript
dispatch.on("start", listener);
```

And then later dispatch an event to all registered listeners:

```javascript
dispatch.start();
```

For details on how to pass arguments to listeners, see [dispatch](#wiki-dispatch).

<a name="dispatch_on" href="Internals#wiki-dispatch_on">#</a> dispatch.<b>on</b>(<i>type</i>[, <i>listener</i>])

Adds or removes an event *listener* for the specified *type*. The *type* is a string event type name, such as "start" or "end".  The specified *listener* is invoked with the context and arguments determined by the caller; see [dispatch](#wiki-dispatch). 

If an event listener was already registered for the same type, the existing listener is removed before the new listener is added. To register multiple listeners for the same event type, the type may be followed by an optional namespace, such as "click.foo" and "click.bar".

If *listener* is not specified, returns the currently-assigned listener for the specified *type*, if any.

<a name="dispatch" href="Internals#wiki-dispatch">#</a> dispatch.<b>type</b>(<i>arguments…</i>)

The *type* method (such as `dispatch.start` in the above example) notifies each registered listener, passing the listener the specified *arguments*. The `this` context will be used as the context of the registered listeners. For example, to invoke all registered listeners with the context *foo* and the argument *bar*, say dispatch.call(*foo*, *bar*). Thus, you can pass whatever arguments you want to the listeners; most commonly, you might create an object that represents the event, or pass along the current datum (*d*) and index (*i*). You can also control the "this" context of the listeners using [call](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Function/Call) or [apply](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Function/Apply).

For example, if you wanted a native "click" event to your "custom" event, while preserving the context and arguments, you could say:

```javascript
selection.on("click", function(d, i) {
  dispatch.custom.apply(this, arguments);
});
```