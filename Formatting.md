> [[API Reference|API-Reference]]

## Number Formatting

<a name="d3_format" href="#d3_format">#</a> d3.<b>format</b>(<i>specifier</i>)

Returns a new format function with the given string *specifier*. A format function takes a number as the only argument, and returns a string representing the formatted number. The format specifier is modeled after Python 3.1's built-in [[format specification mini-language|http://docs.python.org/release/3.1.3/library/string.html#formatspec]]. The general form of a specifier is [*sign*][0][*width*][,][.*precision*][*type*]. The *sign* can be one of the following:

* plus ("+") - a sign should be used for both positive and negative numbers.
* minus ("-") - a sign should be used only for negative numbers. (This is the default.)
* space (" ") - a leading space should be used on positive numbers, and a minus sign on negative numbers.

The *comma* (",") option enables the use of a comma for a thousands separator. The *width* defines the minimum field width. If not specified, then the width will be determined by the content. If *width* is preceded by a zero ("0"), zero-padding is enabled. The available *type* values are:

* exponent ("e") - use Number.toExponential.
* general ("g") - use Number.toPrecision.
* fixed ("f") - use Number.toFixed.
* integer ("d") - use Number.toString, but ignore any non-integer values.
* rounded ("r") - like fixed, but round to *precision* significant digits.
* percentage ("%") - like fixed, but multiply by 100 and suffix with "%".
* rounded percentage ("p") - like rounded, but multiply by 100 and suffix with "%".

The type "n" is also supported as shorthand for ",g". The *precision* indicates how many digits should be displayed after the decimal point for a value formatted with types "f" and "%", or before and after the decimal point for a value formatted with types "g", "r" and "p".

## Date Formatting

See the [[d3.time|Time-Formatting]] module.
