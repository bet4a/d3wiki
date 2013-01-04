> [Wiki](Home) ▸ [[API Reference]] ▸ [[Core]] ▸ **Formatting**

Formatting numbers is one of those things you don't normally think about until an ugly "0.30000000000000004" appears on your axis labels. Also, maybe you want to group thousands to improve readability, and use fixed precision, such as "$1,240.10". Or, maybe you want to display only the significant digits of a particular number. D3 makes this easy using a standard **number format**. For example, to create a function that zero-fills to four digits, say:

```javascript
var zero = d3.format("04d");
```

Now you can conveniently format numbers:

```javascript
zero(2); // "0002"
zero(123); // "0123"
```

In addition to numbers, D3 also supports formatting and parsing [[dates|Time-Formatting]], and [[comma-separated values|CSV]].

## Numbers

<a name="d3_format" href="#wiki-d3_format">#</a> d3.<b>format</b>(<i>specifier</i>)

Returns a new format function with the given string *specifier*. A format function takes a number as the only argument, and returns a string representing the formatted number. The format specifier is modeled after Python 3.1's built-in [[format specification mini-language|http://docs.python.org/release/3.1.3/library/string.html#formatspec]]. The general form of a specifier is [*sign*][0][*width*][,][.*precision*][*type*].

The *sign* can be one of the following:

* plus ("+") - a sign should be used for both positive and negative numbers.
* minus ("-") - a sign should be used only for negative numbers. (This is the default.)
* space (" ") - a leading space should be used on positive numbers, and a minus sign on negative numbers.

The *comma* (",") option enables the use of a comma for a thousands separator.

The *width* defines the minimum field width. If not specified, then the width will be determined by the content. If *width* is preceded by a zero ("0"), zero-padding is enabled.

The available *type* values are:

* exponent ("e") - use [[Number.toExponential|https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number/toExponential]].
* general ("g") - use [[Number.toPrecision|https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number/toPrecision]].
* fixed ("f") - use [[Number.toFixed|https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number/toFixed]].
* integer ("d") - use [[Number.toString|https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number/toString]], but ignore any non-integer values.
* rounded ("r") - like fixed, but round to *precision* significant digits.
* percentage ("%") - like fixed, but multiply by 100 and suffix with "%".
* rounded percentage ("p") - like rounded, but multiply by 100 and suffix with "%".
* SI-prefix ("s") - like rounded, but with a unit suffixed such as "9.5M" or "1.00µ".

The type "n" is also supported as shorthand for ",g". The *precision* indicates how many digits should be displayed after the decimal point for a value formatted with types "f" and "%", or before and after the decimal point for a value formatted with types "g", "r" and "p".

<a name="d3_formatPrefix" href="#wiki-d3_formatPrefix">#</a> d3.<b>formatPrefix</b>(<i>value</i>, <i>precision</i>)

Returns the [SI prefix](http://en.wikipedia.org/wiki/Metric_prefix) for the specified *value* at the specified *precision*. The returned prefix object has two properties:

* symbol - the prefix symbol, such as "M" for millions.
* scale - the scale function, for converting numbers to the appropriate prefixed scale.

For example:

```js
var prefix = d3.formatPrefix(1.21e9);
console.log(prefix.symbol); // "G"
console.log(prefix.scale(1.21e9)); // 1.21
```

This method is used by d3.format for the %s format.

<a name="d3_round" href="Formatting#wiki-d3_round">#</a> d3.<b>round</b>(<i>x</i>[, <i>n</i>])

Returns the value *x* rounded to *n* digits after the decimal point. If *n* is omitted, it defaults to zero. The result is a number. Values are rounded to the closest multiple of 10 to the power minus *n*; if two multiples are equally close, the value is rounded up in accordance with the built-in [[round|https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Math/round]] function. Note that the resulting number when converted to a string may be imprecise due to IEEE floating point precision; to format a number to a string with a fixed number of decimal points, use [d3.format](Formatting#wiki-d3_format) instead.

## Strings

<a name="d3_requote" href="Formatting#wiki-d3_requote">#</a> d3.<b>requote</b>(<i>string</i>)

Returns a quoted (escaped) version of the specified *string* such that the string may be embedded in a regular expression as a string literal.

## Dates

See the [[d3.time|Time-Formatting]] module.