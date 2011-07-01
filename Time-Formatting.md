> [[API Reference]]

D3 includes a helper module for parsing and formatting dates modeled after the venerable [strptime](http://pubs.opengroup.org/onlinepubs/009695399/functions/strptime.html) and [strftime](http://pubs.opengroup.org/onlinepubs/007908799/xsh/strftime.html) C-library standards. These functions are also notably available in Python's [time](http://docs.python.org/library/time.html) module.

<a name="format" href="#format">#</a> d3.time.<b>format</b>(<i>specifier</i>)

Constructs a new local time formatter using the given *specifier*. The specifier string may contain the following directives.

* %a - abbreviated weekday name.
* %A - full weekday name.
* %b - abbreviated month name.
* %B - full month name.
* %c - date and time, as "%a %b %e %H:%M:%S %Y".
* %d - zero-padded day of the month as a decimal number [01,31].
* %e - space-padded day of the month as a decimal number [ 1,31].
* %H - hour (24-hour clock) as a decimal number [00,23].
* %I - hour (12-hour clock) as a decimal number [01,12].
* %j - day of the year as a decimal number [001,366].
* %m - month as a decimal number [01,12].
* %M - minute as a decimal number [00,59].
* %p - either AM or PM.
* %S - second as a decimal number [00,61].
* %U - week number of the year (Sunday as the first day of the week) as a decimal number [00,53].
* %w - weekday as a decimal number [0(Sunday),6].
* %W - week number of the year (Monday as the first day of the week) as a decimal number [00,53].
* %x - date, as "%m/%d/%y".
* %X - time, as "%H:%M:%S".
* %y - year without century as a decimal number [00,99].
* %Y - year with century as a decimal number.
* %Z - time zone offset, such as "-0700".
* %% - a literal "%" character.	

For %U, all days in a new year preceding the first Sunday are considered to be in week 0. For %W, all days in a new year preceding the first Monday are considered to be in week 0. In some implementations of strftime and strptime (as in Python), a directive may include an optional field width or precision; this feature is not yet implemented in D3, but may be added in the future. Also note that the JavaScript environment does not provide a standard API for accessing locale-specific date and time formatters, so D3's implementation assumes the conventions of the English language (United States).

<a name="_format" href="#_format">#</a> <b>format</b>(<i>date</i>)

Formats the specified *date*, returning the corresponding string. The *date* must be a JavaScript [Date](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Date) object. Note that when dates are used in conjunction with [quantitative scales](Quantitative-Scales), the dates are implicitly coerced to numbers representing the number of milliseconds since [UNIX epoch](http://en.wikipedia.org/wiki/Unix_time). To convert between numbers and dates, you can use the following code:

```javascript
time = +date; // convert a Date object to time in milliseconds
date = new Date(time); // convert a time in milliseconds to a Date object
```

If you prefer to be explicit, you can also use the date object's [getTime](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Date/getTime) method, but the + operator is shorter and possibly faster.

<a name="parse" href="#parse">#</a> format.<b>parse</b>(<i>string</i>)

Parses the specified *string*, returning the corresponding date object. If the parsing fails, returns null. Unlike "natural language" date parsers (including JavaScript's built-in [parse](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Date/parse)), this method is strict: if the specified string does not exactly match the associated format specifier, this method returns null. For example, if the associated format is the full ISO 8601 string "%Y-%m-%dT%H:%M:%SZ", then the string "2011-07-01T19:15:28Z" will be parsed correctly, but "2011-07-01T19:15:28", "2011-07-01 19:15:28" and "2011-07-01" will return null, despite being valid 8601 dates. If desired, you can use multiple formats to try multiple format specifiers sequentially.

The following directives are *not yet supported* for parsing:

* %j - day of the year.
* %U - week number of the year.
* %w - weekday number.
* %W - week number of the year.
* %Z - time zone offset, such as "-0700".
* %% - a literal "%" character.	

Also, note that %d and %e are considered equivalent for parsing.

<a name="format_utc" href="#format_utc">#</a> d3.time.format.<b>utc</b>(<i>specifier</i>)

Constructs a new UTC time formatter using the given *specifier*. The specifier may contain the same directives as the local time [format](#format). Internally, this time formatter is implemented using the UTC methods on the Date object, such as [getUTCDate](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Date/getUTCDate) and [setUTCDate](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Date/setUTCDate) in place of [getDate](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Date/getDate) and [setDate](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Date/setDate).

<a name="format_iso" href="#format_iso">#</a> d3.time.format.<b>iso</b>

The full ISO 8601 UTC time format: "%Y-%m-%dT%H:%M:%SZ".