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

Get or set the charge strength. A negative number is recommended for repulsion.

<a name="gravity" href="#gravity">#</a> force.<b>gravity</b>([<i>gravity</i>])

Get or set the gravity strength.

<a name="theta" href="#theta">#</a> force.<b>theta</b>([<i>theta</i>])

Get or set the accuracy of the charge interaction (Barnes–Hut approximation).

<a name="nodes" href="#nodes">#</a> force.<b>nodes</b>([<i>nodes</i>])

Get or set the array of nodes to layout.

<a name="links" href="#links">#</a> force.<b>links</b>([<i>links</i>])

Get or set the array of links between nodes.

<a name="start" href="#start">#</a> force.<b>start</b>()

Start the simulation. Can also be used to restart the simulation when the nodes or links change. As the layout stabilizes, it cools, slowing down movement and eventually stopping. This way, it doesn't hog the CPU or drain the battery.

<a name="resume" href="#resume">#</a> force.<b>resume</b>()

Reheat the cooling parameter (*alpha*) and restart simulation.

<a name="stop" href="#stop">#</a> force.<b>stop</b>()

Immediately terminate the simulation.

<a name="on" href="#on">#</a> force.<b>on</b>(<i>type</i>, <i>listener</i>)

Listen to "tick" updates in the computed layout positions. Use this to update the displayed nodes and links.

<a name="drag" href="#drag">#</a> force.<b>drag</b>()

Bind a behavior to nodes to allow interactive dragging. Use in conjunction with the [call](Selections#call) operator on the nodes.