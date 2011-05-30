> [[API Reference|API-Reference]]

Constructing visualizations often involves working with colors. Even though your browser understands a lot about colors, it doesn't offer much help in manipulating colors through JavaScript. So D3 provides representations for both RGB and HSL colors, allowing interpolation in both color spaces, and making colors brighter or darker. For more about color manipulation, see the Wikipedia entries on [[RGB|http://en.wikipedia.org/wiki/RGB_color_model]] and [[HSL|http://en.wikipedia.org/wiki/HSL_and_HSV]].

Note: while you can work with colors directly, you might also want to take a look at D3's built-in [[interpolateRgb|Transitions#d3_interpolateRgb]], [[interpolateHsl|Transitions#d3_interpolateHsl]] and [[scales|Scales]].

## RGB

<a name="d3_rgb" href="#d3_rgb">#</a> d3.<b>rgb</b>(<i>r</i>, <i>g</i>, <i>b</i>)

<a href="#d3_rgb">#</a> d3.<b>rgb</b>(<i>color</i>)

<a name="rgb_brighter" href="#rgb_brighter">#</a> rgb.<b>brighter</b>([<i>k</i>])

<a name="rgb_darker" href="#rgb_darker">#</a> rgb.<b>darker</b>([<i>k</i>])

<a name="rgb_hsl" href="#rgb_hsl">#</a> rgb.<b>hsl</b>()

<a name="rgb_toString" href="#rgb_toString">#</a> rgb.<b>toString</b>()

## HSL

<a name="d3_hsl" href="#d3_hsl">#</a> d3.<b>hsl</b>(<i>h</i>, <i>s</i>, <i>l</i>)

<a href="#d3_hsl">#</a> d3.<b>hsl</b>(<i>color</i>)

<a name="hsl_brighter" href="#hsl_brighter">#</a> hsl.<b>brighter</b>([<i>k</i>])

<a name="hsl_darker" href="#hsl_darker">#</a> hsl.<b>darker</b>([<i>k</i>])

<a name="hsl_rgb" href="#hsl_rgb">#</a> hsl.<b>rgb</b>()

<a name="hsl_toString" href="#hsl_toString">#</a> hsl.<b>toString</b>()
