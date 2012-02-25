> [[API Reference]] ▸ [[Time]]

**Time intervals** are irregular! For example, there are 60 seconds in a minute, but 24 hours in a day. Even more confusing, some days have 23 or 25 hours due to [daylight saving time](http://en.wikipedia.org/wiki/Daylight_saving_time), and the standard [Gregorian calendar](http://en.wikipedia.org/wiki/Gregorian_calendar) uses months of differing lengths. And then there are leap years and leap seconds!

To simplify manipulation of and iteration over time intervals, D3 provides a handful of time utilities in addition to the time [scale](Time-Scales) and [format](Time-Formatting). The utilities support both local time and UTC time. Local time is determined by the browser's JavaScript runtime; arbitrary time zone support would be nice, but requires access to the Olson zoneinfo files.

<a name="interval" href="#wiki-interval">#</a> d3.time.*interval*

Returns the specified *interval*. The following intervals are supported:

* d3.time.[second](#wiki-second)
* d3.time.[minute](#wiki-minute)
* d3.time.[hour](#wiki-hour)
* d3.time.[day](#wiki-day)
* d3.time.[week](#wiki-week) (alias for d3.time.[sunday](#wiki-sunday))
* d3.time.[sunday](#wiki-sunday)
* d3.time.[monday](#wiki-monday)
* d3.time.[tuesday](#wiki-tuesday)
* d3.time.[wednesday](#wiki-wednesday)
* d3.time.[thursday](#wiki-thursday)
* d3.time.[friday](#wiki-friday)
* d3.time.[saturday](#wiki-saturday)
* d3.time.[month](#wiki-month)
* d3.time.[year](#wiki-year)

<a name="_interval" href="#wiki-_interval">#</a> *interval*(*date*)

Alias for *interval*.floor(*date*). For example, `d3.time.day(new Date())` returns midnight (12:00 AM) on the current day, in local time.

<a name="interval_floor" href="#wiki-interval_floor">#</a> *interval*.**floor**(*date*)

Returns the latest time interval before or equal to the specified *date*. For example, `d3.time.day.floor(new Date())` returns midnight (12:00 AM) on the current day, in local time.

<a name="interval_round" href="#wiki-interval_round">#</a> *interval*.**round**(*date*)

Returns the closest time interval to the specified *date*. For example, `d3.time.day.round(new Date())` returns midnight (12:00 AM) on the current day if it is on or before noon, and midnight of the following day if it is after noon.

<a name="interval_ceil" href="#wiki-interval_ceil">#</a> *interval*.**ceil**(*date*)

Returns the earliest time interval after the specified *date*. For example, `d3.time.day.ceil(new Date())` returns midnight (12:00 AM) on the following day, in local time.

<a name="interval_range" href="#wiki-interval_range">#</a> *interval*.**range**(*start*, *stop*[, *step*])

Returns every time interval after or equal to *start* and before *stop*.  If *step* is specified, then every *step*'th interval will be returned, based on the interval number (such as day of month for d3.time.day). For example, a *step* of 2 will return the 1st, 3rd, 5th *etc.* of the month with d3.time.day.

<a name="interval_offset" href="#wiki-interval_offset">#</a> *interval*.**offset**(*date*, *step*)

Returns a new date equal to *date* plus *step* intervals. If *step* is negative, then the returned date will be before the specified *date*; if *step* is zero, then a copy of the specified *date* is returned. This method does not round the specified *date* to the interval. For example, if it is currently 5:34 PM, then `d3.time.day.offset(new Date(), 1)` returns 5:34 PM tomorrow (even if Daylight Savings Time changes!).

<a name="interval_utc" href="#wiki-interval_utc">#</a> *interval*.**utc**

Returns a corresponding time interval in UTC rather than local time.

<a name="day" href="Time-Intervals#wiki-day">#</a> d3.time.<b>day</b>(<i>date</i>)<br>
<a name="day_utc" href="Time-Intervals#wiki-day_utc">#</a> d3.time.day.<b>utc</b>(<i>date</i>)

Returns the latest day boundary (midnight) before or equal to *date*.

<a name="days" href="Time-Intervals#wiki-days">#</a> d3.time.<b>days</b>(<i>start</i>, <i>stop</i>[, <i>step</i>])<br>
<a name="days_utc" href="Time-Intervals#wiki-days_utc">#</a> d3.time.days.<b>utc</b>(<i>start</i>, <i>stop</i>[, <i>step</i>])

Returns the day boundaries (midnight) after or equal to *start* and before *stop*. If *step* is specified, then every *step*'th date will be returned, based on the day of the month. For example, a *step* of 2 will return the 1st, 3rd, 5th *etc.* of the month.

<a name="hour" href="Time-Intervals#wiki-hour">#</a> d3.time.<b>hour</b>(<i>date</i>)<br>
<a name="hour_utc" href="Time-Intervals#wiki-hour_utc">#</a> d3.time.hour.<b>utc</b>(<i>date</i>)

Returns the latest hour boundary (e.g., 01 AM) before or equal to *date*.

<a name="hours" href="Time-Intervals#wiki-hours">#</a> d3.time.<b>hours</b>(<i>start</i>, <i>stop</i>[, <i>step</i>])<br>
<a name="hours_utc" href="Time-Intervals#wiki-hours_utc">#</a> d3.time.hours.<b>utc</b>(<i>start</i>, <i>stop</i>[, <i>step</i>])

Returns the hour boundaries (e.g., 01 AM) after or equal to *start* and before *stop*. If *step* is specified, then every *step*'th hour will be returned, based on the hour of the day. For example, a *step* of 3 will return 9 PM, 12 AM, 3 AM, *etc.*

<a name="minute" href="Time-Intervals#wiki-minute">#</a> d3.time.<b>minute</b>(<i>date</i>)<br>
<a name="minute_utc" href="Time-Intervals#wiki-minute_utc">#</a> d3.time.minute.<b>utc</b>(<i>date</i>)

Returns the latest minute boundary (e.g., 01:23 AM) before or equal to *date*.

<a name="minutes" href="Time-Intervals#wiki-minutes">#</a> d3.time.<b>minutes</b>(<i>start</i>, <i>stop</i>[, <i>step</i>])<br>
<a name="minutes_utc" href="Time-Intervals#wiki-minutes_utc">#</a> d3.time.minutes.<b>utc</b>(<i>start</i>, <i>stop</i>[, <i>step</i>])

Returns the minute boundaries (e.g., 01:23 AM) after or equal to *start* and before *stop*. If *step* is specified, then every *step*'th minute will be returned, based on the minute of the hour. For example, a *step* of 15 will return 9:45 PM, 10:00 PM, 10:15 PM, *etc.*

<a name="month" href="Time-Intervals#wiki-month">#</a> d3.time.<b>month</b>(<i>date</i>)<br>
<a name="month_utc" href="Time-Intervals#wiki-month_utc">#</a> d3.time.month.<b>utc</b>(<i>date</i>)

Returns the latest month boundary (e.g., January 01) before or equal to *date*.

<a name="months" href="Time-Intervals#wiki-months">#</a> d3.time.<b>months</b>(<i>start</i>, <i>stop</i>[, <i>step</i>])<br>
<a name="months_utc" href="Time-Intervals#wiki-months_utc">#</a> d3.time.months.<b>utc</b>(<i>start</i>, <i>stop</i>[, <i>step</i>])

Returns the month boundaries (e.g., January 01) after or equal to *start* and before *stop*. If *step* is specified, then every *step*'th month will be returned, based on the month of the year. For example, a *step* of 3 will return January, April, July, *etc.*

<a name="second" href="Time-Intervals#wiki-second">#</a> d3.time.<b>second</b>(<i>date</i>)<br>
<a name="second_utc" href="Time-Intervals#wiki-second_utc">#</a> d3.time.second.<b>utc</b>(<i>date</i>)

Returns the latest second boundary (e.g., 01:23:45 AM) before or equal to *date*.

<a name="seconds" href="Time-Intervals#wiki-seconds">#</a> d3.time.<b>seconds</b>(<i>start</i>, <i>stop</i>[, <i>step</i>])<br>
<a name="seconds_utc" href="Time-Intervals#wiki-seconds_utc">#</a> d3.time.seconds.<b>utc</b>(<i>start</i>, <i>stop</i>[, <i>step</i>])

Returns the second boundaries (e.g., 01:23:45 AM) after or equal to *start* and before *stop*. If *step* is specified, then every *step*'th second will be returned, based on the second of the minute. For example, a *step* of 15 will return 9:01:45 PM, 9:02:00 PM, 9:02:15 PM, *etc.*

<a name="week" href="Time-Intervals#wiki-week">#</a> d3.time.<b>week</b>(<i>date</i>)<br>
<a name="week_utc" href="Time-Intervals#wiki-week_utc">#</a> d3.time.week.<b>utc</b>(<i>date</i>)

Returns the latest week boundary (midnight Sunday) before or equal to *date*.

<a name="weeks" href="Time-Intervals#wiki-weeks">#</a> d3.time.<b>weeks</b>(<i>start</i>, <i>stop</i>[, <i>step</i>])<br>
<a name="weeks_utc" href="Time-Intervals#wiki-weeks_utc">#</a> d3.time.weeks.<b>utc</b>(<i>start</i>, <i>stop</i>[, <i>step</i>])

Returns the week boundaries (midnight Sunday) after or equal to *start* and before *stop*. If *step* is specified, then every *step*'th week will be returned, based on the week of the year. For example, a *step* of 4 will return January 2, January 30, February 27, *etc.*

<a name="year" href="Time-Intervals#wiki-year">#</a> d3.time.<b>year</b>(<i>date</i>)<br>
<a name="year_utc" href="Time-Intervals#wiki-year_utc">#</a> d3.time.year.<b>utc</b>(<i>date</i>)

Returns the latest year boundary (midnight January 1st) before or equal to *date*.

<a name="years" href="Time-Intervals#wiki-years">#</a> d3.time.<b>years</b>(<i>start</i>, <i>stop</i>[, <i>step</i>])<br>
<a name="years_utc" href="Time-Intervals#wiki-years_utc">#</a> d3.time.years.<b>utc</b>(<i>start</i>, <i>stop</i>[, <i>step</i>])

Returns the year boundaries (midnight January 1st) after or equal to *start* and before *stop*. If *step* is specified, then every *step*'th year will be returned. For example, a *step* of 5 will return 2010, 2015, 2020, *etc.*