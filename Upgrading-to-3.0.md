Most changes to D3 are carefully designed to be backwards-compatible, which makes it easier to upgrade. If you’ve been linking to the official [d3.v2.js](http://d3js.org/d3.v2.js), you’ve been getting bug fixes, performance improvements, and new features automatically. Unfortunately, not all changes can be made backwards-compatible; periodically, these potentially disruptive changes are needed to keep the API and the code lean by removing deprecated, broken or confusing functionality.

D3 3.0 is the first major release since 2.0 was released last August. Since 2.0.0, there have been 10 minor releases and 37 patch releases. 3.0 includes significant new features and improvements, but in accordance with [semantic versioning](http://semver.org/), this major release also includes several backwards-incompatibilities. This document will guide you on how to upgrade from 2.x to 3.0.

## Requests

One of the first things you are likely to notice is that the d3.xhr callback interface has changed. In 2.x, you might have written code like this:

```js
d3.json("my-data.json", function(data) {
  console.log("there are " + data.length + " elements in my dataset");
});
```

In V3, the callback function takes an additional argument, `error`. If there is an error fetching the requested resource, then the error argument contains information that you can use to diagnose the problem or inform the user, such as whether the file is missing or the server is unavailable. The second argument contains the contents of the resource. So, the simplest fix is to change the callback signature:

```js
d3.json("my-data.json", function(error, data) {
  console.log("there are " + data.length + " elements in my dataset");
});
```

Of course, this code still ignores the error. You might prefer to handle errors gracefully:

```js
d3.json("my-data.json", function(error, data) {
  if (error != null) return console.log("there was an error loading the data: " + error);
  console.log("there are " + data.length + " elements in my dataset");
});
```

The reason for this change is two-fold. First, it adopts the standard {error, result} asynchronous callback convention established by Node.js. This makes it familiar to many JavaScript developers, which makes the API easier to learn. Even better, it means you can use d3.xhr methods with helpers for asynchronous JavaScript, such as [Queue.js](https://github.com/mbostock/queue). For example, say you wanted to load two resources for a map visualization, a GeoJSON file "us-states.json", and a data file "us-state-populations.tsv". In 2.x, you probably would have loaded these serially by nesting callbacks:

```js
d3.json("us-states.json", function(states) {
  d3.tsv("us-state-populations.tsv", function(statePopulations) {
    // display map here
  });
});
```

Loading resources serially is slow! It's better to parallelize those requests, which is now easy in 3.0:

```js
queue()
    .defer(d3.json, "us-states.json")
    .defer(d3.tsv, "us-state-populations.tsv")
    .await(ready);

function ready(error, states, statePopulations) {
  // display map here
}
```

The other reason this change was made is to make it more obvious that these requests can fall. That first argument, error, is a nagging reminder that you might want to handle errors when loading resources by displaying a suitable notification to your users and perhaps retrying the request.
