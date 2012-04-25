> [Wiki](Home) ▸ [[API Reference]] ▸ [[Core]] ▸ **Requests**

It goes without saying that to visualize data, you'll need to access the data in the first place! There are a variety of ways to get data into the browser. For small datasets, you might get away with just hardcoding some values in your script. Another option is to load an external JavaScript file that defines your data as a variable. ([[JSONP|http://en.wikipedia.org/wiki/JSONP]] is a common example of this.) HTML5 even has a way of embedding data directly in the document using [[data attributes|http://ejohn.org/blog/html-5-data-attributes/]]. But, one of the most versatile ways of loading data into the browser is using an [[XMLHttpRequest|http://en.wikipedia.org/wiki/XMLHttpRequest]], or **XHR**. This allows data to be loaded asynchronously (so the rest of the page can display while data is loading), and is safer than JSONP. D3 has a variety of helper methods that simplify loading data from files.

When loading data asynchronously, code that depends on the loaded data should generally exist within the callback function. For example, see the [[calendar visualization|http://mbostock.github.com/d3/ex/calendar.html]] on the D3 website. Code that doesn't depend on data can run immediately when the page loads. Also, you may find it convenient to save loaded data to the global namespace, so that you can access it after the initial render, such as during a transition. You can do this using closures, or simply assign the loaded data to a global:

```javascript
var data; // a global

d3.json("path/to/file.json", function(json) {
  data = json;
  visualizeit();
});
```

By default, your browser will not allow cross-domain requests. (This is also true of the local file system, which is why the [[README|https://github.com/mbostock/d3/blob/master/README.md]] recommends using a local web server to host the examples.) While it is possible to use JSONP to workaround this security restriction, this is unsafe from a security perspective because it allows the external site to run arbitrary JavaScript. Instead, use the header Access-Control-Allow-Origin: * to allow your browser to request an external resource safely. For more details, see the W3C recommendation on [[Cross-Origin Resource Sharing|http://www.w3.org/TR/cors/]].

## Issuing Requests

<a name="d3_xhr" href="Requests#wiki-d3_xhr">#</a> d3.<b>xhr</b>(<i>url</i>[, <i>mime</i>], <i>callback</i>)

Issues an HTTP GET request for the specified *url*. An optional *mime* type may be specified as the second argument, such as "application/json". The request is processed asynchronously, such that this method returns immediately after opening the request. When the data is available, the specified *callback* will be invoked, being passed the [[XMLHttpRequest|http://www.w3.org/TR/XMLHttpRequest/]] object. If an error occurs, the callback function will instead be invoked with null.

This method is typically not used directly. Instead, one of the type-specific methods is used instead, such as: [text](Requests#wiki-d3_text) for plain text, [json](Requests#wiki-d3_json) for JSON, [xml](Requests#wiki-d3_xml) for XML, [html](Requests#wiki-d3_html) for HTML, and [[csv|CSV]] for comma-separated values.

<a name="d3_text" href="Requests#wiki-d3_text">#</a> d3.<b>text</b>(<i>url</i>[, <i>mime</i>], <i>callback</i>)

Issues an HTTP GET request for the text file at the specified *url*. An optional *mime* type may be specified as the second argument, such as "text/plain". The request is processed asynchronously, such that this method returns immediately after opening the request. When the text is available, the specified *callback* will be invoked, being passed the text string, per the `responseText` attribute of the request. If an error occurs, the callback function will instead be invoked with null.

<a name="d3_json" href="Requests#wiki-d3_json">#</a> d3.<b>json</b>(<i>url</i>, <i>callback</i>)

Issues an HTTP GET request for the JSON file at the specified *url*. The *mime* type "application/json" will be used. The request is processed asynchronously, such that this method returns immediately after opening the request. When the text is available, the specified *callback* will be invoked, being passed the JSON result (typically, an object or an array, depending on the contents of the file), parsed from the `responseText` attribute of the request. If an error occurs, the callback function will instead be invoked with null.

<a name="d3_xml" href="Requests#wiki-d3_xml">#</a> d3.<b>xml</b>(<i>url</i>[, <i>mime</i>], <i>callback</i>)

Issues an HTTP GET request for the XML file at the specified *url*. An optional *mime* type may be specified as the second argument, such as "application/xml". The request is processed asynchronously, such that this method returns immediately after opening the request. When the XML content is available, the specified *callback* will be invoked, being passed the root (document) element of the loaded XML content, per the `responseXML` attribute of the request. If an error occurs, the callback function will instead be invoked with null.

<a name="d3_html" href="Requests#wiki-d3_html">#</a> d3.<b>html</b>(<i>url</i>, <i>callback</i>)

Issues an HTTP GET request for the HTML file at the specified *url*. The *mime* type "text/html" will be used. The request is processed asynchronously, such that this method returns immediately after opening the request. When the HTML content is available, the specified *callback* will be invoked, being passed the root (document) element of the loaded HTML content. This is generated as a document fragment from the `responseText` attribute of the request. If an error occurs, the callback function will instead be invoked with null.

<a name="d3_csv" href="CSV">#</a> d3.<b>csv</b>(<i>url</i>, <i>callback</i>)

See [[CSV]].