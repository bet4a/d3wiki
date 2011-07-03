> [[API Reference]] ▸ [[Layouts]]

A flexible force-directed graph layout implementation using position [Verlet integration](http://en.wikipedia.org/wiki/Verlet_integration) to allow [simple constraints](http://www.csse.monash.edu.au/~tdwyer/Dwyer2009FastConstraints.pdf). For more on physical simulations, see [Thomas Jakobsen](http://www.gamasutra.com/resource_guide/20030121/jacobson_pfv.htm). This implementation uses a quadtree to accelerate charge interaction using the [Barnes–Hut approximation](http://en.wikipedia.org/wiki/Barnes%E2%80%93Hut_simulation). In addition to the repulsive [charge](#charge) force, a psuedo-[gravity](#gravity) force keeps nodes centered in the visible area. Links are fixed-[distance](#distance) geometric constraints.

![force](force.png)

<a name="force" href="#force">#</a> d3.layout.<b>force</b>()

<a name="size" href="#size">#</a> force.<b>size</b>([<i>size</i>])

<a name="distance" href="#distance">#</a> force.<b>distance</b>([<i>distance</i>])

<a name="friction" href="#friction">#</a> force.<b>friction</b>([<i>friction</i>])

<a name="charge" href="#charge">#</a> force.<b>charge</b>([<i>charge</i>])

<a name="gravity" href="#gravity">#</a> force.<b>gravity</b>([<i>gravity</i>])

<a name="theta" href="#theta">#</a> force.<b>theta</b>([<i>theta</i>])

<a name="nodes" href="#nodes">#</a> force.<b>nodes</b>([<i>nodes</i>])

<a name="links" href="#links">#</a> force.<b>links</b>([<i>links</i>])

<a name="start" href="#start">#</a> force.<b>start</b>()

<a name="resume" href="#resume">#</a> force.<b>resume</b>()

<a name="stop" href="#stop">#</a> force.<b>stop</b>()

<a name="on" href="#on">#</a> force.<b>on</b>(<i>type</i>, <i>listener</i>)

<a name="drag" href="#drag">#</a> force.<b>drag</b>()
