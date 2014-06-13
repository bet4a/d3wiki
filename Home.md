> **Wiki**

**D3.js** is a JavaScript library for manipulating documents based on data. **D3** helps you bring data to life using HTML, SVG and CSS. D3’s emphasis on web standards gives you the full capabilities of modern browsers without tying yourself to a proprietary framework, combining powerful visualization components and a data-driven approach to DOM manipulation.

## Resources

* [Introduction](http://d3js.org/)
* [[Examples Gallery|Gallery]]
* [[Tutorials and Talks|Tutorials]]
* [[API Reference]]
* [Release Notes](/mbostock/d3/releases)
* [Plugins](/d3/d3-plugins)
* [d3.js on Stack Overflow](http://stackoverflow.com/questions/tagged/d3.js)
* [d3-js Google Group](http://groups.google.com/group/d3-js)
* [d3-js Runnable.com](http://runnable.com/d3.js)
* [한국어](https://github.com/zziuni/d3/wiki)
* [日本語](/mbostock/d3/wiki/JP-Home)
* [中文](/mbostock/d3/wiki/CN-Home)
* [[API Reference (русскоязычная версия)]]
* [API Kaynak - Türkçe](https://github.com/ahmetkurnaz/d3/wiki)


## Browser Support

D3 supports so-called “modern” browsers, which generally means everything _except_ IE8 and below. D3 is tested against Firefox, Chrome (Chromium), Safari (WebKit), Opera and IE9. Parts of D3 may work in older browsers, as the core D3 library has minimal requirements: JavaScript and the [W3C DOM](http://www.w3.org/DOM/) API. For IE8, the compatibility library [Aight](https://github.com/shawnbot/aight) is recommended. D3 uses the [Selectors API](http://www.w3.org/TR/selectors-api/) Level 1, but you can preload [Sizzle](http://sizzlejs.com/) for compatibility. You'll need a modern browser to use [SVG](http://www.w3.org/TR/SVG/) and [CSS3 Transitions](http://www.w3.org/TR/css3-transitions/). D3 is not a compatibility layer, so if your browser doesn't support standards, you're out of luck. Sorry!

D3 works in Node.js as well. See <https://groups.google.com/forum/#!msg/d3-js/JyldAkWkTvI/n8thanJeGvAJ> for details.

## Installing

Download the latest version here:

* <https://github.com/mbostock/d3/releases>

Or, to link directly to the latest release, copy this snippet:

```html
<script src="http://d3js.org/d3.v3.min.js" charset="utf-8"></script>
```

Or, if you want the full repository including tests:

* <https://github.com/mbostock/d3/zipball/master>

When developing locally, note that your browser may enforce strict permissions for reading files out of the local file system. **If you use [d3.xhr](wiki/Requests) locally (including d3.json et al.), you must have a local web server.** For example, you can run Python's built-in server:

    python -m SimpleHTTPServer 8888 &

or for Python 3+

    python -m http.server 8888 &

Once this is running, go to <http://localhost:8888/>.

D3 supports the asynchronous module definition (AMD) API. For example, if you use [RequireJS](http://requirejs.org/), you may load as follows:

```js
require.config({paths: {d3: "http://d3js.org/d3.v3.min"}});

require(["d3"], function(d3) {
  console.log(d3.version);
});
```

## Modifying

If you want to modify how D3 is implemented, click the "Fork" button in the top-right corner of this page, and then clone your fork from the command line by replacing *username* with your GitHub username:

```bash
git clone git://github.com/username/d3.git
```

The D3 repository should work out of the box if you just want to create new visualizations using D3. On the other hand, if you want to extend D3 with new features, fix bugs, or run tests, you should [fork the D3 repository](/mbostock/d3), and install [Node.js](http://nodejs.org/) (version 0.10.x or higher). From the root directory of this repository, you can then install D3's dependencies:

    npm install

To run the tests, use:

    make test

