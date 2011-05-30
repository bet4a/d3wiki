> [[API Reference|API-Reference]]

Constructing visualizations often involves working with colors. Even though your browser understands a lot about colors, it doesn't offer much help in manipulating colors through JavaScript. So D3 provides representations for both RGB and HSL colors, allowing interpolation in both color spaces, and making colors brighter or darker. For more about color manipulation, see the Wikipedia entries on [[RGB|http://en.wikipedia.org/wiki/RGB_color_model]] and [[HSL|http://en.wikipedia.org/wiki/HSL_and_HSV]].

Note: while you can work with colors directly, you might also want to take a look at D3's built-in [[interpolateRgb|Transitions#d3_interpolateRgb]], [[interpolateHsl|Transitions#d3_interpolateHsl]] and [[scales|Scales]]. There are also some fantastic categorical color scales built-in to D3 provided by [[ColorBrewer|http://colorbrewer2.org/]].

## RGB

<a name="d3_rgb" href="#d3_rgb">#</a> d3.<b>rgb</b>(<i>r</i>, <i>g</i>, <i>b</i>)

Constructs a new RGB color with the specified *r*, *g* and *b* channel values. Each channel must be specified as an integer in the range [0,255]. The channels are available as the `r`, `g` and `b` attributes of the returned object.

<a href="#d3_rgb">#</a> d3.<b>rgb</b>(<i>color</i>)

Constructs a new RGB color by parsing the specified *color* string. If *color* is not a string, it is coerced to a string; thus, this constructor can also be used to create a copy of an existing color, or force the conversion of a [d3.hsl](#d3_hsl) color to RGB. The color string may be in a variety of formats:

* rgb decimal - "rgb(255,255,255)"
* hsl decimal - "hsl(120,50%,20%)"
* rgb hexadecimal - "#ffeeaa"
* rgb shorthand hexadecimal - "#fea"
* named - "red", "white", "blue"

The resulting color is stored as red, green and blue integer channel values in the range [0,255]. The channels are available as the `r`, `g` and `b` attributes of the returned object. The list of supported [[named colors|http://www.w3.org/TR/SVG/types.html#ColorKeywords]] is specified by CSS. If the color is specified in HSL space, it is converted to RGB in a manner equivalent to [hsl.rgb](#hsl_rgb).

<a name="rgb_brighter" href="#rgb_brighter">#</a> rgb.<b>brighter</b>([<i>k</i>])

Returns a brighter copy of this color. Each channel is multiplied by 0.7 ^ *-k*. The the gamma value *k* is omitted, it defaults to 1. Channel values are capped at the maximum value of 255, and the minimum value of 30.

<a name="rgb_darker" href="#rgb_darker">#</a> rgb.<b>darker</b>([<i>k</i>])

Returns a darker copy of this color. Each channel is multiplied by 0.7 ^ *k*. The the gamma value *k* is omitted, it defaults to 1.

<a name="rgb_hsl" href="#rgb_hsl">#</a> rgb.<b>hsl</b>()

Returns the equivalent color in HSL space; see [d3.hsl](#d3_hsl) for details on the returned object. The conversion from HSL to RGB is described in [[CSS3 Color Module Level 3|http://www.w3.org/TR/css3-color/#hsl-color]]; this is the equivalent reverse operation.

<a name="rgb_toString" href="#rgb_toString">#</a> rgb.<b>toString</b>()

Converts this RGB color to a string, such as "#f7eaba".

## HSL

<a name="d3_hsl" href="#d3_hsl">#</a> d3.<b>hsl</b>(<i>h</i>, <i>s</i>, <i>l</i>)

Constructs a new HSL color with the specified hue *h*, saturation *s* and lightness *l*. The hue must be a number in the range [0,360]. The saturation and lightness must be in the range [0,1] (not percentages). These values are available as the `h`, `s` and `l` attributes of the returned object.

<a href="#d3_hsl">#</a> d3.<b>hsl</b>(<i>color</i>)

Constructs a new HSL color by parsing the specified *color* string. If *color* is not a string, it is coerced to a string; thus, this constructor can also be used to create a copy of an existing color, or force the conversion of a [d3.rgb](#d3_rgb) color to HSL. The color string may be in a variety of formats:

* rgb decimal - "rgb(255,255,255)"
* hsl decimal - "hsl(120,50%,20%)"
* rgb hexadecimal - "#ffeeaa"
* rgb shorthand hexadecimal - "#fea"
* named - "red", "white", "blue"

The resulting color is stored as hue in the range [0,360], and saturation and lightness values in the range [0,1]. These values are available as the `h`, `s` and `l` attributes of the returned object. The list of supported [[named colors|http://www.w3.org/TR/SVG/types.html#ColorKeywords]] is specified by CSS. If the color is specified in RGB space, it is converted to HSL in a manner equivalent to [rgb.hsl](#rgb_hsl).

<a name="hsl_brighter" href="#hsl_brighter">#</a> hsl.<b>brighter</b>([<i>k</i>])

Returns a brighter copy of this color. The lightness channel is multiplied by 0.7 ^ *-k*. The the gamma value *k* is omitted, it defaults to 1.

<a name="hsl_darker" href="#hsl_darker">#</a> hsl.<b>darker</b>([<i>k</i>])

Returns a darker copy of this color. The lightness channel is multiplied by 0.7 ^ *k*. The the gamma value *k* is omitted, it defaults to 1.

<a name="hsl_rgb" href="#hsl_rgb">#</a> hsl.<b>rgb</b>()

Returns the equivalent color in RGB space; see [d3.rgb](#d3_rgb) for details on the returned object. The conversion from HSL to RGB is described in [[CSS3 Color Module Level 3|http://www.w3.org/TR/css3-color/#hsl-color]].

<a name="hsl_toString" href="#hsl_toString">#</a> hsl.<b>toString</b>()

Converts this HSL color to a string, such as "hsl(120,40%,10%)".