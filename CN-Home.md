> [Wiki](Home) ▸ **中文**
D3js是基于数据操作DOM的JavaScript库。D3帮助你使用HTML，SVG和CSS生动的展现数据。D3不需要将你使用在某个特定的框架，D3重点在于对主流浏览器的全兼容，同时结合了强大的虚拟化组件，以数据驱动的方式去操作DOM。

## 资源
* [介绍](http://mbostock.github.com/d3/)
* [[代码示例|Gallery]]
* [[教程|Tutorials]]
* [[API参考]]
* [[版本发布]]
* [插件](/d3/d3-plugins)
* [d3.js on Stack Overflow](http://stackoverflow.com/questions/tagged/d3.js)
* [d3-js Google Group](http://groups.google.com/group/d3-js)
* [日本語](/mbostock/d3/wiki/JP-Home)

## 浏览器支持
D3支持所谓的主流浏览器除了IE8及以前的版本.D3测试了火狐，Chrome、Safari。Opera和IE9.D3的大部分组件可以在旧的浏览器运行，D3核心库的最低运行要求：支持JavaScript和[W3C DOM](http://www.w3.org/DOM/) API.对于IE8，建议使用兼容性库[Aight](https://github.com/shawnbot/aight)库.D3采用的是Selectors API的第一级标准，你要是考虑兼容性可以预加载[Sizzle](http://sizzlejs.com/)库。你得使用主流的浏览器以便可以支持SVG和CSS3的转场特效。D3不是一个兼容的层，所以如果你的浏览器不支持这些标准，那你很不幸运，很遗憾。

## 安装
下载最新的版本:

* <http://d3js.org/d3.v3.zip>

或者, 直接连接最新的发布版本, 复制如下代码:

```html
<script src="http://d3js.org/d3.v3.min.js"></script>
```

或者, 如果你想获得所有的代码和资源包括测试：

* <https://github.com/mbostock/d3/zipball/master>

Or,从命令行获取:

```bash
git clone git://github.com/mbostock/d3.git
```

When developing locally, note that your browser may enforce strict permissions for reading files out of the local file system. **If you use [d3.xhr](wiki/Requests) locally (including d3.json et al.), you must have a local web server.** For example, you can run Python's built-in server:

    python -m SimpleHTTPServer 8888 &

or for Python 3+

    python -m http.server 8888 &

Once this is running, go to <http://localhost:8888/>.

The D3 repository should work out of the box if you just want to create new visualizations using D3. On the other hand, if you want to extend D3 with new features, fix bugs, or run tests, you should [fork the D3 repository](/mbostock/d3/fork_select), and install [Node.js](http://nodejs.org/). From the root directory of this repository, you can then install D3's dependencies:

    npm install

To run the tests, use:

    make test



