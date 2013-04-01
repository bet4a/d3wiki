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

如果你想获得包括测试在内的所有资源，如下连接：

* <https://github.com/mbostock/d3/zipball/master>

从git命令行获取:

```bash
git clone git://github.com/mbostock/d3.git
```
当你本地开发时，注意有的浏览器或许强制限制读取本地文件系统之外的文件。如果你在本地使用[d3.xhr](wiki/Requests)，其中包括（d3.json et al.），你必须有一个本地的Web服务器。比如，有可以运行Python内置的服务器：

```bash
python -m SimpleHTTPServer 8888 &
```

如果是Python 3+

```bash
python -m http.server 8888 &
```

一旦服务器运行起来，访问 <http://localhost:8888/>.

如果你使用的D3去开发一下新的虚拟化展现，D3的资源库可以立即使用，另外，如果你想扩展D3的功能，修改bug或者运行测试，你应该创建自己的[D3资源库分支](/mbostock/d3/fork_select)，同时安装[Node.js](http://nodejs.org/)。从资源库的根目录，可以安装D3的依赖库：

    npm install

接着运行测试, 使用命令:

    make test