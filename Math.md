> [Wiki](Home) ▸ [[API Reference]] ▸ [[Core]] ▸ **Math**

## Psuedorandom Number Generation

<a name="d3_random_normal" href="#wiki-d3_random_normal">#</a> d3.random.<b>normal</b>([<i>mean</i>, [<i>deviation</i>]])

Returns a function for generating random numbers with a normal (Gaussian) distribution. The expected value of the generated psuedorandom numbers is *mean*, with the given standard *deviation*. If *deviation* is not specified, it defaults to 1.0; if *mean* is not specified, it defaults to 0.0.

## 2D Transforms

<a name="d3_transform" href="#wiki-d3_transform">#</a> d3.<b>transform</b>(<i>string</i>)

Parses the given 2D affine transform string, as defined by SVG's [transform attribute](http://www.w3.org/TR/SVG/coords.html#TransformAttribute). The transform is then decomposed to a standard representation of translate, rotate, x-skew and scale. This behavior is standarded by CSS: see [matrix decomposition for animation](http://www.w3.org/TR/css3-2d-transforms/#matrix-decomposition).

<a name="transform_rotate" href="#wiki-transform_rotate">#</a> transform.<b>rotate</b>

Returns the rotation angle θ of this transform, in degrees.

<a name="transform_translate" href="#wiki-transform_translate">#</a> transform.<b>translate</b>

Returns the [dx, dy] translation of this transform, as a two-element array in local coordinates (typically pixels).

<a name="transform_skew" href="#wiki-transform_skew">#</a> transform.<b>skew</b>

Returns the *x*-skew φ of this transform, in degrees.

<a name="transform_scale" href="#wiki-transform_scale">#</a> transform.<b>scale</b>

Returns the [kx, ky] scale of this transform, as a two-element array.

<a name="transform_toString" href="#wiki-transform_toString">#</a> transform.<b>toString</b>

Returns a string representation of this transform, in the form "translate(dx,dy)rotate(θ)skewX(φ)scale(kx,ky)".