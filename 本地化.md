> [Wiki](Home) ▸ [[API--中文手册]] ▸ [[核心函数]] ▸ **本地化**


按语言和地区格式化数字、日期和不同的货币。D3默认的支持英语，你可以按照需要加载新的本地化来改变D3的格式化行为。

<a name="locale" href="#locale">#</a> d3.<b>locale</b>(<i>definition</i>)

返回指定参数*definition*的新的本地化，数字格式的本地化必须包含下列属性：

* decimal - 数字区域字符串||（例如`"."`）。
* thousands - 组分隔字符串（例如`","`）。
* grouping - 分组大小数组（例如[3]），根据需要循环。
* currency - 货币前后缀字符串（例如 ["$", ""]）。

(注意：thousands 属性稍有命名不当，当组定义允许分组而不是几千。)

本地化定义必须包含以下时间属性：

* dateTime – 日期和时间(%c) 格式化字符串（例如："%a %b %e %X %Y"）。
* date - 日期 (%x) 格式化字符串（例如："%m/%d/%Y"）。
* time - 时间(%X) 格式化字符串（例如："%H:%M:%S"）。 
* periods –本地的上午和下午，同样（例如：["AM", "PM"]）。
* days – 星期的全称，以Sunday开始。
* shortDays -星期的简称，以Sunday开始。
* months –月份的全称，以January开始。
* shortMonths -月份的简称，以January开始。


例如默认的美式英语 (en_US) 本地化定义为：

```json
{
  "decimal": ".",
  "thousands": ",",
  "grouping": [3],
  "currency": ["$", ""],
  "dateTime": "%a %b %e %X %Y",
  "date": "%m/%d/%Y",
  "time": "%H:%M:%S",
  "periods": ["AM", "PM"],
  "days": ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"],
  "shortDays": ["Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"],
  "months": ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"],
  "shortMonths": ["Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"]
}
```

默认的俄语 (ru_RU) 本地化定义为：

```json
{
  "decimal": ",",
  "thousands": "\xa0",
  "grouping": [3],
  "currency": ["", " руб."],
  "dateTime": "%A, %e %B %Y г. %X",
  "date": "%d.%m.%Y",
  "time": "%H:%M:%S",
  "periods": ["AM", "PM"],
  "days": ["воскресенье", "понедельник", "вторник", "среда", "четверг", "пятница", "суббота"],
  "shortDays": ["вс", "пн", "вт", "ср", "чт", "пт", "сб"],
  "months": ["января", "февраля", "марта", "апреля", "мая", "июня", "июля", "августа", "сентября", "октября", "ноября", "декабря"],
  "shortMonths": ["янв", "фев", "мар", "апр", "май", "июн", "июл", "авг", "сен", "окт", "ноя", "дек"]
}
```

<a name="locale_numberFormat" href="#locale_numberFormat">#</a> locale.<b>numberFormat</b>(<i>specifier</i>)

[d3.format](Formatting#d3_format)本地化。

<a name="locale_timeFormat" href="#locale_timeFormat">#</a> locale.<b>timeFormat</b>(<i>specifier</i>)

[d3.time.format](Time-Formatting#format)本地化。

<a name="locale_timeFormat_utc" href="#locale_timeFormat_utc">#</a> locale.timeFormat.<b>utc</b>(<i>specifier</i>)

[d3.time.format.utc](Time-Formatting#format_utc)本地化。
