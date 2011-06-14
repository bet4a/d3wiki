> [[API Reference]] ▸ [[Layouts]]

[Chord diagrams](http://mbostock.github.com/d3/ex/chord.html) show relationships among a group of entities. For example, consider a hypothetical population of people with different hair colors: black, blonde, brown and red. Each person in this population may have a preferred hair color for a dating partner; for example, of the 29,630 (hypothetical) people with black hair, 40% (11,975) prefer partners with the same hair color. This preference is asymmetric: for example, only 10% of people with blonde hair prefer black hair, while 20% of people which black hair prefer blonde hair.

![chord](chord.png)

A chord diagram visualizes these relationships by drawing quadratic Bézier curves between arcs. The source and target arcs represents two mirrored subsets of the total population, such as the number of people with black hair that prefer blonde hair, and the number of people with blonde hair that prefer black hair.

The chord layout is designed to work in conjunction with the [chord shape](SVG-Shapes#chord) and the [arc shape](SVG-Shapes#arc). The layout is used to generate data objects which describe the chords, serving as input to the chord shape. The layout also generates descriptions for the groups, which can be used as input to the arc shape.

<a name="chord" href="#chord">#</a> d3.layout.<b>chord</b>()

<a name="matrix" href="#matrix">#</a> chord.<b>matrix</b>([<i>matrix</i>])

<a name="padding" href="#padding">#</a> chord.<b>padding</b>([<i>padding</i>])

<a name="sortGroups" href="#sortGroups">#</a> chord.<b>sortGroups</b>([<i>comparator</i>])

<a name="sortSubgroups" href="#sortSubgroups">#</a> chord.<b>sortSubgroups</b>([<i>comparator</i>])

<a name="sortChords" href="#sortChords">#</a> chord.<b>sortChords</b>([<i>comparator</i>])

<a name="chords" href="#chords">#</a> chord.<b>chords</b>()

<a name="groups" href="#groups">#</a> chord.<b>groups</b>()
