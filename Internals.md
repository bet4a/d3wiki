> [[API Reference]] ▸ [[Core]]

D3 has a few internal methods defined in the core module that are re-used by other modules; these are not considered part of the public API and should be used with caution outside of D3 as they are not guaranteed to remain backwards-compatible.

## Functions

<a name="functor" href="Internals#wiki-functor">#</a> d3.<b>functor</b>(<i>value</i>)

If the specified *value* is a function, returns the specified value. Otherwise, returns a function that returns the specified value. This method is used internally as a lazy way of upcasting constant values to functions, in cases where a property may be specified either as a function or a constant. For example, many D3 layouts allow properties to be specified this way, and it simplifies the implementation if we automatically convert constant values to functions.

<a name="rebind" href="Internals#wiki-rebind">#</a> d3.<b>rebind</b>(<i>object</i>, <i>function</i>)

Wraps the specified *function*. If the returned function is called with no arguments, *function* is invoked and its return value is returned; this is the "getter" mode. If the returned function is called with any arguments, *function* is invoked and *object* is returned; this is the "setter" mode. The rebind operator allows inherited methods (mix-ins) to be rebound to a subclass on a different object.

## Events

D3 uses a dispatcher to handle custom events.

<a name="d3_dispatch" href="Internals#wiki-d3_dispatch">#</a> d3.<b>dispatch</b>(<i>types…</i>)

Creates a new dispatcher object for the specified *types*. Each argument is a string representing the name of the event type, such as "zoom" or "change". The returned object is an associative array; each type name is associated with a dispatch object. For example, if you wanted to create an event dispatcher for "start" and "end" events, you can say:

```javascript
var event = d3.dispatch("start", "end");
```

Then, you can access the dispatchers for the different event types as `event.start` and `event.end`. For example, you might add an event listener:

```javascript
event.start.add(listener);
```

And then later dispatch an event to all registered listeners:

```javascript
event.start.dispatch();
```

The `dispatch` method will preserve the context in which it is called, and pass any arguments, along to the registered listeners. Thus, by passing different arguments to the dispatch method, you can pass whatever arguments you want to the listeners; most commonly, you might create an object that represents the event, or pass along the current datum (*d*) and index (*i*). You can also control the "this" context of the listeners using [call](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Function/Call) or [apply](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Function/Apply).

<a name="dispatch_add" href="Internals#wiki-dispatch_add">#</a> dispatch.<b>add</b>(<i>listener</i>)

Adds the specified *listener* to this dispatcher. If the *listener* is already registered, this method has no effect.

<a name="dispatch_remove" href="Internals#wiki-dispatch_remove">#</a> dispatch.<b>remove</b>(<i>listener</i>)

Removes the specified *listener* from this dispatcher. If the *listener* is not registered, this method has no effect.

<a name="dispatch_dispatch" href="Internals#wiki-dispatch_dispatch">#</a> dispatch.<b>dispatch</b>(<i>arguments…</i>)

Notifies each registered listener, passing the listener the specified *arguments*. The `this` context of the dispatch method will be used as the context of the registered listeners. For example, to invoke all registered listeners with the context *foo* and the argument *bar*, say dispatch.call(*foo*, *bar*).