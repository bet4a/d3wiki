> [[API Reference]]

<a name="csv" href="#csv">#</a> d3.<b>csv</b>(<i>url</i>, <i>function</i>)

Issues an HTTP GET request for the comma-separated values (CSV) file at the specified *url*. The mime type of the request will be "text/csv". The request is processed asynchronously, such that this method returns immediately after opening the request. When the CSV data is available, the specified callback *function* will be invoked, being passed the [parsed rows](#parse). If an error occurs, the callback function will instead of invoked with null.

<a name="parse" href="#parse">#</a> d3.csv.<b>parse</b>(<i>string</i>)

Parses the specified *string*, which is the contents of a CSV file, returning an array of objects representing the parsed rows. Unlike the [parseRows](#parseRows) method, this method requires that the first line of the CSV file contain a comma-separated list of column names; these column names become the attributes on the returned objects. For example, consider the following CSV file:

```
Year,Make,Model,Length
1997,Ford,E350,2.34
2000,Mercury,Cougar,2.38
```

The resulting JavaScript array is:

```javascript
[
  {"Year": "1997", "Make": "Ford", "Model": "E350", "Length": "2.34"},
  {"Year": "2000", "Make": "Mercury", "Model": "Cougar", "Length": "2.38"}
]
```

Note that the values themselves are always strings; they will not be automatically converted to numbers. JavaScript may coerce strings to numbers for your automatically (for example, using the + operator). Alternatively, you can convert the strings to numbers by iterating over the returned objects:

```javascript
rows.forEach(function(o) {
  o.Year = parseInt(o.Year);
  o.Length = parseFloat(o.Length);
});
```

Using + rather than [parseInt](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/parseInt) or [parseFloat](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/parseFloat) is typically faster, though more restrictive. For example, "30px" when coerced using + returns NaN, while parseInt and parseFloat return 30.

<a name="parseRows" href="#parseRows">#</a> d3.csv.<b>parseRows</b>(<i>string</i>[, <i>accessor</i>])

…

<a name="format" href="#format">#</a> d3.csv.<b>format</b>(<i>rows</i>)

…