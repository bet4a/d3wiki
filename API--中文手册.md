> [Wiki](主页) ▸ **API 参考文档**

* 本文档是D3官方文档中文翻译，并保持与[最新版](https://github.com/mbostock/d3/wiki/API-Reference)同步。
* 如发现翻译不当或有其他问题可以通过以下方式联系译者:
* 邮箱：zhang_tianxu@sina.com
* QQ群：[D3数据可视化](http://jq.qq.com/?_wv=1027&k=ZGcqYF)205076374，[大数据可视化](http://jq.qq.com/?_wv=1027&k=S8wGMe)436442115

D3库中所有函数都在“d3”命名空间内。

D3 使用[语义版本命名](http://semver.org)。 你可以使用“d3.version”查看D3的最新版本

D3 API总览

* [行为](#d3behavior-behaviors) - 可重用的交互行为。
* [核心](#d3-core) - 包括选择器，过渡，数据处理，本地化，颜色等。
* [地理](#d3geo-geography) - 球面坐标，经纬度运算。
* [几何](#d3geom-geometry) - 提供绘制2D几何图形的实用工具。
* [布局](#d3layout-layouts) - 推导定位元素的辅助数据。
* [比例尺](#d3scale-scales) - 数据编码和视觉编码之间转换。
* [可缩放矢量图形](#d3svg-svg) - 提供用于创建可伸缩矢量图形的实用工具。
* [时间](#d3time-time) - 解析或格式化时间，计算日历的时间间隔等。

## [d3 (核心)](核心函数)

### [选择器](选择器)

* [d3.event](选择器#d3_event) - 访问用于交互的当前用户事件。
* [d3.mouse](选择器#d3_mouse) - 获取相对于指定容器的鼠标位置。
* [d3.select](选择器#d3_select) - 从当前文档中选择一个元素。
* [d3.selectAll](选择器#d3_selectAll) - 从当前文档中选择多个元素。
* [d3.selection](选择器#d3_selection) - 增强选择器原型，或测试实例类型。
* [d3.touch](选择器#d3_touch) - 获取相对于指定容器的单点触摸位置。
* [d3.touches](选择器#d3_touches) - 获取相对于指定容器的多点触摸位置。
* [selection.append](选择器#append) - 创建并追加一个新元素。
* [selection.attr](选择器#attr) - 取得或设置属性的值。
* [selection.call](选择器#call) - 为当前选择调用一个函数。
* [selection.classed](选择器#classed) - 添加或移除CSS类。
* [selection.data](选择器#data) - 在计算相关的连接时，取得或设置一组元素的数据。
* [selection.datum](选择器#datum) - 取得或设置单个元素的数据，不必计算连接。
* [selection.each](选择器#each) - 为每个选中的元素调用一个函数。
* [selection.empty](选择器#empty) - 如果选择是空则返回true。
* [selection.enter](选择器#enter) - 为缺失的元素返回占位符。
* [selection.exit](选择器#exit) - 返回不再需要的元素。
* [selection.filter](选择器#filter) - 基于数据过滤选择。
* [selection.html](选择器#html) - 取得或设置innerHTML内容。
* [selection.insert](选择器#insert) - 在已存在元素之前创建并插入一个元素。
* [selection.interrupt](选择器#interrupt) - 如果有过渡的话，立即中断当前的过渡。
* [selection.node](选择器#node) - 返回选择中的第一个节点。
* [selection.on](选择器#on) - 为交互添加或移除事件监听器。
* [selection.order](选择器#order) - 重排列文档中的元素，以匹配选择。
* [selection.property](选择器#property) - 取得或设置行内属性。
* [selection.remove](选择器#remove) - 从当前文档中移除当前元素。
* [selection.select](选择器#select) - 为每个选中元素的在选择一个后代元素。
* [selection.selectAll](选择器#selectAll) - 为每个选中元素的在选择多个后代元素。
* [selection.size](选择器#size) - 返回选择中的元素数。
* [selection.sort](选择器#sort) - 基于数据排列文档中的元素。
* [selection.style](选择器#style) - 取得或设置样式属性。
* [selection.text](选择器#text) - 取得或设置文本内容。
* [selection.transition](选择器#transition) - 在选中元素上开启过渡。

### [过渡](过渡)

* [d3.ease](过渡#d3_ease) - 自定义过渡时间。
* [d3.timer](过渡#d3_timer) - 开启一段自定义动画定时器。
* [d3.interpolate](过渡#d3_interpolate) - 插补两个值。
* [d3.interpolateArray](过渡#d3_interpolateArray) - 插补两个数组。
* [d3.interpolateHcl](过渡#d3_interpolateHcl) - 插补两个HCL颜色值。
* [d3.interpolateHsl](过渡#d3_interpolateHsl) - 插补两个HSL颜色值。
* [d3.interpolateLab](过渡#d3_interpolateLab) - 插补两个L\*a\*b\*颜色值。
* [d3.interpolateNumber](过渡#d3_interpolateNumber) - 插补两个数字值。
* [d3.interpolateObject](过渡#d3_interpolateObject) - 插补两个任意对象。
* [d3.interpolateRgb](过渡#d3_interpolateRgb) - 插补两个RGB颜色值。
* [d3.interpolateRound](过渡#d3_interpolateRound) - 插补两个整数。
* [d3.interpolateString](过渡#d3_interpolateString) - 插补两个字符串。
* [d3.interpolateTransform](过渡#d3_interpolateTransform) - 插补两个2D矩阵变换。
* [d3.interpolateZoom](过渡#d3_interpolateZoom) - 在两个点之间平滑地缩放平移。
* [d3.interpolators](过渡#d3_interpolators) - 注册一个自定义的插值器。
* [d3.timer.flush](过渡#d3_timer_flush) - 立即执行一个0延迟的定时器。
* [d3.transition](过渡#d3_transition) - 开启一个动画过渡。
* [ease](过渡#_ease) - 一个参数化的缓动函数。
* [interpolate](过渡#_interpolate) - 一个参数化的插值器函数。
* [transition.attr](过渡#attr) - 平滑地过渡到一个新的属性值。
* [transition.attrTween](过渡#attrTween) - 在两个属性值之间平滑地过渡。
* [transition.call](过渡#call) - 为当前的过渡调用一个函数。
* [transition.delay](过渡#delay) - 指定每个元素的延迟时间（以毫秒为单位）。
* [transition.duration](过渡#duration) - 指定每个元素的持续时间（以毫秒为单位）。
* [transition.each](过渡#each) - 为过渡结束时间添加一个监听器。
* [transition.ease](过渡#ease) - 指定一个过渡的缓动函数。
* [transition.empty](过渡#empty) - 如果过渡是空则返回true。
* [transition.filter](过渡#filter) - 基于数据过滤一个过渡。
* [transition.node](过渡#node) - 返回过渡中的第一个节点。
* [transition.remove](过渡#remove) - 在过渡的最后移除选中的元素。
* [transition.select](过渡#select) - 为每个选中的元素在一个子元素开启一段过渡。
* [transition.selectAll](过渡#selectAll) - 为每个选中的元素在多个子元素开启一段过渡。
* [transition.size](过渡#size) - 返回在选择中元素的数量。
* [transition.style](过渡#style) - 平滑地过渡到一个新的样式值。
* [transition.styleTween](过渡#styleTween) - 在两个样式属性值之间平滑地过渡。
* [transition.text](过渡#text) - 在过渡开始时设置文本内容。
* [transition.transition](过渡#transition) - 当这次过渡结束时，在相同的元素上开启另一段过渡。
* [transition.tween](过渡#tween) - 指定一个自定义的补间操作符作为过渡的一部分运行。

### [数组](数组)

* [d3.ascending](数组#d3_ascending) - 为排序比较两个值。
* [d3.bisectLeft](数组#d3_bisectLeft) - 在排序数组中检索值。
* [d3.bisector](数组#d3_bisector) - 二等分使用访问器或比较器。
* [d3.bisectRight](数组#d3_bisectRight) - 在排序数组中检索值。
* [d3.bisect](数组#d3_bisect) - 在排序数组中检索值。
* [d3.descending](数组#d3_descending) - 为排序比较两个值。
* [d3.deviation](数组#d3_deviation) - 计算一组数据的标准差。
* [d3.entries](数组#d3_entries) - 列出一个关联数组的键值对实体。
* [d3.extent](数组#d3_extent) - 找出一个数组中的最大值和最小值。
* [d3.keys](数组#d3_keys) - 列出一个关联数组中的键。
* [d3.map](数组#d3_map) - 构建一个新的map。
* [d3.max](数组#d3_max) - 找出一个数组中的最大值。
* [d3.mean](数组#d3_mean) - 计算一组数据的算数平均值。
* [d3.median](数组#d3_median) - 计算一组数据的算数中值。
* [d3.merge](数组#d3_merge) - 合并多个数组为一个数组。
* [d3.min](数组#d3_min) - 找出一个数组中的最小值。
* [d3.nest](数组#d3_nest) - 分层地分组数组元素。
* [d3.pairs](数组#d3_pairs) - 返回一个元素的相邻对数组。
* [d3.permute](数组#d3_permute) - 按照数组的索引重新排序数组元素。
* [d3.quantile](数组#d3_quantile) - 为一个排好序的数字数组的分位数。
* [d3.range](数组#d3_range) - 产生一系列的数值。
* [d3.set](数组#d3_set) - 构建一个新的集合。
* [d3.shuffle](数组#d3_shuffle) - 随机化一个数组的顺序。
* [d3.sum](数组#d3_sum) - 计算数字数组的和。
* [d3.transpose](数组#d3_transpose) - 转置一个数组的数组。
* [d3.values](数组#d3_values) - 列出关联数组的值。
* [d3.variance](数组#d3_variance) - 计算数字数组的方差。
* [d3.zip](数组#d3_zip) - 转置数组的可变数量。
* [map.empty](数组#map_empty) - 如果map不包含元素就返回true。
* [map.entries](数组#map_entries) - 返回map的实体数组。
* [map.forEach](数组#map_forEach) - 为每个指定的实体调用一个函数。
* [map.get](数组#map_get) - 为指定的键返回值。
* [map.has](数组#map_has) - 如果map包含指定的值则返回true。
* [map.keys](数组#map_keys) - 返回map的键数组。
* [map.remove](数组#map_remove) - 为指定的键移除值。
* [map.set](数组#map_set) - 为指定的键设置值。
* [map.size](数组#map_size) - 返回map的实体数量。
* [map.values](数组#map_values) - 返回map的值数组。
* [nest.entries](数组#nest_entries) - 返回一组键-值元组
* [nest.key](数组#nest_key) - 在嵌套层级中添加一个级别。
* [nest.map](数组#nest_map) - 返回一个关联数组。
* [nest.rollup](数组#nest_rollup) - 为叶子值指定一个汇总函数。
* [nest.sortKeys](数组#nest_sortKeys) - 按照键排序叶子嵌套级别。
* [nest.sortValues](数组#nest_sortValues) - 按照值排序叶子嵌套级别。
* [set.add](数组#set_add) - 添加指定的值。
* [set.empty](数组#set_empty) - 如果集合不含元素的话返回true。
* [set.forEach](数组#set_forEach) - 为集合中的每个元素调用指定的函数。
* [set.has](数组#set_has) - 如果集合中包含指定值就返回true。
* [set.remove](数组#set_remove) - 移除指定的值。
* [set.size](数组#set_size) - 返回集合中的元素数量。
* [set.values](数组#set_values) - 返回集合中的值数组。

### [数学](数学)

* [d3.random.bates](数学#random_bates) - 生成具有贝茨分布规律的随机数。
* [d3.random.irwinHall](数学#random_irwinHall) - 生成具有Irwin–Hall分布规律的随机数。
* [d3.random.logNormal](数学#random_logNormal) - 生成具有对数正态分布规律的随机数。
* [d3.random.normal](数学#random_normal) - 生成具有正态分布规律的随机数。
* [d3.transform](数学#d3_transform) - 计算2D放射变换的标准形式。

### [请求](请求)

* [d3.csv](请求#csv) - 请求一个CSV（逗号分隔值）的文件。
* [d3.html](请求#d3_html) - 请求一个HTML文档片段。
* [d3.json](请求#d3_json) - 请求一个JSON对象。
* [d3.text](请求#d3_text) - 请求一个text文件。
* [d3.tsv](请求#tsv) - 请求一个TSV（制表符分隔值）的文件。
* [d3.xhr](请求#d3_xhr) - 使用XMLHttpRequest请求一个资源。
* [d3.xml](请求#d3_xml) - 请求一个XML文档片段。
* [xhr.abort](请求#abort) - 终止未完成的请求。
* [xhr.get](请求#get) - 发送一个GET请求。
* [xhr.header](请求#header) - 设置一个请求头。
* [xhr.mimeType](请求#mimeType) - 设置一个接受请求头并覆盖响应的MIME类型。
* [xhr.on](请求#on) - 为“progress”，“load”或“error”事件添加一个事件监听器。
* [xhr.post](请求#post) - 发送一个POST请求。
* [xhr.response](请求#response) - 设置一个响应映射函数。
* [xhr.send](请求#send) - 使用指定的数据和函数发送一个请求。

### [格式化](格式化)

* [d3.format](格式化#d3_format) - 将一个数组格式化为字符串。
* [d3.formatPrefix](格式化#d3_formatPrefix) - 为指定的值和精度返回[SI 前缀](http://en.wikipedia.org/wiki/Metric_prefix)。
* [d3.requote](格式化#d3_requote) - 将字符串转义为正则表达式。
* [d3.round](格式化#d3_round) - 将值四舍五入到指定小数位。

### [CSV格式化(d3.csv)](CSV)

* [d3.csv.formatRows](CSV#formatRows) - 格式化一组元组为CSV字符串。
* [d3.csv.format](CSV#format) - 格式化一组对象为CSV字符串。
* [d3.csv.parseRows](CSV#parseRows) - 解析CSV字符串为元组，忽略首行。
* [d3.csv.parse](CSV#parse) - 把首行数据CSV字符串解析为对象。
* [d3.csv](CSV#csv) - 请求一个CSV文件。
* [d3.dsv](CSV#dsv) - 为指定的分隔符和mime类型创建一个解析器/格式化器。
* [d3.tsv.formatRows](CSV#tsv_formatRows) - 格式化一组元组为TSV字符串。
* [d3.tsv.format](CSV#tsv_format) - 格式化一组对象为TSV字符串。
* [d3.tsv.parseRows](CSV#tsv_parseRows) - 解析TSV字符串为元组，忽略首行。
* [d3.tsv.parse](CSV#tsv_parse) - 把首行数据TSV字符串解析为对象。
* [d3.tsv](CSV#tsv) - 请求一个TSV文件。

### [本地化](本地化)

* [d3.locale](本地化#d3_locale) - 使用指定的字符串创建一个本地化。
* [locale.numberFormat](本地化#locale_numberFormat) - 创建一个新的数字格式化器。
* [locale.timeFormat](本地化#locale_timeFormat) - 创建一个新的时间格式化器/解析器。

### [颜色](颜色)

* [d3.hcl](颜色#d3_hcl) - 指定一种颜色，创建一个HCL颜色对象。
* [d3.hsl](颜色#d3_hsl) - 指定一种颜色，创建一个HSL颜色对象。
* [d3.lab](颜色#d3_lab) - 指定一种颜色，创建一个L\*a\*b\*颜色对象。
* [d3.rgb](颜色#d3_rgb) - 指定一种颜色，创建一个RGB颜色对象。
* [hcl.brighter](颜色#hcl_brighter) - 增强颜色的亮度，变化幅度由参数决定。
* [hcl.darker](颜色#hcl_darker) - 减弱颜色的亮度，变化幅度由参数决定。
* [hcl.rgb](颜色#hcl_rgb) - 将HCL颜色对象转化成RGB颜色对象。
* [hcl.toString](颜色#hcl_toString) - HCL颜色对象转化为字符串格式。
* [hsl.brighter](颜色#hsl_brighter) - 增强颜色的亮度，变化幅度由参数决定。
* [hsl.darker](颜色#hsl_darker) - 减弱颜色的亮度，变化幅度由参数决定。
* [hsl.rgb](颜色#hsl_rgb) - 将HSL颜色对象转化成RGB颜色对象。
* [hsl.toString](颜色#hsl_toString) - 将HSL颜色对象转化为字符串格式。
* [lab.brighter](颜色#lab_brighter) - 增强颜色的亮度，变化幅度由参数决定。
* [lab.darker](颜色#lab_darker) - 减弱颜色的亮度，变化幅度由参数决定。
* [lab.rgb](颜色#lab_rgb) - 将L\*a\*b\*颜色对象转化成RGB颜色对象。
* [lab.toString](颜色#lab_toString) - 将L\*a\*b\*颜色对象转化为字符串格式。
* [rgb.brighter](颜色#rgb_brighter) - 增强颜色的亮度，变化幅度由参数决定。
* [rgb.darker](颜色#rgb_darker) - 减弱颜色的亮度，变化幅度由参数决定。
* [rgb.hsl](颜色#rgb_hsl) - 将RGB颜色对象转化成HSL颜色对象。
* [rgb.toString](颜色#rgb_toString) - 将RGB颜色对象转化为字符串格式。

### [命名空间](命名空间)

* [d3.ns.prefix](命名空间#prefix) - 访问或扩展已知的XML命名空间。
* [d3.ns.qualify](命名空间#qualify) - 限定一个前缀名称，例如"xlink:href".

### [内部](内部)

* [d3.dispatch](内部#d3_dispatch) - 创建一个定制的事件分发器。
* [d3.functor](内部#functor) - 创建一个函数并返回一个常量。
* [d3.rebind](内部#rebind) - 重新绑定get/set方法到一个子类上。
* [dispatch.on](内部#dispatch_on) - 注册或者解除注册事件监听器。
* [dispatch.type](内部#_dispatch) - 为指定的监听器分发事件。

## [d3.scale (比例尺)](比例尺)

### [定量比例尺](Quantitative-Scales#quantitative)

* [d3.scale.identity](Quantitative-Scales#identity) - 构建一个线性恒等比例尺。
* [d3.scale.linear](Quantitative-Scales#linear) - 构建一个线性定量比例尺。
* [d3.scale.log](Quantitative-Scales#log) - 构建一个对数比例尺。
* [d3.scale.pow](Quantitative-Scales#pow) - 构建一个指数比例尺。
* [d3.scale.quantile](Quantitative-Scales#quantile) - 构建一个分位数比例尺。
* [d3.scale.quantize](Quantitative-Scales#quantize) - 构建一个量化比例尺（值域离散）。
* [d3.scale.sqrt](Quantitative-Scales#sqrt) - 构建一个平方根比例尺。
* [d3.scale.threshold](Quantitative-Scales#threshold) - 构建一个临界值比例尺（值域离散）。
* [identity.copy](Quantitative-Scales#identity_copy) - 复制比例尺。
* [identity.domain](Quantitative-Scales#identity_domain) - 取得或设置比例尺的定义域。
* [identity.invert](Quantitative-Scales#_identity) - 等价于恒等函数。
* [identity.range](Quantitative-Scales#identity_domain) - 等价于identity.domain。
* [identity.tickFormat](Quantitative-Scales#identity_tickFormat) - 获取一个用来展示刻度值得格式化器。
* [identity.ticks](Quantitative-Scales#identity_ticks) - 取得定义域中典型的值。
* [identity](Quantitative-Scales#_identity) - 恒等函数。
* [linear.clamp](Quantitative-Scales#linear_clamp) - 启用或者关闭值域的闭合。
* [linear.copy](Quantitative-Scales#linear_copy) - 复制比例尺。
* [linear.domain](Quantitative-Scales#linear_domain) - 取得或设置比例尺的定义域。
* [linear.interpolate](Quantitative-Scales#linear_interpolate) - 取得或设置输出插值器。
* [linear.invert](Quantitative-Scales#linear_invert) - 取得输出值对应的输入值。
* [linear.nice](Quantitative-Scales#linear_nice) - 扩展比例尺的定义域为一个优化的定义域。
* [linear.rangeRound](Quantitative-Scales#linear_rangeRound) - 设置比例尺的输出范围，并四舍五入。
* [linear.range](Quantitative-Scales#linear_range) - 取得或设置比例尺的输出范围。
* [linear.tickFormat](Quantitative-Scales#linear_tickFormat) - 获取一个用来展示刻度值得格式化器。
* [linear.ticks](Quantitative-Scales#linear_ticks) - 取得定义域中典型的值。
* [linear](Quantitative-Scales#_linear) - 取得输入值对应的输出值。
* [log.clamp](Quantitative-Scales#log_clamp) - 启用或者关闭值域的闭合。
* [log.copy](Quantitative-Scales#log_copy) - 复制比例尺。
* [log.domain](Quantitative-Scales#log_domain) - 取得或设置比例尺的定义域。
* [log.interpolate](Quantitative-Scales#log_interpolate) - 取得或设置输出插值器。
* [log.invert](Quantitative-Scales#log_invert) - 取得输出值对应的输入值。
* [log.nice](Quantitative-Scales#log_nice) - 扩展比例尺的定义域为一个优化的10的次方。
* [log.rangeRound](Quantitative-Scales#log_rangeRound) - 设置比例尺的输出范围，并四舍五入。
* [log.range](Quantitative-Scales#log_range) - 取得或设置比例尺的输出范围。
* [log.tickFormat](Quantitative-Scales#log_tickFormat) - 获取一个用来展示刻度值得格式化器。
* [log.ticks](Quantitative-Scales#log_ticks) - 取得定义域中典型的值。
* [log](Quantitative-Scales#_log) - 取得输入值对应的输出值。
* [pow.clamp](Quantitative-Scales#pow_clamp) - 启用或者关闭值域的闭合。
* [pow.copy](Quantitative-Scales#pow_copy) - 复制比例尺。
* [pow.domain](Quantitative-Scales#pow_domain) - 取得或设置比例尺的定义域。
* [pow.exponent](Quantitative-Scales#pow_exponent) - 取得或设置指数。
* [pow.interpolate](Quantitative-Scales#pow_interpolate) - 取得或设置输出插值器。
* [pow.invert](Quantitative-Scales#pow_invert) - 取得输出值对应的输入值。
* [pow.nice](Quantitative-Scales#pow_nice) - 扩展比例尺的定义域为一个优化的定义域。
* [pow.rangeRound](Quantitative-Scales#pow_rangeRound) - 设置scale的输出范围，并四舍五入。
* [pow.range](Quantitative-Scales#pow_range) - 取得或设置比例尺的值域。
* [pow.tickFormat](Quantitative-Scales#pow_tickFormat) - 获取一个用来展示刻度值得格式化器。
* [pow.ticks](Quantitative-Scales#pow_ticks) - 取得定义域中典型的值。
* [pow](Quantitative-Scales#_pow) - 取得输出值对应的输入值。
* [quantile.copy](Quantitative-Scales#quantile_copy) - 复制比例尺。
* [quantile.domain](Quantitative-Scales#quantile_domain) - 取得或设置比例尺的定义域（离散的值）。
* [quantile.invertExtent](Quantitative-Scales#quantile_invertExtent) - 取得输出值对应的输入值。
* [quantile.quantiles](Quantitative-Scales#quantile_quantiles) - 取得比例尺的分位数箱阈值。
* [quantile.range](Quantitative-Scales#quantile_range) - 取得或设置比例尺的值域（离散的值）。
* [quantile](Quantitative-Scales#_quantile) - 取得输入值对应的输出值。
* [quantize.copy](Quantitative-Scales#quantize_copy) - 复制比例尺。
* [quantize.domain](Quantitative-Scales#quantize_domain) - 取得或设置比例尺的定义域。
* [quantize.invertExtent](Quantitative-Scales#quantize_invertExtent) - 取得输出值对应的输入值。
* [quantize.range](Quantitative-Scales#quantize_range) - 取得或设置比例尺的值域（离散的值）。
* [quantize](Quantitative-Scales#_quantize) - 取得输入值对应的输出值。
* [threshold.copy](Quantitative-Scales#threshold_copy) - 复制比例尺。
* [threshold.domain](Quantitative-Scales#threshold_domain) - 取得或设置比例尺的定义域。
* [threshold.invertExtent](Quantitative-Scales#threshold_invertExtent) - 取得输出值对应的输入值。
* [threshold.range](Quantitative-Scales#threshold_range) - 取得或设置比例尺的值域（离散的值）。
* [threshold](Quantitative-Scales#_threshold) - 取得输入值对应的输出值。

### [序数比例尺](Ordinal-Scales#ordinal)

* [d3.scale.category10](Ordinal-Scales#category10) - 构造一个10种颜色的序数比例尺。
* [d3.scale.category20b](Ordinal-Scales#category20b) - 构造一个20种颜色的序数比例尺。
* [d3.scale.category20c](Ordinal-Scales#category20c) - 构造一个20种颜色的序数比例尺。
* [d3.scale.category20](Ordinal-Scales#category20) - 构造一个20种颜色的序数比例尺。
* [d3.scale.ordinal](Ordinal-Scales#ordinal) - 构造一个序数比例尺。
* [ordinal.copy](Ordinal-Scales#ordinal_copy) - 复制比例尺。
* [ordinal.domain](Ordinal-Scales#ordinal_domain) - 取得或设置比例尺的定义域。
* [ordinal.rangeBands](Ordinal-Scales#ordinal_rangeBands) - 为离散的块划分连续的值域。
* [ordinal.rangeBand](Ordinal-Scales#ordinal_rangeBand) - 取得离散块的宽度。
* [ordinal.rangeExtent](Ordinal-Scales#ordinal_rangeExtent) - 取得值域的范围。
* [ordinal.rangePoints](Ordinal-Scales#ordinal_rangePoints) - 为离散的点划分连续的值域。
* [ordinal.rangeRoundBands](Ordinal-Scales#ordinal_rangeRoundBands) - 为离散的块划分连续的值域。
* [ordinal.rangeRoundPoints](Ordinal-Scales#ordinal_rangeRoundPoints) - 为离散的点划分连续的值域。
* [ordinal.range](Ordinal-Scales#ordinal_range) - 取得或设置比例尺的值域。
* [ordinal](Ordinal-Scales#_ordinal) - 取得输入值对应的输出值。

## [d3.svg (SVG)](SVG)

### [形状](形状)

* [arc.centroid](SVG-Shapes#arc_centroid) - 计算弧中心。
* [arc.cornerRadius](SVG-Shapes#arc_cornerRadius) - 获取或设置拐角（corner）半径访问器。
* [arc.endAngle](SVG-Shapes#arc_endAngle) - 获取或设置结束角度访问器。
* [arc.innerRadius](SVG-Shapes#arc_innerRadius) - 获取或设置内半径访问器。
* [arc.outerRadius](SVG-Shapes#arc_outerRadius) - 获取或设置外半径访问器。
* [arc.padAngle](SVG-Shapes#arc_padAngle) - 获取或设置填补（pad）角度访问器。
* [arc.padRadius](SVG-Shapes#arc_padRadius) - 获取或设置填补（pad）半径访问器。
* [arc.startAngle](SVG-Shapes#arc_startAngle) - 获取或设置开始角度访问器。
* [arc](SVG-Shapes#_arc) - 生成一个像饼图或圆环图中的固定弧度。
* [area.angle](SVG-Shapes#area_radial_angle) - 获取或设置*角度*访问器。
* [area.defined](SVG-Shapes#area_defined) - 控制面积在给定点是否是有定义的。
* [area.defined](SVG-Shapes#area_radial_defined) - 控制径向面积在给定点是否是有定义的。
* [area.endAngle](SVG-Shapes#area_radial_endAngle) - 获取或设置*角度*（顶线）访问器。
* [area.innerRadius](SVG-Shapes#area_radial_innerRadius) - 获取或设置内*半径*（基线）访问器。
* [area.interpolate](SVG-Shapes#area_interpolate) - 获取或设置插值模式。
* [area.outerRadius](SVG-Shapes#area_radial_outerRadius) - 获取或设置外*半径*（顶线）访问器。
* [area.radius](SVG-Shapes#area_radial_radius) - 获取或设置*半径*访问器。
* [area.startAngle](SVG-Shapes#area_radial_startAngle) - 获取或设置*角度*（基线）访问器。
* [area.tension](SVG-Shapes#area_tension) - 获取或设置基本样条线的张力。
* [area.x0](SVG-Shapes#area_x0) - 获取或设置*x0*-坐标（基线）访问器。
* [area.x1](SVG-Shapes#area_x1) - 获取或设置*x1*-坐标（顶线）访问器。
* [area.x](SVG-Shapes#area_x) - 获取或设置*x*-坐标访问器。
* [area.y0](SVG-Shapes#area_y0) - 获取或设置*y0*-坐标（基线）访问器。
* [area.y1](SVG-Shapes#area_y1) - 获取或设置*y1*-坐标（顶线）访问器。
* [area.y](SVG-Shapes#area_y) - 获取或设置*y*-坐标访问器。
* [area](SVG-Shapes#_area) - 生成一个像面积图中的分段线性面积。
* [area](SVG-Shapes#_area_radial) - 生成一个像极坐标面积图中的分段线性面积。
* [chord.endAngle](SVG-Shapes#chord_endAngle) - 获取或设置圆弧结束角访问器。
* [chord.radius](SVG-Shapes#chord_radius) - 获取或设置圆弧半径访问器。
* [chord.source](SVG-Shapes#chord_source) - 获取或设置圆弧来源圆弧访问器。
* [chord.startAngle](SVG-Shapes#chord_startAngle) - 获取或设置圆弧开始角访问器。
* [chord.target](SVG-Shapes#chord_target) - 获取或设置目标圆弧访问器。
* [chord](SVG-Shapes#_chord) - 在弦图中生成一个二次贝塞尔曲线连接两个弧。
* [d3.svg.arc](SVG-Shapes#arc) - 新建一个弧度生成器。
* [d3.svg.area.radial](SVG-Shapes#area_radial) - 新建一个径向面积生成器。
* [d3.svg.area](SVG-Shapes#area) - 新建一个弧度生成器。
* [d3.svg.chord](SVG-Shapes#chord) - 新建一个弦生成器。
* [d3.svg.diagonal.radial](SVG-Shapes#diagonal_radial) - 新建一个径向对角线生成器。
* [d3.svg.diagonal](SVG-Shapes#diagonal) - 新建一个对角线生成器。
* [d3.svg.line.radial](SVG-Shapes#line_radial) - 新建一个径向线生成器。
* [d3.svg.line](SVG-Shapes#line) - 新建一个线生成器。
* [d3.svg.symbolTypes](SVG-Shapes#symbolTypes) - 一组符号类型。
* [d3.svg.symbol](SVG-Shapes#symbol) - 新建一个符号生成器。
* [diagonal.projection](SVG-Shapes#diagonal_projection) - 设置或获取一个可选的点转换。
* [diagonal.source](SVG-Shapes#diagonal_source) - 设置或获取源点访问器。
* [diagonal.target](SVG-Shapes#diagonal_target) - 设置或获取目标点访问器。
* [diagonal](SVG-Shapes#_diagonal) - 生成一个像节点链接图中的二维贝塞尔连接器。
* [diagonal](SVG-Shapes#_diagonal_radial) - 生成一个像节点链接图中的二维径向贝塞尔连接器。
* [line.angle](SVG-Shapes#line_radial_angle) - 设置或获取*角度* accessor.
* [line.defined](SVG-Shapes#line_defined) - 控制线在给定点是否是定义的。
* [line.defined](SVG-Shapes#line_radial_defined) - 控制径向线在给定点是否是定义的。
* [line.interpolate](SVG-Shapes#line_interpolate) - 设置或获取插值模式。
* [line.interpolate](SVG-Shapes#line_radial_interpolate) - 设置或获取径向弦的插值模式。
* [line.radius](SVG-Shapes#line_radial_radius) - 设置或获取*半径*访问器。
* [line.tension](SVG-Shapes#line_radial_tension) - 设置或获取径向基本样条线的张力。
* [line.tension](SVG-Shapes#line_tension) - 设置或获取基本样条线的张力。
* [line.x](SVG-Shapes#line_x) - 设置或获取*x*-坐标访问器。
* [line.y](SVG-Shapes#line_y) - 设置或获取*y*-坐标访问器。
* [line](SVG-Shapes#_line) - 生成一个像线图中的分段线段。
* [line](SVG-Shapes#_line_radial) - 生成一个像极线图中的分段线段。
* [symbol.size](SVG-Shapes#symbol_size) - 设置或获取符号尺寸（平方像素）访问器。
* [symbol.type](SVG-Shapes#symbol_type) - 设置或获取符号类型访问器。
* [symbol](SVG-Shapes#_symbol) - 生成一个像散点图中的符号。

### [轴](轴)

* [axis.innerTickSize](SVG-Axes#innerTickSize) - 指定内刻度大小。
* [axis.orient](SVG-Axes#orient) - 设置或者取得轴的方向。
* [axis.outerTickSize](SVG-Axes#outerTickSize) - 指定外刻度大小。
* [axis.scale](SVG-Axes#scale) - 设置或者取得比例尺。
* [axis.tickFormat](SVG-Axes#tickFormat) - 重载标签的刻度格式化。
* [axis.tickPadding](SVG-Axes#tickPadding) - 指定刻度和刻度标签之间的间距。
* [axis.tickSize](SVG-Axes#tickSize) - 指定主要的次要的和尾部的刻度。
* [axis.ticks](SVG-Axes#ticks) - 控制轴的刻度如何生成。
* [axis.tickValues](SVG-Axes#tickValues) - 明确地指定刻度值。
* [axis](SVG-Axes#_axis) - 为给定的选择器或过渡创建或者更新轴。
* [d3.svg.axis](SVG-Axes#axis) - 创建一个新的轴生成器。

### [拖选](拖选)

* [brush.clear](SVG-Controls#brush_clear) - 重置拖选范围。
* [brush.empty](SVG-Controls#brush_empty) - 拖选是否为空。
* [brush.event](SVG-Controls#brush_event) - 在设置范围之后分发拖选事件。
* [brush.extent](SVG-Controls#brush_extent) - 拖选范围可以是0,1，2维的。
* [brush.on](SVG-Controls#brush_on) - 监听拖选何时改变。
* [brush.x](SVG-Controls#brush_x) - 拖选的<i>x</i>-比例，用于水平拖选。
* [brush.y](SVG-Controls#brush_y) - 拖选的<i>y</i>-比例，用于垂直拖选。
* [brush](SVG-Controls#_brush) - 将拖选应用在指定的选择器和过渡上。
* [d3.svg.brush](SVG-Controls#brush) - 点击和拖曳来选择一个1维或2维区域。

## [d3.time (时间)](时间)

### [时间格式化](时间格式化)

* [d3.time.format.iso](Time-Formatting#format_iso) - ISO 8601 UTC时间格式化器。
* [d3.time.format.multi](Time-Formatting#format_multi) - 创建一个新的本地多功能时间格式化器。
* [d3.time.format.utc](Time-Formatting#format_utc) - 由指定的限定符创建一个新的UTC时间格式化器。
* [d3.time.format](Time-Formatting#format) - 由指定的限定符创建一个新的本地时间格式化器。
* [format.parse](Time-Formatting#parse) - 将字符串解析为时间对象。
* [format](Time-Formatting#_format) - 将一个时间对象格式化为一个字符串。

### [时间比例尺](时间比例尺)

* [d3.time.scale](Time-Scales#scale) - 构造一个线性时间比例尺。
* [scale.clamp](Time-Scales#clamp) - 指定输出范围是否闭合。
* [scale.copy](Time-Scales#copy) - 创建比例尺的副本。
* [scale.domain](Time-Scales#domain) - 取得或设置比例尺度的定义域。
* [scale.interpolate](Time-Scales#interpolate) - 取得或设置比例尺的输出插值器。
* [scale.invert](Time-Scales#invert) - 取得给定输出值对应定义域中的值。
* [scale.nice](Time-Scales#nice) - 扩展比例尺的定义域为一个优化的整数值。
* [scale.rangeRound](Time-Scales#rangeRound) - 设置比例尺的四舍五入输出范围。
* [scale.range](Time-Scales#range) - 取得或设置比例尺的输出范围。
* [scale.tickFormat](Time-Scales#tickFormat) - 取得用于展示刻度值的格式化器。
* [scale.ticks](Time-Scales#ticks) - 取得定义域中有代表性的值。
* [scale](Time-Scales#_scale) - 取得给定定义域中值对应的输出范围中的值。

### [时间间隔](时间间隔)

* [d3.time.dayOfYear](Time-Intervals#dayOfYear) - 计算天数。
* [d3.time.days](Time-Intervals#day) - day.range的别名。
* [d3.time.day](Time-Intervals#day) - 每天（12:00 AM）。
* [d3.time.fridayOfYear](Time-Intervals#fridayOfYear) - 计算基于周五的星期数。
* [d3.time.fridays](Time-Intervals#fridays) -friday.range的别名。
* [d3.time.friday](Time-Intervals#friday) - 每周五（例如February 5, 12:00 AM）。
* [d3.time.hours](Time-Intervals#hours) - hour.range的别名。
* [d3.time.hour](Time-Intervals#hour) - 每个小时（例如, 1:00 AM）。
* [d3.time.interval](Time-Intervals#interval) - 一个基于本地时间的时间间隔。
* [d3.time.minutes](Time-Intervals#minutes) - minute.range的别名。
* [d3.time.minute](Time-Intervals#minute) - 每分钟（例如, 1:02 AM）。
* [d3.time.mondayOfYear](Time-Intervals#mondayOfYear) - 计算基于周一的星期数。
* [d3.time.mondays](Time-Intervals#mondays) - monday.range的别名。
* [d3.time.monday](Time-Intervals#monday) - 每周一（例如, February 5, 12:00 AM）
* [d3.time.months](Time-Intervals#months) - month.range的别名。
* [d3.time.month](Time-Intervals#month) - 每个月（例如, February 1, 12:00 AM）
* [d3.time.saturdayOfYear](Time-Intervals#saturdayOfYear) - 计算基于周六的星期数。
* [d3.time.saturdays](Time-Intervals#saturdays) - saturday.range的别名。
* [d3.time.saturday](Time-Intervals#saturday) - every Saturday （例如, February 5, 12:00 AM）。
* [d3.time.seconds](Time-Intervals#seconds) - second.range的别名。
* [d3.time.second](Time-Intervals#second) - 每秒（例如, 1:02:03 AM）。
* [d3.time.sundayOfYear](Time-Intervals#sundayOfYear) - 计算基于周日的星期数。
* [d3.time.sundays](Time-Intervals#sundays) - sunday.range的别名。
* [d3.time.sunday](Time-Intervals#sunday) - 每周日（例如February 5, 12:00 AM）。
* [d3.time.thursdayOfYear](Time-Intervals#thursdayOfYear) - 计算基于周四的星期数。
* [d3.time.thursdays](Time-Intervals#thursdays) - thursday.range的别名。
* [d3.time.thursday](Time-Intervals#thursday) - 每周四（例如February 5, 12:00 AM）。
* [d3.time.tuesdayOfYear](Time-Intervals#tuesdayOfYear) - 计算基于周二的星期数。
* [d3.time.tuesdays](Time-Intervals#tuesdays) - tuesday.range的别名。
* [d3.time.tuesday](Time-Intervals#tuesday) - 每周二（例如February 5, 12:00 AM）。
* [d3.time.wednesdayOfYear](Time-Intervals#tuesdayOfYear) - 计算基于周三的星期数。
* [d3.time.wednesdays](Time-Intervals#wednesdays) - wednesday.range的别名。
* [d3.time.wednesday](Time-Intervals#wednesday) - 每周三（例如February 5, 12:00 AM）。
* [d3.time.weekOfYear](Time-Intervals#weekOfYear) - sundayOfYear的别名。
* [d3.time.weeks](Time-Intervals#weeks) - sunday.range的别名。
* [d3.time.week](Time-Intervals#week) - sunday的别名。
* [d3.time.years](Time-Intervals#years) - year.range的别名。
* [d3.time.year](Time-Intervals#year) - 每年（例如January 1, 12:00 AM）。
* [interval.ceil](Time-Intervals#interval_ceil) - 上取整到最近的时间间隔。
* [interval.floor](Time-Intervals#interval_floor) - 下取整到最近的时间间隔。
* [interval.offset](Time-Intervals#interval_offset) - 基于一些间隔返回时间偏移。
* [interval.range](Time-Intervals#interval_range) - 返回指定范围中的日期。
* [interval.round](Time-Intervals#interval_round) - 四舍五入到最近的时间间隔。
* [interval.utc](Time-Intervals#interval_utc) - 返回UTC时间间隔。
* [interval](Time-Intervals#_interval) - interval.floor的别名。

## [d3.layout (布局)](布局)

### [捆布局](捆布局)

* [bundle](Bundle-Layout#_bundle) - 对边使用Holten *层次捆绑* 算法。
* [d3.layout.bundle](Bundle-Layout#bundle) - 构造一个新的默认的捆绑布局。

### [弦布局](弦布局)

* [chord.chords](Chord-Layout#chords) - 取回计算的弦角度。
* [chord.groups](Chord-Layout#groups) - 取回计算的分组角度。
* [chord.matrix](Chord-Layout#matrix) - 取得或设置布局需要的矩阵数据。
* [chord.padding](Chord-Layout#padding) - 取得或设置弦片段间的角填充。
* [chord.sortChords](Chord-Layout#sortChords) - 取得或设置用于弦的比较器（Z轴顺序）。
* [chord.sortGroups](Chord-Layout#sortGroups) - 取得或设置用于分组的比较器。
* [chord.sortSubgroups](Chord-Layout#sortSubgroups) - 取得或设置用于子分组的比较器。
* [d3.layout.chord](Chord-Layout#chord) - 从关系矩阵生成一个弦图。

### [簇布局](簇布局)

* [cluster.children](Cluster-Layout#children) - 取得或者设置子节点的访问器函数。
* [cluster.links](Cluster-Layout#links) - 技术树节点之间的父子连接。
* [cluster.nodeSize](Cluster-Layout#nodeSize) - 为每个节点指定固定的尺寸。
* [cluster.nodes](Cluster-Layout#nodes) - 计算簇布局并返回节点数组。
* [cluster.separation](Cluster-Layout#separation) - 取得或设置邻接节点的分隔函数。
* [cluster.size](Cluster-Layout#size) - 取得或设置布局的尺寸。
* [cluster.sort](Cluster-Layout#sort) - 取得或设置兄弟节点的比较器函数。
* [cluster](Cluster-Layout#_cluster) - cluster.nodes的别名。
* [d3.layout.cluster](Cluster-Layout#cluster) - 将实体聚集成树状图。

### [力布局](力布局)

* [d3.layout.force](Force-Layout#force) - 使用物理模拟排放链接节点的位置。
* [force.alpha](Force-Layout#alpha) - 取得或者设置力布局的冷却参数。
* [force.chargeDistance](Force-Layout#chargeDistance) - 取得或者设置最大电荷距离。
* [force.charge](Force-Layout#charge) - 取得或者设置电荷强度。
* [force.drag](Force-Layout#drag) - 给节点绑定拖动行为。
* [force.friction](Force-Layout#friction) - 取得或者设置摩擦系数。
* [force.gravity](Force-Layout#gravity) - 取得或者设置重力强度。
* [force.linkDistance](Force-Layout#linkDistance) - 取得或者设置链接距离。
* [force.linkStrength](Force-Layout#linkStrength) - 取得或者设置链接强度。
* [force.links](Force-Layout#links) - 取得或者设置节点间的链接数组。
* [force.nodes](Force-Layout#nodes) - 取得或者设置布局的节点数组。
* [force.on](Force-Layout#on) - 监听在计算布局位置时的更新。
* [force.resume](Force-Layout#resume) - 重新加热冷却参数，并重启模拟。
* [force.size](Force-Layout#size) - 取得或者设置布局大小。
* [force.start](Force-Layout#start) - 当节点变化时启动或者重启模拟。
* [force.stop](Force-Layout#stop) - 立即停止模拟。
* [force.theta](Force-Layout#theta) - 取得或者设置电荷作用的精度。
* [force.tick](Force-Layout#tick) - 运行布局模拟的一步。

### [层次布局](层次布局)

* [d3.layout.hierarchy](Hierarchy-Layout#hierarchy) - 派生一个定制的层次布局实现。
* [hierarchy.children](Hierarchy-Layout#children) -取得或设置子节点的访问器。
* [hierarchy.links](Hierarchy-Layout#links) - 计算树节点中的父子链接。
* [hierarchy.nodes](Hierarchy-Layout#nodes) - 计算层次布局并返回节点数组。
* [hierarchy.revalue](Hierarchy-Layout#revalue) - 重新计算层次值。
* [hierarchy.sort](Hierarchy-Layout#sort) - 取得或设置兄弟节点的比较器函数。
* [hierarchy.value](Hierarchy-Layout#value) - 取得或设置值访问器函数。
* [hierarchy](Hierarchy-Layout#_hierarchy) - hierarchy.nodes的别名。

### [直方图布局](直方图布局)

* [d3.layout.histogram](Histogram-Layout#histogram) - 构造一个新的默认的直方图布局。
* [histogram.bins](Histogram-Layout#bins) - 指定值是如何组织到箱中的。
* [histogram.frequency](Histogram-Layout#frequency) - 按频数或者频率计算分布。
* [histogram.range](Histogram-Layout#range) - 取得或设置值得范围。
* [histogram.value](Histogram-Layout#value) - 取得或设置值访问器。
* [histogram](Histogram-Layout#_histogram) - 使用量化的箱计算数据的分布。

### [包布局](包布局)

* [d3.layout.pack](Pack-Layout#pack) - 用递归的圆-包生成一个层次布局。
* [pack.children](Pack-Layout#children) - 取得或设置子节点的访问器。
* [pack.links](Pack-Layout#links) - 计算树节点中的父子链接。
* [pack.nodes](Pack-Layout#nodes) - 计算包布局并返回节点数组。
* [pack.padding](Pack-Layout#padding) - 指定布局间距（以像素为单位）
* [pack.radius](Pack-Layout#radius) - 指定节点半径（不是由值派生来的）
* [pack.size](Pack-Layout#size) - 指定布局尺寸。
* [pack.sort](Pack-Layout#sort) - 控制兄弟节点的遍历顺序。
* [pack.value](Pack-Layout#value) -  取得或设置用于圆尺寸的值访问器。
* [pack](Pack-Layout#_pack) - pack.nodes的别名。

### [分区布局](分区布局)

* [d3.layout.partition](Partition-Layout#partition) - 递归地将节点树分区为旭日图或者冰柱图。
* [partition.children](Partition-Layout#children) - 取得或设置孩子访问器。
* [partition.links](Partition-Layout#links) - 计算树节点中的父子链接。
* [partition.nodes](Partition-Layout#nodes) - 计算分区布局并返回节点数组。
* [partition.size](Partition-Layout#size) - 指定布局的尺寸。
* [partition.sort](Partition-Layout#sort) - 控制兄弟节点的遍历顺序。
* [partition.value](Partition-Layout#value) - 取得或设置用来指定圆尺寸的值访问器。
* [partition](Partition-Layout#_partition) - partition.nodes的别名。

### [饼](饼)

* [d3.layout.pie](Pie-Layout#pie) - 构造一个新的默认的饼布局。
* [pie.endAngle](Pie-Layout#endAngle) -取得或设置饼布局整体的结束角度。
* [pie.padAngle](Pie-Layout#padAngle) - 取得或设置饼布局填充角度。
* [pie.sort](Pie-Layout#sort) - 控制饼片段的顺时针方向的顺序。
* [pie.startAngle](Pie-Layout#startAngle) - 取得或设置饼布局整体的开始角度。
* [pie.value](Pie-Layout#value) - 取得或设置值访问器函数。
* [pie](Pie-Layout#_pie) - 计算饼图或圆环图中弧的开始和结束角度。

### [堆叠](堆叠)

* [d3.layout.stack](Stack-Layout#stack) - 构造一个新的默认的堆叠布局。
* [stack.offset](Stack-Layout#offset) - 指定整体的基线算法。
* [stack.order](Stack-Layout#order) - 控制每个系列的顺序。
* [stack.out](Stack-Layout#out) - 取得或设置用于存储基线的输出函数。
* [stack.values](Stack-Layout#values) - 取得或设置每个系列的值访问器函数。
* [stack.x](Stack-Layout#x) - 取得或设置*x*-维访问器函数。
* [stack.y](Stack-Layout#y) - 取得或设置*y*-维访问器函数。
* [stack](Stack-Layout#_stack) - 计算堆叠图或者面积图的基线。

### [树](树)

* [d3.layout.tree](Tree-Layout#tree) - 整齐地排列树节点。
* [tree.children](Tree-Layout#children) - 取得或设置孩子访问器。
* [tree.links](Tree-Layout#links) - 计算树节点的父-子连接。
* [tree.nodeSize](Tree-Layout#nodeSize) - 为每个节点指定一个固定的尺寸。
* [tree.nodes](Tree-Layout#nodes) - 计算父布局并返回一组节点。
* [tree.separation](Tree-Layout#separation) - 取得或设置相邻节点的间隔函数。
* [tree.size](Tree-Layout#size) - 用*x*和*y*指定树的尺寸。
* [tree.sort](Tree-Layout#sort) - 控制遍历顺序中兄弟节点的顺序。
* [tree](Tree-Layout#_tree) - tree.nodes的别名。

### [矩形树](矩形树)

* [d3.layout.treemap](Treemap-Layout#treemap) - 使用空间递归分区算法展示树的节点。
* [treemap.children](Treemap-Layout#children) - 取得或设置孩子访问器。
* [treemap.links](Treemap-Layout#links) - 计算树节点中的父子链接。
* [treemap.mode](Treemap-Layout#mode) - 改变布局的算法。
* [treemap.nodes](Treemap-Layout#nodes) - 计算矩形树布局并返回节点数组。
* [treemap.padding](Treemap-Layout#padding) - 指定父子之间的间距。
* [treemap.round](Treemap-Layout#round) - 启用或者禁用四舍五入像素值。
* [treemap.size](Treemap-Layout#size) - 指定布局的尺寸。
* [treemap.sort](Treemap-Layout#sort) - 控制兄弟节点的遍历顺序。
* [treemap.sticky](Treemap-Layout#sticky) - 让布局对稳定的更新是粘滞的（sticky）。
* [treemap.value](Treemap-Layout#value) - 取得或设置用来指定矩形树中矩形单元尺寸的值访问器。
* [treemap](Treemap-Layout#_treemap) - treemap.nodes的别名。

## [d3.geo (地理)](地理)

### [地理路径](地理路径)

* [circle.angle](Geo-Paths#circle_angle) - 指定角半径（以度为单位）。
* [circle.origin](Geo-Paths#circle_origin) - 指定经纬度原点。
* [circle.precision](Geo-Paths#circle_precision) - 指定分段圆的精度。
* [circle](Geo-Paths#_circle) - 生成一个分段圆。
* [d3.geo.area](Geo-Paths#area) - 计算给定要素的球体面积。
* [d3.geo.bounds](Geo-Paths#bounds) - 计算给定要素的经纬度边界框。
* [d3.geo.centroid](Geo-Paths#centroid) - 计算给定要素的球体中心。
* [d3.geo.circle](Geo-Paths#circle) - 创建一个圆生成器。
* [d3.geo.distance](Geo-Paths#distance) - 计算两点之间的大弧距离。
* [d3.geo.graticule](Geo-Paths#graticule) - 创建一个经纬网生成器。
* [d3.geo.interpolate](Geo-Paths#interpolate) - 两个点之间插入一个大弧。
* [d3.geo.length](Geo-Paths#length) - 计算线的长度或多边形的面积。
* [d3.geo.path](Geo-Paths#path) - 创建一个地理路径生成器。
* [d3.geo.rotation](Geo-Paths#rotation) - 为指定的角度[λ, φ, γ]创建一个旋转角度。
* [graticule.extent](Geo-Paths#graticule_extent) - 取得或设置major & minor范围。
* [graticule.lines](Geo-Paths#graticule_lines) - 为经线和纬线生成线数组。
* [graticule.majorExtent](Geo-Paths#graticule_majorExtent) - 取得或设置major范围。
* [graticule.majorStep](Geo-Paths#graticule_majorStep) - 取得或设置major步长间隔。
* [graticule.minorExtent](Geo-Paths#graticule_minorExtent) - 取得或设置minor范围。
* [graticule.minorStep](Geo-Paths#graticule_minorStep) - 取得或设置minor步长间隔。
* [graticule.outline](Geo-Paths#graticule_outline) - 生成格子线范围的一个多边形。
* [graticule.precision](Geo-Paths#graticule_precision) - 取得或设置纬度精度。
* [graticule.step](Geo-Paths#graticule_step) - 取得或设置major & minor步长间隔。
* [graticule](Geo-Paths#_graticule) - 生成经纬线的多线要素。
* [path.area](Geo-Paths#path_area) - 计算给定要素的投影面积。
* [path.bounds](Geo-Paths#path_bounds) - 计算给定要素的投影边界。
* [path.centroid](Geo-Paths#path_centroid) - 计算给定要素的投影中心。
* [path.context](Geo-Paths#path_context) - 取得或设置渲染上下文。
* [path.pointRadius](Geo-Paths#path_pointRadius) - 取得或设置点要素的半径。
* [path.projection](Geo-Paths#path_projection) - 取得或设置地理投影。
* [path](Geo-Paths#_path) - 投影指定的要素并渲染上下文。
* [rotation.invert](Geo-Paths#rotation_invert) - 反旋转球体周围的给定位置。
* [rotation](Geo-Paths#_rotation) - 旋转球体周围的给定位置。

### [地理投影](地理投影)

* [albers.parallels](Geo-Projections#albers_parallels) - 取得或者设置投影的两条标准平行线。
* [d3.geo.albersUsa](Geo-Projections#albersUsa) - 用于展示美国地图的Albers复合投影。
* [d3.geo.albers](Geo-Projections#albers) - Albers等面积圆锥投影。
* [d3.geo.azimuthalEqualArea.raw](Geo-Projections#azimuthalEqualArea_raw) - 原始方位角等面积投影。
* [d3.geo.azimuthalEqualArea](Geo-Projections#azimuthalEqualArea) - 方位角等面积投影。
* [d3.geo.azimuthalEquidistant.raw](Geo-Projections#azimuthalEquidistant_raw) - 原始方位角等距投影。
* [d3.geo.azimuthalEquidistant](Geo-Projections#azimuthalEquidistant) - 方位角等距投影。
* [d3.geo.conicConformal.raw](Geo-Projections#conicConformal_raw) - 原始圆锥正形投影。
* [d3.geo.conicConformal](Geo-Projections#conicConformal) - 圆锥正形投影。
* [d3.geo.conicEqualArea.raw](Geo-Projections#conicEqualArea_raw) 原始圆锥等面积投影 (a.k.a. Albers)。
* [d3.geo.conicEqualArea](Geo-Projections#conicEqualArea) 圆锥等面积投影 (a.k.a. Albers)。
* [d3.geo.conicEquidistant.raw](Geo-Projections#conicEquidistant_raw) - 原始圆锥等距投影。
* [d3.geo.conicEquidistant](Geo-Projections#conicEquidistant) - 圆锥等距投影。
* [d3.geo.equirectangular.raw](Geo-Projections#equirectangular_raw) - 原始等角投影（普通圆柱投影）。
* [d3.geo.equirectangular](Geo-Projections#equirectangular) - 等角投影（普通圆柱投影）。
* [d3.geo.gnomonic.raw](Geo-Projections#gnomonic_raw) - 原始球心投影。
* [d3.geo.gnomonic](Geo-Projections#gnomonic) - 球心投影。
* [d3.geo.mercator.raw](Geo-Projections#mercator_raw) - 原始墨卡托投影。
* [d3.geo.mercator](Geo-Projections#mercator) - 球形墨卡托投影。
* [d3.geo.orthographic.raw](Geo-Projections#orthographic_raw) - 原始方位角直角投影。
* [d3.geo.orthographic](Geo-Projections#orthographic) - 方位角直角投影。
* [d3.geo.projectionMutator](Geo-Projections#projectionMutator) - 从可变的原始投影创建一个标准投影。
* [d3.geo.projection](Geo-Projections#projection) - 从原始投影创建一个标准投影。
* [d3.geo.stereographic.raw](Geo-Projections#stereographic_raw) - 原始方位角立体投影。
* [d3.geo.stereographic](Geo-Projections#stereographic) - 方位角立体投影。
* [d3.geo.transverseMercator.raw](Geo-Projections#transverseMercator_raw) - 原始横向墨卡托投影。
* [projection.center](Geo-Projections#center) - 取得或设置投影的中心位置。
* [projection.clipAngle](Geo-Projections#clipAngle) - get or set the radius of the projection’s clip circle.
* [projection.clipExtent](Geo-Projections#clipExtent) - 取得或设置投影的视口剪切范围（以像素为单位）。
* [projection.invert](Geo-Projections#invert) - 为指定的位置反转投影。
* [projection.precision](Geo-Projections#precision) - 取得或设置自适应重采样的精度阈值。
* [projection.rotate](Geo-Projections#rotate) - 取得或设置投影的三轴旋转角。
* [projection.scale](Geo-Projections#scale) - 取得或设置投影的缩放系数。
* [projection.stream](Geo-Projections#stream) - 包装指定的流监听器，投影输入的几何图形。
* [projection.translate](Geo-Projections#translate) - 取得或设置投影的平移位置。
* [projection](Geo-Projections#_projection) - 投影指定的位置。

### [流](流)

* [clipExtent.extent](Geo-Streams#clipExtent_extent) - 设置剪裁范围。
* [d3.geo.clipExtent](Geo-Streams#clipExtent) - 流转换剪切几何图形为给定的轴对齐矩形。
* [d3.geo.stream](Geo-Streams#stream) - 将GeoJSON对象转换为几何流。
* [d3.geo.transform](Geo-Streams#transform) - 转换流几何图形。
* [stream.lineEnd](Geo-Streams#stream_lineEnd) - 表示线或者环的终点。
* [stream.lineStart](Geo-Streams#stream_lineStart) - 表示线或者环的起点。
* [stream.point](Geo-Streams#stream_point) - 表面*x*, *y* (可选的 *z*) 坐标。
* [stream.polygonEnd](Geo-Streams#stream_polygonEnd) - 表明多边形的终点。
* [stream.polygonStart](Geo-Streams#stream_polygonStart) - 表明多边形的起点。
* [stream.sphere](Geo-Streams#stream_sphere) - 表明一个球体。
* [transform.stream](Geo-Streams#transform_stream) - 包装指定的流。

## [d3.geom (几何)](几何)

### [泰森多边形](泰森多边形)

* [d3.geom.voronoi](Voronoi-Geom#voronoi) - 用默认的访问器创建一个泰森多边形布局。
* [voronoi.clipExtent](Voronoi-Geom#clipExtent) -取得或者设置铺嵌的剪切范围。
* [voronoi.links](Voronoi-Geom#links) - 计算Delaunay mesh为一个链接网络。
* [voronoi.triangles](Voronoi-Geom#triangles) - 计算Delaunay mesh为一个三角形密铺。
* [voronoi.x](Voronoi-Geom#x) - 取得或者设置每个点的x-坐标访问器。
* [voronoi.y](Voronoi-Geom#y) - 取得或者设置每个点的y-坐标访问器。
* [voronoi](Voronoi-Geom#_voronoi) - 为每个指定的点计算泰森多边形密铺。

### [四叉树](四叉树)

* [d3.geom.quadtree](Quadtree-Geom#quadtree) - 为一个点数组创建一个四叉树。
* [quadtree.add](Quadtree-Geom#add) - 添加点到四叉树中。
* [quadtree.find](Quadtree-Geom#find) - 找到四叉树中最近的点。
* [quadtree.visit](Quadtree-Geom#visit) - 递归地遍历四叉树中的点。

### [多边形](多边形)

* [d3.geom.polygon](Polygon-Geom#polygon) - 由指定的点数组创建多边形。
* [polygon.area](Polygon-Geom#area) - 计算多边形逆时针方向的面积。
* [polygon.centroid](Polygon-Geom#centroid) - 计算多边形的面积中心。
* [polygon.clip](Polygon-Geom#clip) - 对这个多边形进行执行的多边形剪切。

### [赫尔](赫尔图)

* [d3.geom.hull](Hull-Geom#hull) - 使用默认访问器创建一个convex hull布局。
* [hull](Hull-Geom#_hull) - 为给定的点数组计算convex hull。
* [hull.x](Hull-Geom#x) - 取得或设置*x*-坐标访问器。
* [hull.y](Hull-Geom#y) - 取得或设置*y*-坐标访问器。

## [d3.behavior (行为)](行为)

### [拖动](拖动r)

* [d3.behavior.drag](Drag-Behavior#drag)
* [drag.on](Drag-Behavior#on)
* [drag.origin](Drag-Behavior#origin)

### [缩放](缩放)

* [d3.behavior.zoom](Zoom-Behavior#zoom) - 创建缩放行为。
* [zoom.center](Zoom-Behavior#center) - 鼠标滚轮缩放的焦点。
* [zoom.duration](Zoom-Behavior#duration) - 取得或设置双击事件的过渡持续的时间。
* [zoom.event](Zoom-Behavior#event) - 设置完缩放比例或平移之后分发缩放事件。
* [zoom.on](Zoom-Behavior#on) - 事件监听器。
* [zoom.scaleExtent](Zoom-Behavior#scaleExtent) - 可选参数，比例因子范围。
* [zoom.scale](Zoom-Behavior#scale) - 当前的比例因子。
* [zoom.size](Zoom-Behavior#size) - 视口的大小。
* [zoom.translate](Zoom-Behavior#translate) - 当前的平移偏移量。
* [zoom.x](Zoom-Behavior#x) - 可选比例尺，其定义域绑定到视口的_x_范围。
* [zoom.y](Zoom-Behavior#y) - 可选比例尺，其定义域绑定到视口的_y_范围。
* [zoom](Zoom-Behavior#_zoom) - 给指定的元素应用缩放行为。