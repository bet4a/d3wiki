## Release Notes

### 2.0.0 - August 23, 2011

The enter selection now merges into the update selection when you append or insert. This means you no longer need to re-select after entering new nodes; those new nodes will be automatically merged into the update selection.

A new **axis** component has been added to the d3.svg module.

Transitions are now arrays of elements, just like selections. You can now inspect them in the developer console. Each array is wrapped in an object that stores the delay and duration of the associated transition. Transition's `each` operator can now be called with one argument, with the same behavior as selection. Transitions also expose an `id` property, which can be useful for debugging concurrent transitions; this id is inherited by subtransitions, fixing a bug where nested transitions would compete for element ownership.

Selection's `select` and `selectAll` operators can now take functions.

Selection and transition are now defined using **prototype injection** rather than direct extension. This improves performance and reduces memory overhead, as the majority of methods are defined on the object's prototype rather than on each instance. Also, it makes the code cleaner as each operator is fully separable and defined in its own source file. This also fixes a few bugs, such as the missing `empty` operator on the enter selection. Prototype injection also means that selections and transitions can be extended! You can now override the behavior of D3's core operators, or add your own. This may be particularly useful to provide compatibility with nonstandard browsers. You can also use JavaScript's `instanceof` operator to see whether an object is a `d3.selection` or `d3.transition` instance.

Transition has a new `tween` operator which is used internally by all the other tweens (`style`, `attr`, *etc.*). You can use this operator directly if you want to define a custom tween as part of the transition; use this instead of listening for a transition "tick" event.
