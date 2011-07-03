> [[API Reference]] ▸ [[Layouts]]

A flexible force-directed graph layout implementation using position [Verlet integration](http://en.wikipedia.org/wiki/Verlet_integration) to allow [simple constraints](http://www.csse.monash.edu.au/~tdwyer/Dwyer2009FastConstraints.pdf). For more on physical simulations, see [Thomas Jakobsen](http://www.gamasutra.com/resource_guide/20030121/jacobson_pfv.htm). This implementation uses a [quadtree](Quadtree-Geom) to accelerate charge interaction using the [Barnes–Hut approximation](http://en.wikipedia.org/wiki/Barnes%E2%80%93Hut_simulation). In addition to the repulsive [charge](#charge) force, a psuedo-[gravity](#gravity) force keeps nodes centered in the visible area. Links are fixed-[distance](#distance) geometric constraints. Additional custom forces and constraints may be applied on the "tick" event, simply by updating the *x* and *y* attributes of nodes. For example, this can be used to implement [multiple](http://bl.ocks.org/1021953) [foci](http://bl.ocks.org/1021841). Thanks to gravity, the layout algorithm is also extremely robust in dealing with [disconnected graphs](http://bl.ocks.org/929623). Force-directed layout can also be applied to [trees](http://bl.ocks.org/1062288).

![force](force.png)

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

Get or set the link distance.

<a name="friction" href="#friction">#</a> force.<b>friction</b>([<i>friction</i>])

Get or set the friction coefficient in [0,1].

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