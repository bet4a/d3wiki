> **Wiki**

**D3.js** is a JavaScript library for manipulating documents based on data. **D3** helps you bring data to life using HTML, SVG and CSS. D3’s emphasis on web standards gives you the full capabilities of modern browsers without tying yourself to a proprietary framework, combining powerful visualization components and a data-driven approach to DOM manipulation.

## Resources

* [Introduction](http://mbostock.github.com/d3/)
* [Examples Gallery](http://github.com/mbostock/d3/wiki/Gallery)
* [Tutorials and Talks](http://github.com/mbostock/d3/wiki/Tutorials)
* [[API Reference]]
* [[Release Notes]]
* [Plugins](/d3/d3-plugins)
* [d3.js on Stack Overflow](http://stackoverflow.com/questions/tagged/d3.js)
* [d3-js Google Group](http://groups.google.com/group/d3-js)

## Browser Support

D3 supports so-called “modern” browsers, which generally means everything _except_ IE8 and below. D3 is tested against Firefox, Chrome (Chromium), Safari (WebKit), Opera and IE9. Parts of D3 may work in older browsers, as the core D3 library has minimal requirements: JavaScript and the [W3C DOM](http://www.w3.org/DOM/) API. For IE8, the compatibility library [Aight](https://github.com/shawnbot/aight) is recommended. D3 uses the [Selectors API](http://www.w3.org/TR/selectors-api/) Level 1, but you can preload [Sizzle](http://sizzlejs.com/) for compatibility. You'll need a modern browser to use [SVG](http://www.w3.org/TR/SVG/) and [CSS3 Transitions](http://www.w3.org/TR/css3-transitions/). D3 is not a compatibility layer, so if your browser doesn't support standards, you're out of luck. Sorry!

## Installing

If you just want the latest release of D3 as a JavaScript file, you can download them here:

* http://d3js.org/d3.v2.js - development
* http://d3js.org/d3.v2.min.js - production

To get the latest release and all the examples, you can find a tarball here:

* https://github.com/mbostock/d3/zipball/master

Or, from the command line:

```bash
git clone git://github.com/mbostock/d3.git
```

When running the examples locally, note that your browser may enforce strict permissions for reading files out of the local file system. Some examples use AJAX which works differently via HTTP instead of local files. **To view the examples locally, you must have a local web server.** Any web server will work; for example you can run Python's built-in server:

    python -m SimpleHTTPServer 8888 &

Once this is running, go to <http://localhost:8888/examples/>.

The D3 repository should work out of the box if you just want to create new visualizations using D3. On the other hand, if you want to extend D3 with new features, fix bugs, or run tests, you should [fork the D3 repository](/mbostock/d3/fork_select), and install a few more things. D3's test framework uses [Vows](http://vowsjs.org), which depends on [Node.js](http://nodejs.org/) and [NPM](http://npmjs.org/). If you are developing on Mac OS X, an easy way to install Node and NPM is using [Homebrew](http://mxcl.github.com/homebrew/):

    brew install node

Next, from the root directory of this repository, install D3's dependencies:

    npm install

To run the tests, use:

    npm test