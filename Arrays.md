> [[API Reference|API-Reference]]

When using D3—and doing data visualization in general—you tend to do a lot of **array manipulation**. That's because D3's canonical representation of data is an array. Some common forms of array manipulation include taking a contiguous slice (subset) of an array, filtering an array using a predicate function, and mapping an array to a parallel set of values using a transform function. Before looking at the set of utilities that D3 provides for arrays, you should familiarize yourself with the powerful array methods built-in to JavaScript.

This includes **mutator methods** that modify the array:

* [reverse](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/reverse) - Reverse the order of the elements of the array.
* [shift](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/shift) - Remove the first element from the array.
* [sort](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/sort) - Sort the elements of the array.
* [splice](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/splice) - Add or remove elements from the array.
* [unshift](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/unshift) - Add one or more elements to the front of the array.

There are also **accessor methods** that return some representation of the array:

* [concat](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/concat) - Join the array with other array(s) or value(s).
* [join](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/join) - Join all elements of the array into a string.
* [slice](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/slice) - Extract a section of the array.
* [indexOf](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/indexOf) - Find the first occurrence of a value within the array.
* [lastIndexOf](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/lastIndexOf) - Find the last occurrence of a value within the array.

And finally, **iteration methods** that apply functions to elements in the array:

* [filter](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/filter) - Create a new array with only the elements for which a predicate is true.
* [forEach](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/forEach) - Call a function for each element in the array.
* [every](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/every) - See if every element in the array satisfies a predicate.
* [map](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/map) - Create a new array with the result of a function of every element in the array.
* [some](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/some) - See if at least one element in the array satisfies a predicate.
* [reduce](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/reduce) - Apply a function to reduce the array to a single value (from left-to-right).
* [reduceRight](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/reduceRight) - Apply a function to reduce the array to a single value (from right-to-left).

