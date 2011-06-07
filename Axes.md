Each example shows axes in four orientations. In clockwise order: top, right, bottom, left.

* grid - major, minor, none
* domain - open, closed (true/false?)
* tick - tick, none (true/false?)
* labels - point, section

## Open Domain

An **open domain** means that only ticks or grid lines are drawn:

![axes-open-labels](axes-open-labels.png)
![axes-open](axes-open.png)
![axes-open-major-labels](axes-open-major-labels.png)

It is also possible to draw both ticks and grid lines. If the ticks are not drawn, then the labels are positioned closer to the grid lines.

## Closed Domain

A **closed domain** means that we can visualize the domain extent. This can be done in by drawing a path:

![axes-closed-labels](axes-closed-labels.png)
![axes-closed](axes-closed.png)

Or by filling the background. In this case we include major and minor grid lines which subdivide the ticks:

![axes-open-minor-labels](axes-open-minor-labels.png)

Note that the grid lines can also be drawn with an open domain, as above. And the background need not be filled—we could instead stroke the background to create a frame.

## Sectional

Sometimes we want to label sections rather than points on the axes:

![axes-open-region-labels](axes-open-region-labels.png)
![axes-closed-region-labels](axes-closed-region-labels.png)
