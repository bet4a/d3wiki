> [Wiki](主页) ▸ **API 参考文档**

* 本文档是D3官方文档中文翻译，并保持与[最新版](https://github.com/mbostock/d3/wiki/API-Reference)同步。
* 如发现翻译不当或有其他问题可以通过以下方式联系译者:
* 邮箱：zhang_tianxu@sina.com
* QQ群：[D3数据可视化](http://jq.qq.com/?_wv=1027&k=ZGcqYF)

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

### [CSV Formatting (d3.csv)](CSV)

* [d3.csv.formatRows](CSV#formatRows) - format an array of tuples into a CSV string.
* [d3.csv.format](CSV#format) - format an array of objects into a CSV string.
* [d3.csv.parseRows](CSV#parseRows) - parse a CSV string into tuples, ignoring the header row.
* [d3.csv.parse](CSV#parse) - parse a CSV string into objects using the header row.
* [d3.csv](CSV#csv) - request a comma-separated values (CSV) file.
* [d3.dsv](CSV#dsv) - create a parser/formatter for the specified delimiter and mime type.
* [d3.tsv.formatRows](CSV#tsv_formatRows) - format an array of tuples into a TSV string.
* [d3.tsv.format](CSV#tsv_format) - format an array of objects into a TSV string.
* [d3.tsv.parseRows](CSV#tsv_parseRows) - parse a TSV string into tuples, ignoring the header row.
* [d3.tsv.parse](CSV#tsv_parse) - parse a TSV string into objects using the header row.
* [d3.tsv](CSV#tsv) - request a tab-separated values (TSV) file.

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

## [d3.scale (Scales)](Scales)

### [Quantitative](Quantitative-Scales#quantitative)

* [d3.scale.identity](Quantitative-Scales#identity) - construct a linear identity scale.
* [d3.scale.linear](Quantitative-Scales#linear) - construct a linear quantitative scale.
* [d3.scale.log](Quantitative-Scales#log) - construct a quantitative scale with an logarithmic transform.
* [d3.scale.pow](Quantitative-Scales#pow) - construct a quantitative scale with an exponential transform.
* [d3.scale.quantile](Quantitative-Scales#quantile) - construct a quantitative scale mapping to quantiles.
* [d3.scale.quantize](Quantitative-Scales#quantize) - construct a linear quantitative scale with a discrete output range.
* [d3.scale.sqrt](Quantitative-Scales#sqrt) - construct a quantitative scale with a square root transform.
* [d3.scale.threshold](Quantitative-Scales#threshold) - construct a threshold scale with a discrete output range.
* [identity.copy](Quantitative-Scales#identity_copy) - create a new scale from an existing scale.
* [identity.domain](Quantitative-Scales#identity_domain) - get or set the scale's domain and range.
* [identity.invert](Quantitative-Scales#_identity) - equivalent to identity; the identity function.
* [identity.range](Quantitative-Scales#identity_domain) - equivalent to identity.domain.
* [identity.tickFormat](Quantitative-Scales#identity_tickFormat) - get a formatter for displaying tick values.
* [identity.ticks](Quantitative-Scales#identity_ticks) - get representative values from the domain.
* [identity](Quantitative-Scales#_identity) - the identity function.
* [linear.clamp](Quantitative-Scales#linear_clamp) - enable or disable clamping of the output range.
* [linear.copy](Quantitative-Scales#linear_copy) - create a new scale from an existing scale.
* [linear.domain](Quantitative-Scales#linear_domain) - get or set the scale's input domain.
* [linear.interpolate](Quantitative-Scales#linear_interpolate) - get or set the scale's output interpolator.
* [linear.invert](Quantitative-Scales#linear_invert) - get the domain value corresponding to a given range value.
* [linear.nice](Quantitative-Scales#linear_nice) - extend the scale domain to nice round numbers.
* [linear.rangeRound](Quantitative-Scales#linear_rangeRound) - set the scale's output range, and enable rounding.
* [linear.range](Quantitative-Scales#linear_range) - get or set the scale's output range.
* [linear.tickFormat](Quantitative-Scales#linear_tickFormat) - get a formatter for displaying tick values.
* [linear.ticks](Quantitative-Scales#linear_ticks) - get representative values from the input domain.
* [linear](Quantitative-Scales#_linear) - get the range value corresponding to a given domain value.
* [log.clamp](Quantitative-Scales#log_clamp) - enable or disable clamping of the output range.
* [log.copy](Quantitative-Scales#log_copy) - create a new scale from an existing scale.
* [log.domain](Quantitative-Scales#log_domain) - get or set the scale's input domain.
* [log.interpolate](Quantitative-Scales#log_interpolate) - get or set the scale's output interpolator.
* [log.invert](Quantitative-Scales#log_invert) - get the domain value corresponding to a given range value.
* [log.nice](Quantitative-Scales#log_nice) - extend the scale domain to nice powers of ten.
* [log.rangeRound](Quantitative-Scales#log_rangeRound) - set the scale's output range, and enable rounding.
* [log.range](Quantitative-Scales#log_range) - get or set the scale's output range.
* [log.tickFormat](Quantitative-Scales#log_tickFormat) - get a formatter for displaying tick values.
* [log.ticks](Quantitative-Scales#log_ticks) - get representative values from the input domain.
* [log](Quantitative-Scales#_log) - get the range value corresponding to a given domain value.
* [pow.clamp](Quantitative-Scales#pow_clamp) - enable or disable clamping of the output range.
* [pow.copy](Quantitative-Scales#pow_copy) - create a new scale from an existing scale.
* [pow.domain](Quantitative-Scales#pow_domain) - get or set the scale's input domain.
* [pow.exponent](Quantitative-Scales#pow_exponent) - get or set the exponent power.
* [pow.interpolate](Quantitative-Scales#pow_interpolate) - get or set the scale's output interpolator.
* [pow.invert](Quantitative-Scales#pow_invert) - get the domain value corresponding to a given range value.
* [pow.nice](Quantitative-Scales#pow_nice) - extend the scale domain to nice round numbers.
* [pow.rangeRound](Quantitative-Scales#pow_rangeRound) - set the scale's output range, and enable rounding.
* [pow.range](Quantitative-Scales#pow_range) - get or set the scale's output range.
* [pow.tickFormat](Quantitative-Scales#pow_tickFormat) - get a formatter for displaying tick values.
* [pow.ticks](Quantitative-Scales#pow_ticks) - get representative values from the input domain.
* [pow](Quantitative-Scales#_pow) - get the range value corresponding to a given domain value.
* [quantile.copy](Quantitative-Scales#quantile_copy) - create a new scale from an existing scale.
* [quantile.domain](Quantitative-Scales#quantile_domain) - get or set the scale's input domain (as discrete values).
* [quantile.invertExtent](Quantitative-Scales#quantile_invertExtent) - get the domain values for the specified range value.
* [quantile.quantiles](Quantitative-Scales#quantile_quantiles) - get the scale's quantile bin thresholds.
* [quantile.range](Quantitative-Scales#quantile_range) - get or set the scale's output range (as discrete values).
* [quantile](Quantitative-Scales#_quantile) - get the range value corresponding to a given domain value.
* [quantize.copy](Quantitative-Scales#quantize_copy) - create a new scale from an existing scale.
* [quantize.domain](Quantitative-Scales#quantize_domain) - get or set the scale's input domain.
* [quantize.invertExtent](Quantitative-Scales#quantize_invertExtent) - get the domain values for the specified range value.
* [quantize.range](Quantitative-Scales#quantize_range) - get or set the scale's output range (as discrete values).
* [quantize](Quantitative-Scales#_quantize) - get the range value corresponding to a given domain value.
* [threshold.copy](Quantitative-Scales#threshold_copy) - create a new scale from an existing scale.
* [threshold.domain](Quantitative-Scales#threshold_domain) - get or set the scale's input domain.
* [threshold.invertExtent](Quantitative-Scales#threshold_invertExtent) - get the domain values for the specified range value.
* [threshold.range](Quantitative-Scales#threshold_range) - get or set the scale's output range (as discrete values).
* [threshold](Quantitative-Scales#_threshold) - get the range value corresponding to a given domain value.

### [Ordinal](Ordinal-Scales#ordinal)

* [d3.scale.category10](Ordinal-Scales#category10) - construct an ordinal scale with ten categorical colors.
* [d3.scale.category20b](Ordinal-Scales#category20b) - construct an ordinal scale with twenty categorical colors.
* [d3.scale.category20c](Ordinal-Scales#category20c) - construct an ordinal scale with twenty categorical colors.
* [d3.scale.category20](Ordinal-Scales#category20) - construct an ordinal scale with twenty categorical colors.
* [d3.scale.ordinal](Ordinal-Scales#ordinal) - construct an ordinal scale.
* [ordinal.copy](Ordinal-Scales#ordinal_copy) - create a new scale from an existing scale.
* [ordinal.domain](Ordinal-Scales#ordinal_domain) - get or set the scale's input domain.
* [ordinal.rangeBands](Ordinal-Scales#ordinal_rangeBands) - divide a continuous output range for discrete bands.
* [ordinal.rangeBand](Ordinal-Scales#ordinal_rangeBand) - get the discrete range band width.
* [ordinal.rangeExtent](Ordinal-Scales#ordinal_rangeExtent) - get the minimum and maximum values of the output range.
* [ordinal.rangePoints](Ordinal-Scales#ordinal_rangePoints) - divide a continuous output range for discrete points.
* [ordinal.rangeRoundBands](Ordinal-Scales#ordinal_rangeRoundBands) - divide a continuous output range for discrete bands.
* [ordinal.rangeRoundPoints](Ordinal-Scales#ordinal_rangeRoundPoints) - divide a continuous output range for discrete points.
* [ordinal.range](Ordinal-Scales#ordinal_range) - get or set the scale's output range.
* [ordinal](Ordinal-Scales#_ordinal) - get the range value corresponding to a given domain value.

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
* [d3.svg.arc](SVG-Shapes#arc) - create a new arc generator.
* [d3.svg.area.radial](SVG-Shapes#area_radial) - create a new area generator.
* [d3.svg.area](SVG-Shapes#area) - create a new area generator.
* [d3.svg.chord](SVG-Shapes#chord) - create a new chord generator.
* [d3.svg.diagonal.radial](SVG-Shapes#diagonal_radial) - create a new diagonal generator.
* [d3.svg.diagonal](SVG-Shapes#diagonal) - create a new diagonal generator.
* [d3.svg.line.radial](SVG-Shapes#line_radial) - create a new radial line generator.
* [d3.svg.line](SVG-Shapes#line) - create a new line generator.
* [d3.svg.symbolTypes](SVG-Shapes#symbolTypes) - the array of supported symbol types.
* [d3.svg.symbol](SVG-Shapes#symbol) - create a new symbol generator.
* [diagonal.projection](SVG-Shapes#diagonal_projection) - get or set an optional point transform.
* [diagonal.source](SVG-Shapes#diagonal_source) - get or set the source point accessor.
* [diagonal.target](SVG-Shapes#diagonal_target) - get or set the target point accessor.
* [diagonal](SVG-Shapes#_diagonal) - generate a two-dimensional Bézier connector, as in a node-link diagram.
* [diagonal](SVG-Shapes#_diagonal_radial) - generate a two-dimensional Bézier connector, as in a node-link diagram.
* [line.angle](SVG-Shapes#line_radial_angle) - get or set the *angle* accessor.
* [line.defined](SVG-Shapes#line_defined) - control whether the line is defined at a given point.
* [line.defined](SVG-Shapes#line_radial_defined) - control whether the line is defined at a given point.
* [line.interpolate](SVG-Shapes#line_interpolate) - get or set the interpolation mode.
* [line.interpolate](SVG-Shapes#line_radial_interpolate) - get or set the interpolation mode.
* [line.radius](SVG-Shapes#line_radial_radius) - get or set the *radius* accessor.
* [line.tension](SVG-Shapes#line_radial_tension) - get or set the cardinal spline tension.
* [line.tension](SVG-Shapes#line_tension) - get or set the cardinal spline tension.
* [line.x](SVG-Shapes#line_x) - get or set the *x*-coordinate accessor.
* [line.y](SVG-Shapes#line_y) - get or set the *y*-coordinate accessor.
* [line](SVG-Shapes#_line) - generate a piecewise linear curve, as in a line chart.
* [line](SVG-Shapes#_line_radial) - generate a piecewise linear curve, as in a polar line chart.
* [symbol.size](SVG-Shapes#symbol_size) - get or set the symbol size (in square pixels) accessor.
* [symbol.type](SVG-Shapes#symbol_type) - get or set the symbol type accessor.
* [symbol](SVG-Shapes#_symbol) - generate categorical symbols, as in a scatterplot.

### [Axes](SVG-Axes)

* [axis.innerTickSize](SVG-Axes#innerTickSize) - specify the size of inner ticks.
* [axis.orient](SVG-Axes#orient) - get or set the axis orientation.
* [axis.outerTickSize](SVG-Axes#outerTickSize) - specify the size of outer ticks.
* [axis.scale](SVG-Axes#scale) - get or set the axis scale.
* [axis.tickFormat](SVG-Axes#tickFormat) - override the tick formatting for labels.
* [axis.tickPadding](SVG-Axes#tickPadding) - specify padding between ticks and tick labels.
* [axis.tickSize](SVG-Axes#tickSize) - specify the size of major, minor and end ticks.
* [axis.ticks](SVG-Axes#ticks) - control how ticks are generated for the axis.
* [axis.tickValues](SVG-Axes#tickValues) - specify tick values explicitly.
* [axis](SVG-Axes#_axis) - creates or updates an axis for the given selection or transition.
* [d3.svg.axis](SVG-Axes#axis) - create a new axis generator.

### [Controls](SVG-Controls)

* [brush.clear](SVG-Controls#brush_clear) - reset the brush extent.
* [brush.empty](SVG-Controls#brush_empty) - whether or not the brush extent is empty.
* [brush.event](SVG-Controls#brush_event) - dispatch brush events after setting the extent.
* [brush.extent](SVG-Controls#brush_extent) - the brush’s extent in zero, one or two dimensions.
* [brush.on](SVG-Controls#brush_on) - listeners for when the brush is moved.
* [brush.x](SVG-Controls#brush_x) - the brush’s <i>x</i>-scale, for horizontal brushing.
* [brush.y](SVG-Controls#brush_y) - the brush’s <i>y</i>-scale, for vertical brushing.
* [brush](SVG-Controls#_brush) - apply a brush to the given selection or transition.
* [d3.svg.brush](SVG-Controls#brush) - click and drag to select one- or two-dimensional regions.

## [d3.time (Time)](Time)

### [Time Formatting](Time-Formatting)

* [d3.time.format.iso](Time-Formatting#format_iso) - the ISO 8601 UTC time formatter.
* [d3.time.format.multi](Time-Formatting#format_multi) - create a new local multi-resolution time formatter.
* [d3.time.format.utc](Time-Formatting#format_utc) - create a new UTC time formatter for a given specifier.
* [d3.time.format](Time-Formatting#format) - create a new local time formatter for a given specifier.
* [format.parse](Time-Formatting#parse) - parse a string into a date.
* [format](Time-Formatting#_format) - format a date into a string.

### [Time Scales](Time-Scales)

* [d3.time.scale](Time-Scales#scale) - construct a linear time scale.
* [scale.clamp](Time-Scales#clamp) - enable or disable clamping of the output range.
* [scale.copy](Time-Scales#copy) - create a new scale from an existing scale.
* [scale.domain](Time-Scales#domain) - get or set the scale's input domain.
* [scale.interpolate](Time-Scales#interpolate) - get or set the scale's output interpolator.
* [scale.invert](Time-Scales#invert) - get the domain value corresponding to a given range value.
* [scale.nice](Time-Scales#nice) - extend the scale domain to nice round numbers.
* [scale.rangeRound](Time-Scales#rangeRound) - set the scale's output range, and enable rounding.
* [scale.range](Time-Scales#range) - get or set the scale's output range.
* [scale.tickFormat](Time-Scales#tickFormat) - get a formatter for displaying tick values.
* [scale.ticks](Time-Scales#ticks) - get representative values from the input domain.
* [scale](Time-Scales#_scale) - get the range value corresponding to a given domain value.

### [Time Intervals](Time-Intervals)

* [d3.time.dayOfYear](Time-Intervals#dayOfYear) - computes the day number.
* [d3.time.days](Time-Intervals#day) - alias for day.range.
* [d3.time.day](Time-Intervals#day) - every day (12:00 AM).
* [d3.time.fridayOfYear](Time-Intervals#fridayOfYear) - computes the friday-based week number.
* [d3.time.fridays](Time-Intervals#fridays) - alias for friday.range.
* [d3.time.friday](Time-Intervals#friday) - every Friday (e.g., February 5, 12:00 AM).
* [d3.time.hours](Time-Intervals#hours) - alias for hour.range.
* [d3.time.hour](Time-Intervals#hour) - every hour (e.g., 1:00 AM).
* [d3.time.interval](Time-Intervals#interval) - a time interval in local time.
* [d3.time.minutes](Time-Intervals#minutes) - alias for minute.range.
* [d3.time.minute](Time-Intervals#minute) - every minute (e.g., 1:02 AM).
* [d3.time.mondayOfYear](Time-Intervals#mondayOfYear) - computes the monday-based week number.
* [d3.time.mondays](Time-Intervals#mondays) - alias for monday.range.
* [d3.time.monday](Time-Intervals#monday) - every Monday (e.g., February 5, 12:00 AM).
* [d3.time.months](Time-Intervals#months) - alias for month.range.
* [d3.time.month](Time-Intervals#month) - every month (e.g., February 1, 12:00 AM).
* [d3.time.saturdayOfYear](Time-Intervals#saturdayOfYear) - computes the saturday-based week number.
* [d3.time.saturdays](Time-Intervals#saturdays) - alias for saturday.range.
* [d3.time.saturday](Time-Intervals#saturday) - every Saturday (e.g., February 5, 12:00 AM).
* [d3.time.seconds](Time-Intervals#seconds) - alias for second.range.
* [d3.time.second](Time-Intervals#second) - every second (e.g., 1:02:03 AM).
* [d3.time.sundayOfYear](Time-Intervals#sundayOfYear) - computes the sunday-based week number.
* [d3.time.sundays](Time-Intervals#sundays) - alias for sunday.range.
* [d3.time.sunday](Time-Intervals#sunday) - every Sunday (e.g., February 5, 12:00 AM).
* [d3.time.thursdayOfYear](Time-Intervals#thursdayOfYear) - computes the thursday-based week number.
* [d3.time.thursdays](Time-Intervals#thursdays) - alias for thursday.range.
* [d3.time.thursday](Time-Intervals#thursday) - every Thursday (e.g., February 5, 12:00 AM).
* [d3.time.tuesdayOfYear](Time-Intervals#tuesdayOfYear) - computes the tuesday-based week number.
* [d3.time.tuesdays](Time-Intervals#tuesdays) - alias for tuesday.range.
* [d3.time.tuesday](Time-Intervals#tuesday) - every Tuesday (e.g., February 5, 12:00 AM).
* [d3.time.wednesdayOfYear](Time-Intervals#tuesdayOfYear) - computes the wednesday-based week number.
* [d3.time.wednesdays](Time-Intervals#wednesdays) - alias for wednesday.range.
* [d3.time.wednesday](Time-Intervals#wednesday) - every Wednesday (e.g., February 5, 12:00 AM).
* [d3.time.weekOfYear](Time-Intervals#weekOfYear) - alias for sundayOfYear.
* [d3.time.weeks](Time-Intervals#weeks) - alias for sunday.range.
* [d3.time.week](Time-Intervals#week) - alias for sunday.
* [d3.time.years](Time-Intervals#years) - alias for year.range.
* [d3.time.year](Time-Intervals#year) - every year (e.g., January 1, 12:00 AM).
* [interval.ceil](Time-Intervals#interval_ceil) - rounds up to the nearest interval.
* [interval.floor](Time-Intervals#interval_floor) - rounds down to the nearest interval.
* [interval.offset](Time-Intervals#interval_offset) - returns a date offset by some interval.
* [interval.range](Time-Intervals#interval_range) - returns dates within the specified range.
* [interval.round](Time-Intervals#interval_round) - rounds up or down to the nearest interval.
* [interval.utc](Time-Intervals#interval_utc) - returns the UTC-equivalent time interval.
* [interval](Time-Intervals#_interval) - alias for interval.floor.

## [d3.layout (Layouts)](Layouts)

### [Bundle](Bundle-Layout)

* [bundle](Bundle-Layout#_bundle) - apply Holten's *hierarchical bundling* algorithm to edges.
* [d3.layout.bundle](Bundle-Layout#bundle) - construct a new default bundle layout.

### [Chord](Chord-Layout)

* [chord.chords](Chord-Layout#chords) - retrieve the computed chord angles.
* [chord.groups](Chord-Layout#groups) - retrieve the computed group angles.
* [chord.matrix](Chord-Layout#matrix) - get or set the matrix data backing the layout.
* [chord.padding](Chord-Layout#padding) - get or set the angular padding between chord segments.
* [chord.sortChords](Chord-Layout#sortChords) - get or set the comparator function for chords (z-order).
* [chord.sortGroups](Chord-Layout#sortGroups) - get or set the comparator function for groups.
* [chord.sortSubgroups](Chord-Layout#sortSubgroups) - get or set the comparator function for subgroups.
* [d3.layout.chord](Chord-Layout#chord) - produce a chord diagram from a matrix of relationships.

### [Cluster](Cluster-Layout)

* [cluster.children](Cluster-Layout#children) - get or set the accessor function for child nodes.
* [cluster.links](Cluster-Layout#links) - compute the parent-child links between tree nodes.
* [cluster.nodeSize](Cluster-Layout#nodeSize) - specify a fixed size for each node.
* [cluster.nodes](Cluster-Layout#nodes) - compute the cluster layout and return the array of nodes.
* [cluster.separation](Cluster-Layout#separation) - get or set the spacing function between neighboring nodes.
* [cluster.size](Cluster-Layout#size) - get or set the layout size in *x* and *y*.
* [cluster.sort](Cluster-Layout#sort) - get or set the comparator function for sibling nodes.
* [cluster](Cluster-Layout#_cluster) - alias for cluster.nodes.
* [d3.layout.cluster](Cluster-Layout#cluster) - cluster entities into a dendrogram.

### [Force](Force-Layout)

* [d3.layout.force](Force-Layout#force) - position linked nodes using physical simulation.
* [force.alpha](Force-Layout#alpha) - get or set the layout's cooling parameter.
* [force.chargeDistance](Force-Layout#chargeDistance) - get or set the maximum charge distance.
* [force.charge](Force-Layout#charge) - get or set the charge strength.
* [force.drag](Force-Layout#drag) - bind a behavior to nodes to allow interactive dragging.
* [force.friction](Force-Layout#friction) - get or set the friction coefficient.
* [force.gravity](Force-Layout#gravity) - get or set the gravity strength.
* [force.linkDistance](Force-Layout#linkDistance) - get or set the link distance.
* [force.linkStrength](Force-Layout#linkStrength) - get or set the link strength.
* [force.links](Force-Layout#links) - get or set the array of links between nodes.
* [force.nodes](Force-Layout#nodes) - get or set the array of nodes to layout.
* [force.on](Force-Layout#on) - listen to updates in the computed layout positions.
* [force.resume](Force-Layout#resume) - reheat the cooling parameter and restart simulation.
* [force.size](Force-Layout#size) - get or set the layout size in *x* and *y*.
* [force.start](Force-Layout#start) - start or restart the simulation when the nodes change.
* [force.stop](Force-Layout#stop) - immediately terminate the simulation.
* [force.theta](Force-Layout#theta) - get or set the accuracy of the charge interaction.
* [force.tick](Force-Layout#tick) - run the layout simulation one step.

### [Hierarchy](Hierarchy-Layout)

* [d3.layout.hierarchy](Hierarchy-Layout#hierarchy) - derive a custom hierarchical layout implementation.
* [hierarchy.children](Hierarchy-Layout#children) - get or set the accessor function for child nodes.
* [hierarchy.links](Hierarchy-Layout#links) - compute the parent-child links between tree nodes.
* [hierarchy.nodes](Hierarchy-Layout#nodes) - compute the layout and return the array of nodes.
* [hierarchy.revalue](Hierarchy-Layout#revalue) - recompute the hierarchy values.
* [hierarchy.sort](Hierarchy-Layout#sort) - get or set the comparator function for sibling nodes.
* [hierarchy.value](Hierarchy-Layout#value) - get or set the value accessor function.
* [hierarchy](Hierarchy-Layout#_hierarchy) - alias for hierarchy.nodes.

### [Histogram](Histogram-Layout)

* [d3.layout.histogram](Histogram-Layout#histogram) - construct a new default histogram layout.
* [histogram.bins](Histogram-Layout#bins) - specify how values are organized into bins.
* [histogram.frequency](Histogram-Layout#frequency) - compute the distribution as counts or probabilities.
* [histogram.range](Histogram-Layout#range) - get or set the considered value range.
* [histogram.value](Histogram-Layout#value) - get or set the value accessor function.
* [histogram](Histogram-Layout#_histogram) - compute the distribution of data using quantized bins.

### [Pack](Pack-Layout)

* [d3.layout.pack](Pack-Layout#pack) - produce a hierarchical layout using recursive circle-packing.
* [pack.children](Pack-Layout#children) - get or set the children accessor function.
* [pack.links](Pack-Layout#links) - compute the parent-child links between tree nodes.
* [pack.nodes](Pack-Layout#nodes) - compute the pack layout and return the array of nodes.
* [pack.padding](Pack-Layout#padding) - specify the layout padding in (approximate) pixels.
* [pack.radius](Pack-Layout#radius) - specify the node radius, rather than deriving it from value.
* [pack.size](Pack-Layout#size) - specify the layout size in *x* and *y*.
* [pack.sort](Pack-Layout#sort) - control the order in which sibling nodes are traversed.
* [pack.value](Pack-Layout#value) - get or set the value accessor used to size circles.
* [pack](Pack-Layout#_pack) - alias for pack.nodes.

### [Partition](Partition-Layout)

* [d3.layout.partition](Partition-Layout#partition) - recursively partition a node tree into a sunburst or icicle.
* [partition.children](Partition-Layout#children) - get or set the children accessor function.
* [partition.links](Partition-Layout#links) - compute the parent-child links between tree nodes.
* [partition.nodes](Partition-Layout#nodes) - compute the partition layout and return the array of nodes.
* [partition.size](Partition-Layout#size) - specify the layout size in *x* and *y*.
* [partition.sort](Partition-Layout#sort) - control the order in which sibling nodes are traversed.
* [partition.value](Partition-Layout#value) - get or set the value accessor used to size circles.
* [partition](Partition-Layout#_partition) - alias for partition.nodes.

### [Pie](Pie-Layout)

* [d3.layout.pie](Pie-Layout#pie) - construct a new default pie layout.
* [pie.endAngle](Pie-Layout#endAngle) - get or set the overall end angle of the pie.
* [pie.padAngle](Pie-Layout#padAngle) - get or set the pad angle of the pie.
* [pie.sort](Pie-Layout#sort) - control the clockwise order of pie slices.
* [pie.startAngle](Pie-Layout#startAngle) - get or set the overall start angle of the pie.
* [pie.value](Pie-Layout#value) - get or set the value accessor function.
* [pie](Pie-Layout#_pie) - compute the start and end angles for arcs in a pie or donut chart.

### [Stack](Stack-Layout)

* [d3.layout.stack](Stack-Layout#stack) - construct a new default stack layout.
* [stack.offset](Stack-Layout#offset) - specify the overall baseline algorithm.
* [stack.order](Stack-Layout#order) - control the order in which series are stacked.
* [stack.out](Stack-Layout#out) - get or set the output function for storing the baseline.
* [stack.values](Stack-Layout#values) - get or set the values accessor function per series.
* [stack.x](Stack-Layout#x) - get or set the *x*-dimension accessor function.
* [stack.y](Stack-Layout#y) - get or set the *y*-dimension accessor function.
* [stack](Stack-Layout#_stack) - compute the baseline for each series in a stacked bar or area chart.

### [Tree](Tree-Layout)

* [d3.layout.tree](Tree-Layout#tree) - position a tree of nodes tidily.
* [tree.children](Tree-Layout#children) - get or set the children accessor function.
* [tree.links](Tree-Layout#links) - compute the parent-child links between tree nodes.
* [tree.nodeSize](Tree-Layout#nodeSize) - specify a fixed size for each node.
* [tree.nodes](Tree-Layout#nodes) - compute the tree layout and return the array of nodes.
* [tree.separation](Tree-Layout#separation) - get or set the spacing function between neighboring nodes.
* [tree.size](Tree-Layout#size) - specify the layout size in *x* and *y*.
* [tree.sort](Tree-Layout#sort) - control the order in which sibling nodes are traversed.
* [tree](Tree-Layout#_tree) - alias for tree.nodes.

### [Treemap](Treemap-Layout)

* [d3.layout.treemap](Treemap-Layout#treemap) - use recursive spatial subdivision to display a tree of nodes.
* [treemap.children](Treemap-Layout#children) - get or set the children accessor function.
* [treemap.links](Treemap-Layout#links) - compute the parent-child links between tree nodes.
* [treemap.mode](Treemap-Layout#mode) - change the treemap layout algorithm.
* [treemap.nodes](Treemap-Layout#nodes) - compute the treemap layout and return the array of nodes.
* [treemap.padding](Treemap-Layout#padding) - specify the padding between a parent and its children.
* [treemap.round](Treemap-Layout#round) - enable or disable rounding to exact pixels.
* [treemap.size](Treemap-Layout#size) - specify the layout size in *x* and *y*.
* [treemap.sort](Treemap-Layout#sort) - control the order in which sibling nodes are traversed.
* [treemap.sticky](Treemap-Layout#sticky) - make the layout sticky for stable updates.
* [treemap.value](Treemap-Layout#value) - get or set the value accessor used to size treemap cells.
* [treemap](Treemap-Layout#_treemap) - alias for treemap.nodes.

## [d3.geo (Geography)](Geo)

### [Paths](Geo-Paths)

* [circle.angle](Geo-Paths#circle_angle) - specify the angular radius in degrees.
* [circle.origin](Geo-Paths#circle_origin) - specify the origin in latitude and longitude.
* [circle.precision](Geo-Paths#circle_precision) - specify the precision of the piecewise circle.
* [circle](Geo-Paths#_circle) - generate a piecewise circle as a Polygon.
* [d3.geo.area](Geo-Paths#area) - compute the spherical area of a given feature.
* [d3.geo.bounds](Geo-Paths#bounds) - compute the latitude-longitude bounding box for a given feature.
* [d3.geo.centroid](Geo-Paths#centroid) - compute the spherical centroid of a given feature.
* [d3.geo.circle](Geo-Paths#circle) - create a circle generator.
* [d3.geo.distance](Geo-Paths#distance) - compute the great-arc distance between two points.
* [d3.geo.graticule](Geo-Paths#graticule) - create a graticule generator.
* [d3.geo.interpolate](Geo-Paths#interpolate) - interpolate between two points along a great arc.
* [d3.geo.length](Geo-Paths#length) - compute the length of a line string or the perimeter of a polygon.
* [d3.geo.path](Geo-Paths#path) - create a new geographic path generator.
* [d3.geo.rotation](Geo-Paths#rotation) - create a rotation function for the specified angles [λ, φ, γ].
* [graticule.extent](Geo-Paths#graticule_extent) - get or set the major & minor extents.
* [graticule.lines](Geo-Paths#graticule_lines) - generate an array of LineStrings of meridians and parallels.
* [graticule.majorExtent](Geo-Paths#graticule_majorExtent) - get or set the major extent.
* [graticule.majorStep](Geo-Paths#graticule_majorStep) - get or set the major step intervals.
* [graticule.minorExtent](Geo-Paths#graticule_minorExtent) - get or set the minor extent.
* [graticule.minorStep](Geo-Paths#graticule_minorStep) - get or set the minor step intervals.
* [graticule.outline](Geo-Paths#graticule_outline) - generate a Polygon of the graticule’s extent.
* [graticule.precision](Geo-Paths#graticule_precision) - get or set the latitudinal precision.
* [graticule.step](Geo-Paths#graticule_step) - get or set the major & minor step intervals.
* [graticule](Geo-Paths#_graticule) - generate a MultiLineString of meridians and parallels.
* [path.area](Geo-Paths#path_area) - compute the projected area of a given feature.
* [path.bounds](Geo-Paths#path_bounds) - compute the projected bounds of a given feature.
* [path.centroid](Geo-Paths#path_centroid) - compute the projected centroid of a given feature.
* [path.context](Geo-Paths#path_context) - get or set the render context.
* [path.pointRadius](Geo-Paths#path_pointRadius) - get or set the radius to display point features.
* [path.projection](Geo-Paths#path_projection) - get or set the geographic projection.
* [path](Geo-Paths#_path) - project the specified feature and render it to the context.
* [rotation.invert](Geo-Paths#rotation_invert) - inverse-rotate the given location around the sphere.
* [rotation](Geo-Paths#_rotation) - rotate the given location around the sphere.

### [Projections](Geo-Projections)

* [albers.parallels](Geo-Projections#albers_parallels) - get or set the projection's two standard parallels.
* [d3.geo.albersUsa](Geo-Projections#albersUsa) - a composite Albers projection for the United States.
* [d3.geo.albers](Geo-Projections#albers) - the Albers equal-area conic projection.
* [d3.geo.azimuthalEqualArea.raw](Geo-Projections#azimuthalEqualArea_raw) - the raw azimuthal equal-area projection.
* [d3.geo.azimuthalEqualArea](Geo-Projections#azimuthalEqualArea) - the azimuthal equal-area projection.
* [d3.geo.azimuthalEquidistant.raw](Geo-Projections#azimuthalEquidistant_raw) - the azimuthal equidistant projection.
* [d3.geo.azimuthalEquidistant](Geo-Projections#azimuthalEquidistant) - the azimuthal equidistant projection.
* [d3.geo.conicConformal.raw](Geo-Projections#conicConformal_raw) - the raw conic conformal projection.
* [d3.geo.conicConformal](Geo-Projections#conicConformal) - the conic conformal projection.
* [d3.geo.conicEqualArea.raw](Geo-Projections#conicEqualArea_raw) the raw conic equal-area (a.k.a. Albers) projection.
* [d3.geo.conicEqualArea](Geo-Projections#conicEqualArea) the conic equal-area (a.k.a. Albers) projection.
* [d3.geo.conicEquidistant.raw](Geo-Projections#conicEquidistant_raw) - the raw conic equidistant projection.
* [d3.geo.conicEquidistant](Geo-Projections#conicEquidistant) - the conic equidistant projection.
* [d3.geo.equirectangular.raw](Geo-Projections#equirectangular_raw) - the raw equirectangular (plate carrée) projection.
* [d3.geo.equirectangular](Geo-Projections#equirectangular) - the equirectangular (plate carreé) projection.
* [d3.geo.gnomonic.raw](Geo-Projections#gnomonic_raw) - the raw gnomonic projection.
* [d3.geo.gnomonic](Geo-Projections#gnomonic) - the gnomonic projection.
* [d3.geo.mercator.raw](Geo-Projections#mercator_raw) - the raw Mercator projection.
* [d3.geo.mercator](Geo-Projections#mercator) - the spherical Mercator projection.
* [d3.geo.orthographic.raw](Geo-Projections#orthographic_raw) - the raw azimuthal orthographic projection.
* [d3.geo.orthographic](Geo-Projections#orthographic) - the azimuthal orthographic projection.
* [d3.geo.projectionMutator](Geo-Projections#projectionMutator) - create a standard projection from a mutable raw projection.
* [d3.geo.projection](Geo-Projections#projection) - create a standard projection from a raw projection.
* [d3.geo.stereographic.raw](Geo-Projections#stereographic_raw) - the raw azimuthal stereographic projection.
* [d3.geo.stereographic](Geo-Projections#stereographic) - the azimuthal stereographic projection.
* [d3.geo.transverseMercator.raw](Geo-Projections#transverseMercator_raw) - the raw transverse Mercator projection.
* [projection.center](Geo-Projections#center) - get or set the projection’s center location.
* [projection.clipAngle](Geo-Projections#clipAngle) - get or set the radius of the projection’s clip circle.
* [projection.clipExtent](Geo-Projections#clipExtent) - get or set the projection’s viewport clip extent, in pixels.
* [projection.invert](Geo-Projections#invert) - invert the projection for the specified point.
* [projection.precision](Geo-Projections#precision) - get or set the precision threshold for adaptive resampling.
* [projection.rotate](Geo-Projections#rotate) - get or set the projection’s three-axis rotation.
* [projection.scale](Geo-Projections#scale) - get or set the projection’s scale factor.
* [projection.stream](Geo-Projections#stream) - wrap the specified stream listener, projecting input geometry.
* [projection.translate](Geo-Projections#translate) - get or set the projection’s translation position.
* [projection](Geo-Projections#_projection) - project the specified location.

### [Streams](Geo-Streams)

* [clipExtent.extent](Geo-Streams#clipExtent_extent) - sets the clip extent.
* [d3.geo.clipExtent](Geo-Streams#clipExtent) - a stream transform that clips geometries to a given axis-aligned rectangle.
* [d3.geo.stream](Geo-Streams#stream) - convert a GeoJSON object to a geometry stream.
* [d3.geo.transform](Geo-Streams#transform) - transform streaming geometries.
* [stream.lineEnd](Geo-Streams#stream_lineEnd) - indicate the end of a line or ring.
* [stream.lineStart](Geo-Streams#stream_lineStart) - indicate the start of a line or ring.
* [stream.point](Geo-Streams#stream_point) - indicate an *x*, *y* (and optionally *z*) coordinate.
* [stream.polygonEnd](Geo-Streams#stream_polygonEnd) - indicate the end of a polygon.
* [stream.polygonStart](Geo-Streams#stream_polygonStart) - indicate the start of a polygon.
* [stream.sphere](Geo-Streams#stream_sphere) - indicate a sphere.
* [transform.stream](Geo-Streams#transform_stream) - wraps a given stream.

## [d3.geom (Geometry)](Geometry)

### [Voronoi](Voronoi-Geom)

* [d3.geom.voronoi](Voronoi-Geom#voronoi) - create a Voronoi layout with default accessors.
* [voronoi.clipExtent](Voronoi-Geom#clipExtent) - get or set the clip extent for the tesselation.
* [voronoi.links](Voronoi-Geom#links) - compute the Delaunay mesh as a network of links.
* [voronoi.triangles](Voronoi-Geom#triangles) - compute the Delaunay mesh as a triangular tessellation.
* [voronoi.x](Voronoi-Geom#x) - get or set the x-coordinate accessor for each point.
* [voronoi.y](Voronoi-Geom#y) - get or set the y-coordinate accessor for each point.
* [voronoi](Voronoi-Geom#_voronoi) - compute the Voronoi tessellation for the specified points.

### [Quadtree](Quadtree-Geom)

* [d3.geom.quadtree](Quadtree-Geom#quadtree) - constructs a quadtree for an array of points.
* [quadtree.add](Quadtree-Geom#add) - add a point to the quadtree.
* [quadtree.find](Quadtree-Geom#find) - find the closest point in the quadtree.
* [quadtree.visit](Quadtree-Geom#visit) - recursively visit nodes in the quadtree.

### [Polygon](Polygon-Geom)

* [d3.geom.polygon](Polygon-Geom#polygon) - create a polygon from the specified array of points.
* [polygon.area](Polygon-Geom#area) - compute the counterclockwise area of this polygon.
* [polygon.centroid](Polygon-Geom#centroid) - compute the area centroid of this polygon.
* [polygon.clip](Polygon-Geom#clip) - clip the specified polygon to this polygon.

### [Hull](Hull-Geom)

* [d3.geom.hull](Hull-Geom#hull) - create a convex hull layout with default accessors.
* [hull](Hull-Geom#_hull) - compute the convex hull for the given array of points.
* [hull.x](Hull-Geom#x) - get or set the *x*-coordinate accessor.
* [hull.y](Hull-Geom#y) - get or set the *y*-coordinate accessor.

## [d3.behavior (Behaviors)](Behaviors)

### [Drag](Drag-Behavior)

* [d3.behavior.drag](Drag-Behavior#drag)
* [drag.on](Drag-Behavior#on)
* [drag.origin](Drag-Behavior#origin)

### [Zoom](Zoom-Behavior)

* [d3.behavior.zoom](Zoom-Behavior#zoom) - create a zoom behavior.
* [zoom.center](Zoom-Behavior#center) - an optional focal point for mousewheel zooming.
* [zoom.duration](Zoom-Behavior#duration) - get or set the dblclick transition duration.
* [zoom.event](Zoom-Behavior#event) - dispatch zoom events after setting the scale or translate.
* [zoom.on](Zoom-Behavior#on) - listeners for when the scale or translate changes.
* [zoom.scaleExtent](Zoom-Behavior#scaleExtent) - optional limits on the scale factor.
* [zoom.scale](Zoom-Behavior#scale) - the current scale factor.
* [zoom.size](Zoom-Behavior#size) - the dimensions of the viewport.
* [zoom.translate](Zoom-Behavior#translate) - the current translate offset.
* [zoom.x](Zoom-Behavior#x) - an optional scale whose domain is bound to the _x_ extent of the viewport.
* [zoom.y](Zoom-Behavior#y) - an optional scale whose domain is bound to the _y_ extent of the viewport.
* [zoom](Zoom-Behavior#_zoom) - apply the zoom behavior to the selected elements.