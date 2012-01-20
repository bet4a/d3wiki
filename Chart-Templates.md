Recommendations for reusable chart templates for D3. There is an implementation in progress [here](https://gist.github.com/1363743).

## Recommendations

* Use D3's zero- or single-argument getter/setter methods. For example, parent(selector) sets the chart's parent element, and parent() returns the chart's parent element. If the parent is specified as a selector string, it is implicitly converted to an element by selecting from the document at the time the parent is set.

* Getter/setter methods should be bound to the chart instance and use private (local) variables to hide internal state, rather than assigning to the prototype. This is consistent with the rest of D3, affords more flexibility in implementation, and the performance impact is negligible.

* The parent can be specified either as a selector string or as a raw element. (However, it should not be specified as a selection.)

* I like the idea of inferring the chart dimensions from the parent element. You might need to use getClientBoundingRect or getBBox (for SVG parents… read on), though. Also, we'd probably need to document that if the parent changes size, the chart will not automatically readjust. Sometimes, it's useful to resize automatically when the window dispatches a "resize" event.

* In addition to width and height, charts will probably need a configurable margin. This will allow the user to specify how much space to reserve for labels and axes, etc. The width and height that the user specifies becomes the outer width and height; positive margins subtract from these dimensions, given a smaller usable *inner* width and height internally.

* Charts will probably need configurable orientations. A bar chart might have four possible orientations.

* Setting any attribute of the chart should cause it to redraw immediately. The user should not be required to call draw after changing any aspect of the chart, nor to distinguish between an initial draw and a subsequent redraw; drawing should happen automatically. In the event that multiple attributes of the chart are changed simultaneously, this may cause multiple redraws, but the performance implications are negligible. (Transitions can automatically coalesce multiple redraws by waiting for the first timer tick to start work.)

* With automatic redraw, a way to specify a transition is needed. Perhaps calling transition([duration]) on the chart would indicate that any subsequent changes will take place over an optional duration rather than happening immediately.

* For object constancy, the user needs to be able to specify a key function along with the data. This way, when the data changes, the chart can correctly transition entering, updating and exiting elements. This can default to null which means to join by index.

* Likewise, a value function is also needed for the (e.g.) bar chart to extract the quantitative value of each data element. Different charts may have different accessor functions. A scatterplot, for example, might have an x and y accessor function.

* The user should have some way of specifying the type of quantitative scale for quantitative data. For example, the user might want to use a sqrt scale for a bar chart, or a log scale for a scatterplot. The chart should be able to determine the domain and range automatically (deriving the domain from the data and value accessor, and the range from the chart dimensions), but the user might still want to apply a transform to the position. One way of doing this might be to pass a scale instance to the chart, and then the chart sets the domain and range automatically. Note that this is combined with the value accessor, as scale(value(data)).

* Likewise, a label function is needed for the (e.g.) bar chart to extract the text label for each data element.

* Likewise, a color function is needed to determine the data value that should be encoded as color. The default might be null, which means all bars have the same color. Otherwise, it might return a string identifier that could be passed to a categorical scale. In addition, the user should also be able to specify the scale implementation, say as a standard d3.scale.ordinal, instead of an array of strings; this would also let the user specify a quantitative color scale, if desired. Color can be quantitative (steelblue-brown), ordinal (white, grey, black) or categorical (category10), so the user needs a way of controlling the encoding, and automatic type inference isn't precise enough.

* How would a bar chart support either grouped or stacked bars? Would this be a separate template, a different data representation, or perhaps a key function for nesting data elements into groups or stacks?

* Meta comment: as much as possible (i.e., without sacrificing ease-of-use), charts should be consistent with the rest of D3 and teach people the underlying API.

* We might want to allow the parent selector to be an SVG element (such as svg:g), so that it's possible to have multiple charts within the same SVG element, and to apply clipping or masking to the chart. To do this, the bar chart will need to detect the type of parent element, and then determine whether to create a containing svg:svg or svg:g.

* Charts should be configurable through CSS as much as possible. Default color schemes and such could be specified as a bundled stylesheet rather than in-code.

* Charts should use the d3.svg.axis component for quantitative axes.