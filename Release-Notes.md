# Release Notes

## 2.0.0 - August 23, 2011

### Enter and Update

The **enter-update** pattern has been simplified: the [enter](Selections#wiki-enter) selection now merges into the [update](Selections#wiki-data) selection when you append or insert. This new approach reduces code duplication between enter and update. Rather than applying operators to both the enter and update selection separately, you can now apply them to the update selection after entering the nodes.

For example, say you had a selection of circles and wanted to update their radii. Previously you had to call the attr operator twice, once for enter and once for update:

```javascript
var circle = svg.selectAll("circle").data([data]);
circle.exit().remove();
circle.enter().append("svg:circle").attr("r", radius); // for enter
circle.attr("r", radius); // for update
```

In addition, if you wanted `circle` to refer to all the on-screen nodes (enter plus update) subsequently, you'd have to reselect as well to merge the enter and update selections:

```javascript
circle = svg.selectAll("circle"); // reselect
```

In 2.0, you can eliminate this duplicate code because entering nodes will add them to *both* the enter selection and the update selection. Running operators on the update selection after enter will thus apply to both entering and updating nodes:

```javascript
var circle = svg.selectAll("circle").data([data]);
circle.exit().remove();
circle.enter().append("svg:circle"); // adds enter to update
circle.attr("r", radius); // for enter and update
```

Note: if you want to run operators only on the updating nodes, you can run them on the update selection before entering new nodes.

### Selector Functions

The [select](Selections#wiki-select) and (selectAll)[Selections#wiki-selectAll] operators can now take **selector functions**, in addition to selector strings. For example, if you want to select the first child of every element, you can say:

```javascript
var children = g.select(function() { return this.firstChild; });
```

If you want, you could even create new elements dynamically and insert them into the DOM. This is an advanced feature, but might be useful for more advanced selection and creation. For example, you could use XPath rather than selectors if you wanted.

### Transparent Transitions

Transitions are now **transparent** arrays of elements, and you can inspect them in the developer console just like selections. Each selected element is wrapped in an object that stores the delay and duration of the associated transition. (Recall that these values are computed on a per-element basis for staggered animations.) Internally, some of the timing logic that manages transitions has also been cleaned up, improving performance and fixing a few timing bugs.

The [each](Transitions#wiki-each) operator can now be called with one argument (a callback function), offering compatibility with the selection's [each](Selections#wiki-each) operator. Transitions now expose an [id](Transitions#wiki-id) property, which can be useful for debugging concurrent transitions; this identifier is inherited by subtransitions, fixing a bug with nested transitions.

### Custom Tweens

A new, generic [tween](Transitions#wiki-tween) operator is used internally by all the other tweens (`style`, `attr`, *etc.*). You can use this operator directly if you want to define a custom tween as part of the transition; use this instead of listening for a transition "tick" event. For example, the `text` operator does not interpolate by default. You can now interpolate text content by saying:

```javascript
selection.transition().tween("text", function() {
  var i = d3.interpolate(this.textContent, "yellow");
  return function(t) {
    this.textContent = i(t);
  };
});
```

Of course, you might want to write your tweens as reusable functions (say, closures) rather than the above example which hard-codes the transition to "yellow". See the built-in attr and style tweens for inspiration.

### SVG

A new **axis** component has been added to the d3.svg module.

### Extending and Overriding

Selection and transition are now defined using [prototype injection](http://perfectionkills.com/how-ecmascript-5-still-does-not-allow-to-subclass-an-array/) rather than direct extension. This improves performance and reduces memory overhead, as the majority of methods are defined on the object's prototype rather than on each instance. Also, it makes the code cleaner as each operator is fully separable and defined in its own source file. This fixed a few bugs, such as the missing [empty](Selections#wiki-empty) operator on enter selections.

Prototype injection also means that selections and transitions can be extended! You can now override the behavior of D3's core operators, or add your own. This may be particularly useful to provide compatibility with nonstandard browsers. You can also use JavaScript's `instanceof` operator to see whether an object is a `d3.selection` or `d3.transition`.

### Tests

D3 now has an extensive test suite built with [Vows](http://vowsjs.org). As of the 2.0.0 release, we have 1,200+ tests and 90% coverage of the core library. More tests are under development. The tests are written to test the behavior of each of D3's operators, and may be interesting to explore if you have questions about how D3 works, complementing the API reference.
