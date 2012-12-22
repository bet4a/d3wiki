> [Wiki](Home) ▸ [[API Reference]] ▸ [[Core]] ▸ **Requests**

You can’t visualize data if you can’t access it! Fortunately, there are many ways to get data into the browser. For small datasets, you might hardcode the data in your script, or embed data in the DOM using [[data attributes|http://ejohn.org/blog/html-5-data-attributes/]]. For larger datasets, you could load an external script that defines your data as a global variable. ([[JSONP|http://en.wikipedia.org/wiki/JSONP]] is a common example of this.) But, the most versatile way of loading data into the browser is using an [[XMLHttpRequest|http://en.wikipedia.org/wiki/XMLHttpRequest]], or **XHR**. This allows data to be loaded _asynchronously_ (so the rest of the page can display while data is loading), and is safer than JSONP. D3’s xhr module simplifies loading and parsing data.

When loading data asynchronously, code that depends on the loaded data should generally exist within the callback function. For example, see the [[calendar visualization|http://mbostock.github.com/d3/ex/calendar.html]] on the D3 website. Code that doesn't depend on data can run immediately when the page loads. Also, you may find it convenient to save loaded data to the global namespace, so that you can access it after the initial render, such as during a transition. You can do this using closures, or simply assign the loaded data to a global:

```javascript
var data; // a global

d3.json("path/to/file.json", function(json) {
  data = json;
  visualizeit();
});
```

By default, most browsers do not allow cross-domain requests. To [enable cross-domain requests](http://enable-cors.org/), have the server set the header Access-Control-Allow-Origin: *. For more details, see the W3C recommendation on [[Cross-Origin Resource Sharing|http://www.w3.org/TR/cors/]].

## Requests

<a name="d3_xhr" href="Requests#wiki-d3_xhr">#</a> d3.<b>xhr</b>(<i>url</i>[, <i>mime</i>], <i>callback</i>)

Issues an HTTP GET request for the specified *url*. An optional *mime* type may be specified as the second argument, such as "application/json". The request is processed asynchronously, such that this method returns immediately after opening the request. When the data is available, the specified *callback* will be invoked, being passed the [[XMLHttpRequest|http://www.w3.org/TR/XMLHttpRequest/]] object. If an error occurs, the callback function will instead be invoked with null.

## Convenience Methods

Often, d3.xhr is not used directly. Instead, one of the type-specific methods is used instead, such as: [text](Requests#wiki-d3_text) for plain text, [json](Requests#wiki-d3_json) for JSON, [xml](Requests#wiki-d3_xml) for XML, [html](Requests#wiki-d3_html) for HTML, and [[csv|CSV]] for comma-separated values.

<a name="d3_text" href="Requests#wiki-d3_text">#</a> d3.<b>text</b>(<i>url</i>[, <i>mime</i>][, <i>callback</i>])

Creates a request for the text file at the specified *url*. An optional *mime* type may be specified as the second argument, such as "text/plain". If a *callback* is specified, the request is immediately issued as a GET request, and the callback will be invoked asynchronously when the file is loaded or the request fails; the callback is invoked with two arguments: the error, if any, and the response text. The response text is undefined if an error occurs. If no callback is specified, the returned request can be issued using xhr.get or similar, and handled using xhr.on.

<a name="d3_json" href="Requests#wiki-d3_json">#</a> d3.<b>json</b>(<i>url</i>[, <i>callback</i>])

Creates a request for the [JSON](http://json.org) file at the specified *url* with the mime type "application/json". If a *callback* is specified, the request is immediately issued as a GET request, and the callback will be invoked asynchronously when the file is loaded or the request fails; the callback is invoked with two arguments: the error, if any, and the parsed JSON. The parsed JSON is undefined if an error occurs. If no callback is specified, the returned request can be issued using xhr.get or similar, and handled using xhr.on.

<a name="d3_xml" href="Requests#wiki-d3_xml">#</a> d3.<b>xml</b>(<i>url</i>[, <i>mime</i>][, <i>callback</i>])

Creates a request for the XML file at the specified *url*. An optional *mime* type may be specified as the second argument, such as "application/xml". If a *callback* is specified, the request is immediately issued as a GET request, and the callback will be invoked asynchronously when the file is loaded or the request fails; the callback is invoked with two arguments: the error, if any, and the parsed XML as a [document](http://www.w3.org/TR/XMLHttpRequest/#the-responsexml-attribute). The parsed XML is undefined if an error occurs. If no callback is specified, the returned request can be issued using xhr.get or similar, and handled using xhr.on.

<a name="d3_html" href="Requests#wiki-d3_html">#</a> d3.<b>html</b>(<i>url</i>[, <i>callback</i>])

Creates a request for the HTML file at the specified *url* with the mime type "text/html". If a *callback* is specified, the request is immediately issued as a GET request, and the callback will be invoked asynchronously when the file is loaded or the request fails; the callback is invoked with two arguments: the error, if any, and the parsed HTML as a [document fragment](https://developer.mozilla.org/en-US/docs/DOM/range.createContextualFragment). The parsed HTML is undefined if an error occurs. If no callback is specified, the returned request can be issued using xhr.get or similar, and handled using xhr.on.

<a name="d3_csv" href="CSV">#</a> d3.<b>csv</b>(<i>url</i>[, <i>callback</i>])

Creates a request for the [[CSV]] file at the specified *url* with the mime type "text/csv". If a *callback* is specified, the request is immediately issued as a GET request, and the callback will be invoked asynchronously when the file is loaded or the request fails; the callback is invoked with two arguments: the error, if any, and the array of [parsed rows](CSV#wiki-parse) per [RFC 4180](http://tools.ietf.org/html/rfc4180). The rows array is undefined if an error occurs. If no callback is specified, the returned request can be issued using xhr.get or similar, and handled using xhr.on.

<a name="d3_tsv" href="CSV#wiki-tsv">#</a> d3.<b>tsv</b>(<i>url</i>[, <i>callback</i>])

Creates a request for the [TSV](CSV#wiki-d3_tsv) file at the specified *url* with the mime type "text/tab-separated-values". If a *callback* is specified, the request is immediately issued as a GET request, and the callback will be invoked asynchronously when the file is loaded or the request fails; the callback is invoked with two arguments: the error, if any, and the array of [parsed rows](CSV#wiki-tsv_parse) per [RFC 4180](http://tools.ietf.org/html/rfc4180). The rows array is undefined if an error occurs. If no callback is specified, the returned request can be issued using xhr.get or similar, and handled using xhr.on.
