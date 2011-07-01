> [[API Reference]]

D3 includes a helper module for parsing and formatting dates modeled after the venerable [strptime](http://pubs.opengroup.org/onlinepubs/009695399/functions/strptime.html) and [strftime](http://pubs.opengroup.org/onlinepubs/007908799/xsh/strftime.html) C-library standards. These functions are also notably available in Python's [time](http://docs.python.org/library/time.html) module.

<a name="format" href="#format">#</a> d3.time.<b>format</b>(<i>specifier</i>)

Constructs a new time formatter using the given *specifier*. The specifier string may contain the following directives.

* %a - abbreviated weekday name.
* %A - full weekday name.
* %b - abbreviated month name.
* %B - full month name.
* %c - date and time, as "%a %b %e %H:%M:%S %Y".
* %d - day of the month as a decimal number [01,31].
* %H - hour (24-hour clock) as a decimal number [00,23].
* %I - hour (12-hour clock) as a decimal number [01,12].
* %j - day of the year as a decimal number [001,366].
* %m - month as a decimal number [01,12].
* %M - minute as a decimal number [00,59].
* %p - either AM or PM.
* %S - second as a decimal number [00,61].
* %U - week number of the year (Sunday as the first day of the week) as a decimal number [00,53]. All days in a new year preceding the first Sunday are considered to be in week 0.
* %w - weekday as a decimal number [0(Sunday),6].
* %W - week number of the year (Monday as the first day of the week) as a decimal number [00,53]. All days in a new year preceding the first Monday are considered to be in week 0.
* %x - date, as "%m/%d/%y".
* %X - time, as "%H:%M:%S".
* %y - year without century as a decimal number [00,99].
* %Y - year with century as a decimal number.
* %Z - time zone offset, such as "-0700".
* %% - a literal "%" character.	

In some implementations of strftime and strptime (as in Python), a directive may include an optional field width or precision; this feature is not yet implemented in D3, but may be added in the future. Also note that the JavaScript environment does not provide a standard API for accessing locale-specific date and time formatters, so D3's implementation assumes the conventions of the English language (United States).

<a name="_format" href="#_format">#</a> <b>format</b>(<i>date</i>)

…

<a name="parse" href="#parse">#</a> format.<b>parse</b>(<i>string</i>)

…

<a name="format_utc" href="#format_utc">#</a> d3.time.format.<b>utc</b>(<i>specifier</i>)

…

<a name="format_iso" href="#format_iso">#</a> d3.time.format.<b>iso</b>

… %Y-%m-%dT%H:%M:%SZ
