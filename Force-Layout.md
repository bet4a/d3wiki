> [[API Reference]] ▸ [[Layouts]]

A flexible force-directed graph layout implementation using position [Verlet integration](http://en.wikipedia.org/wiki/Verlet_integration) to allow [simple constraints](http://www.csse.monash.edu.au/~tdwyer/Dwyer2009FastConstraints.pdf). For more on physical simulations, see [Thomas Jakobsen](http://www.gamasutra.com/resource_guide/20030121/jacobson_pfv.htm). This implementation uses a [quadtree](Quadtree-Geom) to accelerate charge interaction using the [Barnes–Hut approximation](http://en.wikipedia.org/wiki/Barnes%E2%80%93Hut_simulation). In addition to the repulsive [charge](#charge) force, a psuedo-[gravity](#gravity) force keeps nodes centered in the visible area and avoids expulsion of disconnected subgraphs, while links are fixed-[distance](#distance) geometric constraints. Additional custom forces and constraints may be applied on the "tick" event, simply by updating the *x* and *y* attributes of nodes.

![force](force.png)

Some fun examples:

* [divergent forces](http://bl.ocks.org/1021841)
* [multiple foci](http://bl.ocks.org/1021953)
* [graph constructor](http://bl.ocks.org/929623)
* [force-directed tree](http://bl.ocks.org/1062288)
* [force-directed symbols](http://bl.ocks.org/1062383)
* [force-directed images and labels](http://bl.ocks.org/950642)

Like other classes in D3, layouts follow the method chaining pattern where setter methods return the layout itself, allowing multiple setters to be invoked in a concise statement. Unlike some of the other layout implementations which are stateless, the force layout keeps a reference to the associated nodes and links internally; thus, a given force layout instance can only be used with a single dataset.

<a name="force" href="#force">#</a> d3.layout.<b>force</b>()

Constructs a new force-directed layout with the default settings: size 1×1, friction 0.9, distance 20, charge strength -30, gravity strength 0.1, and theta parameter 0.8. The default nodes and links are the empty array, and when the layout is started, the internal alpha cooling parameter is set to 0.1. The general pattern for constructing force-directed layouts is to set all the configuration properties, and then call [start](#start):

```javascript
var force = d3.layout.force()
    .nodes(nodes)
    .links(links)
    .size([w, h])
    .start();
```

Note that, like D3's other layouts, the force-directed layout doesn't mandate a particular visual representation. Most commonly, nodes are mapped to SVG circle elements, and links are mapped to SVG line elements. But you might also display nodes as [symbols](http://bl.ocks.org/1062383) or [images](http://bl.ocks.org/950642).

<a name="size" href="#size">#</a> force.<b>size</b>([<i>size</i>])

If *size* is specified, sets the available layout size to the specified two-element array of numbers representing *x* and *y*. If *size* is not specified, returns the current size, which defaults to 1×1. The size affects two aspects of the force-directed layout: the gravitational center, and the initial random position. The center of gravity is simply [*x* / 2, *y* / 2]. When nodes are added to the force layout, if they do not have *x* and *y* attributes already set, then these attributes are initialized using a uniform random distribution in the range [0, *x*] and [0, *y*], respectively.

<a name="distance" href="#distance">#</a> force.<b>distance</b>([<i>distance</i>])

If *distance* is specified, sets the target distance between linked nodes to the specified value. If *distance* is not specified, returns the layout's current target distance, which defaults to 20. Typically, the distance is specified in pixels; however, the units are arbitrary relative to the layout's [size](#size). Links are not implemented as "spring forces", as in common in other force-directed layouts, but as weak geometric constraints. For each tick of the layout, the distance between each pair of linked nodes is computed and compared to the target distance; the links are then moved towards each other, or away from each other, so as to converge on the desired distance. This method of constraints relaxation on top of position Verlet integration is vastly more stable than previous methods using spring forces, and also allows for the flexible implementation of [other constraints](http://www.csse.monash.edu.au/~tdwyer/Dwyer2009FastConstraints.pdf) in the tick event listener, such as hierarchical layering.

The current implementation does not allow variable link distances or strengths; this is being tracked as issue [#211](https://github.com/mbostock/d3/issues/211) and will be added in a future release. The goal will be to allow the link distance and strength to be computed as a function on the link objects, allowing total flexibility in the link specification.

<a name="friction" href="#friction">#</a> force.<b>friction</b>([<i>friction</i>])

If *friction* is specified, sets the friction coefficient to the specified value. If *friction* is not specified, returns the current coefficient, which defaults to 0.9. The name of this parameter is perhaps misleading; it does not correspond to a standard physical [coefficient of friction](http://en.wikipedia.org/wiki/Friction#Coefficient_of_friction). Instead, it more closely approximates velocity decay: at each tick of the simulation, the particle velocity is scaled by the specified *friction*. Thus, a value of 1 corresponds to a frictionless environment, while a value of 0 freezes all particles in place. Values outside the range [0,1] are not recommended and may have destabilizing effects.

<a name="charge" href="#charge">#</a> force.<b>charge</b>([<i>charge</i>])

If *charge* is specified, sets the charge strength to the specified value. If *charge* is not specified, returns the current charge strength, which defaults to -30. A negative value results in node repulsion, while a positive value results in node attraction. For graph layout, negative values should be used; for [*n*-body simulation](http://mbostock.github.com/protovis/ex/nbody.html), positive values can be used. All nodes are assumed to be infinitesimal points with equal charge and mass.

<a name="theta" href="#theta">#</a> force.<b>theta</b>([<i>theta</i>])

If *theta* is specified, sets the Barnes–Hut approximation criterion to the specified value. If *theta* is not specified, returns the current value, which defaults to 0.8.  Unlike links, which only affect two linked nodes, the charge force is global: every node affects every other node, even if they are on disconnected subgraphs.

To avoid quadratic performance slowdown for large graphs, the force layout uses the [Barnes–Hut approximation](http://en.wikipedia.org/wiki/Barnes-Hut_simulation) which takes O(*n* log *n*) per tick. For each tick, a quadtree is created to store the current node positions; then for each node, the sum charge force of all other nodes on the given node are computed. For clusters of nodes that are far away, the charge force is approximated by treating the distance cluster of nodes as a single, larger node. *Theta* determines the accuracy of the computation: if the ratio of the area of a quadrant in the quadtree to the distance between a node to the quadrants's center of mass is less than *theta*, all nodes in the given quadrant are treated as a single, larger node rather than computed individually.

<a name="gravity" href="#gravity">#</a> force.<b>gravity</b>([<i>gravity</i>])

If *gravity* is specified, sets the gravitational strength to the specified value. If *gravity* is not specified, returns the current gravitational strength, which defaults to 0.1. The name of this parameter is perhaps misleading; it does not corresponding to physical [gravity](http://en.wikipedia.org/wiki/Gravitation) (which can be simulated using a positive [charge](#charge) parameter). Instead, gravity is implemented as a weak geometric constraint similar to a virtual spring connecting each node to the center of the layout's [size](#size). This approach has nice properties: near the center of the layout, the gravitational strength is almost zero, avoiding any local distortion of the layout; as nodes get pushed farther away from the center, the gravitational strength becomes strong in linear proportion to the distance. Thus, gravity will always overcome repulsive charge forces as some threshold, prevent disconnected nodes from escaping the layout.

Gravity can be disabled by setting the gravitational strength to zero. If you disable gravity, it is recommended that you implement some other geometric constraint to prevent nodes from escaping the layout, such as constraining them within the layout's bounds.

<a name="nodes" href="#nodes">#</a> force.<b>nodes</b>([<i>nodes</i>])

If *nodes* is specified, sets the layout's associated nodes to the specified array. If *nodes* is not specified, returns the current array, which defaults to the empty array. Each node has the following attributes:

* index - the zero-based index of the node within the *nodes* array.
* x - the *x*-coordinate of the current node position.
* y - the *y*-coordinate of the current node position.
* px - the *x*-coordinate of the previous node position.
* py - the *y*-coordinate of the previous node position.
* fixed - a boolean indicating whether node position is locked.

These attributes do not need to be set before passing the nodes to the layout; if they are not set, suitable defaults will be initialized by the layout when [start](#start) is called. However, be aware that if you are storing other data on your nodes, your data attributes should not conflict with the above properties used by the layout.

<a name="links" href="#links">#</a> force.<b>links</b>([<i>links</i>])



Get or set the array of links between nodes.

<a name="start" href="#start">#</a> force.<b>start</b>()

Starts the simulation; this method must be called when the layout is first created, after assigning the nodes and links. In addition, it should be called again whenever the nodes or links change. Internally, the layout uses a cooling parameter *alpha* which controls the layout temperature: as the physical simulation converges on a stable layout, the temperature drops, causing nodes to move more slowly. Eventually, *alpha* drops below a threshold and the simulation stops completely, freeing the CPU and avoiding battery drain. The layout can be reheated using [resume](#resume) or by restarting; this happens automatically when using the [drag](#drag) behavior.

On start, the layout initializes various attributes on the associated nodes. The *index* of each node is computed by iterating over the array, starting at zero. The initial *x* and *y* coordinates, if not already set externally to a valid number, are computed by examining neighboring nodes: if a linked node already has an initial position in *x* or *y*, the corresponding coordinates are applied to the new node. This increases the stability of the graph layout when new nodes are added, rather than using the default which is to initialize the position randomly within the layout's [size](#size). The previous *px* and *py* position is set to the initial position, if not already set, giving new nodes an initial velocity of zero. Finally, the *fixed* boolean defaults to false.

<a name="resume" href="#resume">#</a> force.<b>resume</b>()

Reheat the cooling parameter (*alpha*) and restart simulation.

<a name="stop" href="#stop">#</a> force.<b>stop</b>()

Immediately terminate the simulation.

<a name="on" href="#on">#</a> force.<b>on</b>(<i>type</i>, <i>listener</i>)

Listen to "tick" updates in the computed layout positions. Use this to update the displayed nodes and links.

<a name="drag" href="#drag">#</a> force.<b>drag</b>()

Bind a behavior to nodes to allow interactive dragging. Use in conjunction with the [call](Selections#call) operator on the nodes.