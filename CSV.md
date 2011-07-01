> [[API Reference]]

<a name="csv" href="#csv">#</a> d3.<b>csv</b>(<i>url</i>, <i>function</i>)

Issues an HTTP GET request for the comma-separated values (CSV) file at the specified *url*. The mime type of the request will be "text/csv". The request is processed asynchronously, such that this method returns immediately after opening the request. When the CSV data is available, the specified callback *function* will be invoked, being passed the [parsed rows](#parse). If an error occurs, the callback function will instead of invoked with null.

<a name="parse" href="#parse">#</a> d3.csv.<b>parse</b>(<i>string</i>)

…

<a name="parseRows" href="#parseRows">#</a> d3.csv.<b>parseRows</b>(<i>string</i>[, <i>accessor</i>])

…

<a name="format" href="#format">#</a> d3.csv.<b>format</b>(<i>rows</i>)

…