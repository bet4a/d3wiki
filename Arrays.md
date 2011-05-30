> [[API Reference|API-Reference]]

When using D3—and doing data visualization in general—you tend to do a lot of **array manipulation**. That's because D3's canonical representation of data is an array. Some common forms of array manipulation include taking a contiguous slice (subset) of an array, filtering an array using a predicate function, and mapping an array to a parallel set of values using a transform function. Before looking at the set of utilities that D3 provides for arrays, you should familiarize yourself with the powerful array methods built-in to JavaScript.

This includes **mutator methods** that modify the array:

* [array.reverse](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/reverse) - Reverse the order of the elements of the array.
* [array.shift](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/shift) - Remove the first element from the array.
* [array.sort](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/sort) - Sort the elements of the array.
* [array.splice](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/splice) - Add or remove elements from the array.
* [array.unshift](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/unshift) - Add one or more elements to the front of the array.

There are also **accessor methods** that return some representation of the array:

* [array.concat](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/concat) - Join the array with other array(s) or value(s).
* [array.join](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/join) - Join all elements of the array into a string.
* [array.slice](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/slice) - Extract a section of the array.
* [array.indexOf](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/indexOf) - Find the first occurrence of a value within the array.
* [array.lastIndexOf](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/lastIndexOf) - Find the last occurrence of a value within the array.

And finally, **iteration methods** that apply functions to elements in the array:

* [array.filter](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/filter) - Create a new array with only the elements for which a predicate is true.
* [array.forEach](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/forEach) - Call a function for each element in the array.
* [array.every](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/every) - See if every element in the array satisfies a predicate.
* [array.map](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/map) - Create a new array with the result of a function of every element in the array.
* [array.some](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/some) - See if at least one element in the array satisfies a predicate.
* [array.reduce](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/reduce) - Apply a function to reduce the array to a single value (from left-to-right).
* [array.reduceRight](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/reduceRight) - Apply a function to reduce the array to a single value (from right-to-left).

## Ordering

<a name="d3_ascending" href="#d3_ascending">#</a> d3.<b>ascending</b>(<i>a</i>, <i>b</i>)

Returns -1 if *a* is less than *b*, or 1 if *a* is greater than *b*, or 0. This is the comparator function for natural order, and can be used in conjunction with the built-in array sort method to arrange elements in ascending order:

    function(a, b) {
      return a < b ? -1 : a > b ? 1 : 0;
    }

Note that if no comparator function is specified to the built-in sort method, the default order is lexicographic (alphabetical), not natural! This can lead to bugs when sorting an array of numbers.

<a name="d3_descending" href="#d3_descending">#</a> d3.<b>descending</b>(<i>a</i>, <i>b</i>)

Returns -1 if *a* is greater than *b*, or 1 if *a* is less than *b*, or 0. This is the comparator function for reverse natural order, and can be used in conjunction with the built-in array sort method to arrange elements in descending order:

    function(a, b) {
      return b < a ? -1 : b > a ? 1 : 0;
    }

Note that if no comparator function is specified to the built-in sort method, the default order is lexicographic (alphabetical), not natural! This can lead to bugs when sorting an array of numbers.

<a name="d3_min" href="#d3_min">#</a> d3.<b>min</b>(<i>array</i>[, <i>function</i>])

Returns the minimum value in the given *array*. If the array is empty, returns undefined. An optional accessor *function* may be specified, which is equivalent to calling *array.map(function)* before computing the minimum value. Unlike the built-in [Math.min](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Math/min), this method ignores any values that cannot be coerced to a number, such as NaN or undefined. Thus, when computing the domain of a [[scale|Scales]] from data, only the defined region of the data is considered, rather than applying a degenerate domain.

<a name="d3_max" href="#d3_max">#</a> d3.<b>max</b>(<i>array</i>[, <i>function</i>])

Returns the maximum value in the given *array*. If the array is empty, returns undefined. An optional accessor *function* may be specified, which is equivalent to calling *array.map(function)* before computing the maximum value. Unlike the built-in [Math.max](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Math/max), this method ignores any values that cannot be coerced to a number, such as NaN or undefined. Thus, when computing the domain of a [[scale|Scales]] from data, only the defined region of the data is considered, rather than applying a degenerate domain.

## Associative Arrays

<a name="d3_keys" href="#d3_keys">#</a> d3.<b>keys</b>(<i>object</i>)

Returns an array containing the property names of the specified object (an associative array). The order of the returned array is not defined, though it will be consistent with your browser's iteration order when using a [for…in loop](https://developer.mozilla.org/en/JavaScript/Reference/Statements/for...in).

<a name="d3_values" href="#d3_values">#</a> d3.<b>values</b>(<i>object</i>)

Returns an array containing the property values of the specified object (an associative array). The order of the returned array is not defined, though it will be consistent with your browser's iteration order when using a [for…in loop](https://developer.mozilla.org/en/JavaScript/Reference/Statements/for...in).

<a name="d3_entries" href="#d3_entries">#</a> d3.<b>entries</b>(<i>object</i>)

Returns an array containing the property keys and values of the specified object (an associative array). Each entry is an object with a key and value attribute, such as {key: "foo", value: 42}. The order of the returned array is not defined, though it will be consistent with your browser's iteration order when using a [for…in loop](https://developer.mozilla.org/en/JavaScript/Reference/Statements/for...in).

## Array Operators

<a name="d3_split" href="#d3_split">#</a> d3.<b>split</b>(<i>array</i>[, <i>function</i>])

<a name="d3_merge" href="#d3_merge">#</a> d3.<b>merge</b>(<i>arrays</i>)

<a name="d3_range" href="#d3_range">#</a> d3.<b>range</b>([<i>start</i>, ]<i>stop</i>[, <i>step</i>])

### Nest

<a name="d3_nest" href="#d3_nest">#</a> d3.<b>nest</b>()

<a name="nest_key" href="#nest_key">#</a> nest.<b>key</b>(<i>function</i>)

<a name="nest_sortKeys" href="#nest_sortKeys">#</a> nest.<b>sortKeys</b>(<i>comparator</i>)

<a name="nest_sortValues" href="#nest_sortValues">#</a> nest.<b>sortValues</b>(<i>comparator</i>)

<a name="nest_rollup" href="#nest_rollup">#</a> nest.<b>rollup</b>(<i>function</i>)

<a name="nest_map" href="#nest_map">#</a> nest.<b>map</b>(<i>array</i>)

<a name="nest_entries" href="#nest_entries">#</a> nest.<b>entries</b>(<i>array</i>)
