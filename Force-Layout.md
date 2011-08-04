> [[API Reference]] ▸ [[Layouts]]

A flexible force-directed graph layout implementation using position [Verlet integration](http://en.wikipedia.org/wiki/Verlet_integration) to allow [simple constraints](http://www.csse.monash.edu.au/~tdwyer/Dwyer2009FastConstraints.pdf). For more on physical simulations, see [Thomas Jakobsen](http://www.gamasutra.com/resource_guide/20030121/jacobson_pfv.htm). This implementation uses a [quadtree](Quadtree-Geom) to accelerate charge interaction using the [Barnes–Hut approximation](http://en.wikipedia.org/wiki/Barnes%E2%80%93Hut_simulation). In addition to the repulsive [charge](#charge) force, a pseudo-[gravity](#gravity) force keeps nodes centered in the visible area and avoids expulsion of disconnected subgraphs, while links are fixed-[distance](#distance) geometric constraints. Additional custom forces and constraints may be applied on the "tick" event, simply by updating the *x* and *y* attributes of nodes.

![force](force.png)

Some fun examples:

* [divergent forces](http://bl.ocks.org/1021841)
* [multiple foci](http://bl.ocks.org/1021953)
* [graph constructor](http://bl.ocks.org/929623)
* [force-directed tree](http://bl.ocks.org/1062288)
* [force-directed symbols](http://bl.ocks.org/1062383)
* [force-directed images and labels](http://bl.ocks.org/950642)
* [force-directed states](http://bl.ocks.org/1073373)

Like other classes in D3, layouts follow the method chaining pattern where setter methods return the layout itself, allowing multiple setters to be invoked in a concise statement. Unlike some of the other layout implementations which are stateless, the force layout keeps a reference to the associated nodes and links internally; thus, a given force layout instance can only be used with a single dataset.

Note: this layout depends on [d3.geom.quadtree](Quadtree-Geom), so you must load d3.geom.js, or build a custom d3.js that includes d3.geom.quadtree.

<a name="force" href="Force-Layout#force">#</a> d3.layout.<b>force</b>()

Constructs a new force-directed layout with the default settings: size 1×1, friction 0.9, distance 20, charge strength -30, gravity strength 0.1, and theta parameter 0.8. The default nodes and links are the empty array, and when the layout is started, the internal alpha cooling parameter is set to 0.1. The general pattern for constructing force-directed layouts is to set all the configuration properties, and then call [start](#start):

```javascript
var force = d3.layout.force()
    .nodes(nodes)
    .links(links)
    .size([w, h])
    .start();
```

Note that, like D3's other layouts, the force-directed layout doesn't mandate a particular visual representation. Most commonly, nodes are mapped to SVG circle elements, and links are mapped to SVG line elements. But you might also display nodes as [symbols](http://bl.ocks.org/1062383) or [images](http://bl.ocks.org/950642).

<a name="size" href="Force-Layout#size">#</a> force.<b>size</b>([<i>size</i>])

If *size* is specified, sets the available layout size to the specified two-element array of numbers representing *x* and *y*. If *size* is not specified, returns the current size, which defaults to 1×1. The size affects two aspects of the force-directed layout: the gravitational center, and the initial random position. The center of gravity is simply [*x* / 2, *y* / 2]. When nodes are added to the force layout, if they do not have *x* and *y* attributes already set, then these attributes are initialized using a uniform random distribution in the range [0, *x*] and [0, *y*], respectively.

<a name="linkDistance" href="Force-Layout#linkDistance">#</a> force.<b>linkDistance</b>([<i>distance</i>])

If *distance* is specified, sets the target distance between linked nodes to the specified value. If *distance* is not specified, returns the layout's current link distance, which defaults to 20. If *distance* is a constant, then all links are the same distance. Otherwise, if *distance* is a function, then the function is evaluated for each link (in order), being passed the link and its index, with the `this` context as the force layout; the function's return value is then used to set each link's distance. The function is evaluated whenever the layout [starts](#start). Typically, the distance is specified in pixels; however, the units are arbitrary relative to the layout's [size](#size).

Links are not implemented as "spring forces", as in common in other force-directed layouts, but as weak geometric constraints. For each tick of the layout, the distance between each pair of linked nodes is computed and compared to the target distance; the links are then moved towards each other, or away from each other, so as to converge on the desired distance. This method of constraints relaxation on top of position Verlet integration is vastly more stable than previous methods using spring forces, and also allows for the flexible implementation of [other constraints](http://www.csse.monash.edu.au/~tdwyer/Dwyer2009FastConstraints.pdf) in the tick event listener, such as hierarchical layering.

<a name="linkStrength" href="Force-Layout#linkStrength">#</a> force.<b>linkStrength</b>([<i>strength</i>])

If *strength* is specified, sets the strength (rigidity) of links to the specified value in the range [0,1]. If *strength* is not specified, returns the layout's current link strength, which defaults to 1. If *strength* is a constant, then all links have the same strength. Otherwise, if *strength* is a function, then the function is evaluated for each link (in order), being passed the link and its index, with the `this` context as the force layout; the function's return value is then used to set each link's strength. The function is evaluated whenever the layout [starts](#start).

<a name="friction" href="Force-Layout#friction">#</a> force.<b>friction</b>([<i>friction</i>])

If *friction* is specified, sets the friction coefficient to the specified value. If *friction* is not specified, returns the current coefficient, which defaults to 0.9. The name of this parameter is perhaps misleading; it does not correspond to a standard physical [coefficient of friction](http://en.wikipedia.org/wiki/Friction#Coefficient_of_friction). Instead, it more closely approximates velocity decay: at each tick of the simulation, the particle velocity is scaled by the specified *friction*. Thus, a value of 1 corresponds to a frictionless environment, while a value of 0 freezes all particles in place. Values outside the range [0,1] are not recommended and may have destabilizing effects.

<a name="charge" href="Force-Layout#charge">#</a> force.<b>charge</b>([<i>charge</i>])

If *charge* is specified, sets the charge strength to the specified value. If *charge* is not specified, returns the current charge strength, which defaults to -30. A negative value results in node repulsion, while a positive value results in node attraction. For graph layout, negative values should be used; for [*n*-body simulation](http://mbostock.github.com/protovis/ex/nbody.html), positive values can be used. All nodes are assumed to be infinitesimal points with equal charge and mass.

<a name="theta" href="Force-Layout#theta">#</a> force.<b>theta</b>([<i>theta</i>])

If *theta* is specified, sets the Barnes–Hut approximation criterion to the specified value. If *theta* is not specified, returns the current value, which defaults to 0.8.  Unlike links, which only affect two linked nodes, the charge force is global: every node affects every other node, even if they are on disconnected subgraphs.

To avoid quadratic performance slowdown for large graphs, the force layout uses the [Barnes–Hut approximation](http://en.wikipedia.org/wiki/Barnes-Hut_simulation) which takes O(*n* log *n*) per tick. For each tick, a quadtree is created to store the current node positions; then for each node, the sum charge force of all other nodes on the given node are computed. For clusters of nodes that are far away, the charge force is approximated by treating the distance cluster of nodes as a single, larger node. *Theta* determines the accuracy of the computation: if the ratio of the area of a quadrant in the quadtree to the distance between a node to the quadrant's center of mass is less than *theta*, all nodes in the given quadrant are treated as a single, larger node rather than computed individually.

<a name="gravity" href="Force-Layout#gravity">#</a> force.<b>gravity</b>([<i>gravity</i>])

If *gravity* is specified, sets the gravitational strength to the specified value. If *gravity* is not specified, returns the current gravitational strength, which defaults to 0.1. The name of this parameter is perhaps misleading; it does not corresponding to physical [gravity](http://en.wikipedia.org/wiki/Gravitation) (which can be simulated using a positive [charge](#charge) parameter). Instead, gravity is implemented as a weak geometric constraint similar to a virtual spring connecting each node to the center of the layout's [size](#size). This approach has nice properties: near the center of the layout, the gravitational strength is almost zero, avoiding any local distortion of the layout; as nodes get pushed farther away from the center, the gravitational strength becomes strong in linear proportion to the distance. Thus, gravity will always overcome repulsive charge forces as some threshold, prevent disconnected nodes from escaping the layout.

Gravity can be disabled by setting the gravitational strength to zero. If you disable gravity, it is recommended that you implement some other geometric constraint to prevent nodes from escaping the layout, such as constraining them within the layout's bounds.

<a name="nodes" href="Force-Layout#nodes">#</a> force.<b>nodes</b>([<i>nodes</i>])

If *nodes* is specified, sets the layout's associated nodes to the specified array. If *nodes* is not specified, returns the current array, which defaults to the empty array. Each node has the following attributes:

* index - the zero-based index of the node within the *nodes* array.
* x - the *x*-coordinate of the current node position.
* y - the *y*-coordinate of the current node position.
* px - the *x*-coordinate of the previous node position.
* py - the *y*-coordinate of the previous node position.
* fixed - a boolean indicating whether node position is locked.

These attributes do not need to be set before passing the nodes to the layout; if they are not set, suitable defaults will be initialized by the layout when [start](#start) is called. However, be aware that if you are storing other data on your nodes, your data attributes should not conflict with the above properties used by the layout.

<a name="links" href="Force-Layout#links">#</a> force.<b>links</b>([<i>links</i>])

If *links* is specified, sets the layout's associated links to the specified array. If *links* is not specified, returns the current array, which defaults to the empty array. Each link has the following attributes:

* source - the source node (an element in *nodes*).
* target - the target node (an element in *nodes*).

You can also customize the link [strength](#linkStrength) and [distance](#linkDistance) on a per-link basis using an accessor function.

<a name="start" href="Force-Layout#start">#</a> force.<b>start</b>()

Starts the simulation; this method must be called when the layout is first created, after assigning the nodes and links. In addition, it should be called again whenever the nodes or links change. Internally, the layout uses a cooling parameter *alpha* which controls the layout temperature: as the physical simulation converges on a stable layout, the temperature drops, causing nodes to move more slowly. Eventually, *alpha* drops below a threshold and the simulation stops completely, freeing the CPU and avoiding battery drain. The layout can be reheated using [resume](#resume) or by restarting; this happens automatically when using the [drag](#drag) behavior.

On start, the layout initializes various attributes on the associated nodes. The *index* of each node is computed by iterating over the array, starting at zero. The initial *x* and *y* coordinates, if not already set externally to a valid number, are computed by examining neighboring nodes: if a linked node already has an initial position in *x* or *y*, the corresponding coordinates are applied to the new node. This increases the stability of the graph layout when new nodes are added, rather than using the default which is to initialize the position randomly within the layout's [size](#size). The previous *px* and *py* position is set to the initial position, if not already set, giving new nodes an initial velocity of zero. Finally, the *fixed* boolean defaults to false.

The layout also initializes the *source* and *target* attributes on the associated links: for convenience, these attributes may be specified as a numeric index rather than a direct link, such that the nodes and links can be read-in from a JSON file or other static description that may not allow circular linking. The *source* and *target* attributes on incoming links are only replaced with the corresponding entries in *nodes* if these attributes are numbers; thus, these attributes on existing links are unaffected when the layout is restarted. The link [distances](#linkDistance) and [strengths](#linkStrength) are also computed on start.

<a name="resume" href="Force-Layout#resume">#</a> force.<b>resume</b>()

Reheat the cooling parameter (*alpha*) and restart simulation. This method sets the internal *alpha* parameter to 0.1, and then restarts the [timer](Transitions#d3_timer). Typically, you don't need to call this method directly; it is called automatically by [start](#start). It is also called automatically by [drag](#drag) on mouseover.

<a name="stop" href="Force-Layout#stop">#</a> force.<b>stop</b>()

Immediately terminates the simulation, setting *alpha* to zero. This can be used to stop the simulation explicitly, for example, if you want to show animation or allow other interaction. If you do not stop the layout explicitly, it will still stop automatically after the layout's cooling parameter decays below some threshold.

<a name="on" href="Force-Layout#on">#</a> force.<b>on</b>(<i>type</i>, <i>listener</i>)

Registers the specified *listener* to receive events of the specified *type* from the force layout. Currently, only "tick" events are supported, which are dispatched for each tick of the simulation. Listen to tick events to update the displayed positions of nodes and links. For example, if you initially display the nodes and links like so:

```javascript
var link = vis.selectAll("line")
    .data(links)
  .enter().append("svg:line")
    .attr("x1", function(d) { return d.source.x; })
    .attr("y1", function(d) { return d.source.y; })
    .attr("x2", function(d) { return d.target.x; })
    .attr("y2", function(d) { return d.target.y; });

var node = vis.selectAll("circle")
    .data(nodes)
  .enter().append("svg:circle")
    .attr("cx", function(d) { return d.x; })
    .attr("cy", function(d) { return d.y; })
    .attr("r", 5);
```

You can update their positions on tick:

```javascript
force.on("tick", function() {
  link.attr("x1", function(d) { return d.source.x; })
      .attr("y1", function(d) { return d.source.y; })
      .attr("x2", function(d) { return d.target.x; })
      .attr("y2", function(d) { return d.target.y; });

  node.attr("cx", function(d) { return d.x; })
      .attr("cy", function(d) { return d.y; });
});
```

In this case, we've stored the selections `node` and `link` on initialization, so that we don't need to reselect the nodes on every tick. If you prefer, you can display nodes and links differently; for example, you might use [symbols](SVG-Shapes#symbol) rather than circles.

<a name="drag" href="Force-Layout#drag">#</a> force.<b>drag</b>()

Bind a behavior to nodes to allow interactive dragging. Use this in conjunction with the [call](Selections#call) operator on the nodes; for example, say `node.call(force.drag)` on initialization. The drag event sets the *fixed* attribute of nodes on mouseover, such that as soon as the mouse is over a node, it stops moving. Fixing on mouseover, rather than on mousedown, makes it easier to catch moving nodes. When a mousedown event is received, and on each subsequent mousemove until mouseup, the node center is set to the current mouse position. In addition, each mousemove triggers a [resume](#resume) of the force layout, reheating the simulation. This behavior also supports touch events for iOS.

Implementation note: the mousemove and mouseup event listeners are registered on the current window, such that when the user starts dragging a node, they can continue to drag the node even if the mouse leaves the window. Each event listener uses the "force" namespace, so as to avoid collision with other event listeners you may wish to bind to nodes or to the window. If a node is moved by the drag behavior, the subsequent click event that would be triggered by the final mouseup is captured and stopped from propagating. This allows you to register click event handlers on nodes that will only be triggered if nodes are clicked *without* dragging.
