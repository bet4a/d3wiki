> [Wiki](Home) ▸ [[API Reference]] ▸ [[Time]] ▸ **Time Intervals**

**Time intervals** are irregular! For example, there are 60 seconds in a minute, but 24 hours in a day. Even more confusing, some days have 23 or 25 hours due to [daylight saving time](http://en.wikipedia.org/wiki/Daylight_saving_time), and the standard [Gregorian calendar](http://en.wikipedia.org/wiki/Gregorian_calendar) uses months of differing lengths. And then there are leap years and leap seconds!

To simplify manipulation of and iteration over time intervals, D3 provides a handful of time utilities in addition to the time [scale](Time-Scales) and [format](Time-Formatting). The utilities support both local time and UTC time. Local time is determined by the browser's JavaScript runtime; arbitrary time zone support would be nice, but requires access to the Olson zoneinfo files.

## Interval

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

Returns a corresponding time interval in UTC rather than local time. For example, `d3.time.day.range(start, stop)` returns local time days between *start* and *stop*, while `d3.time.day.utc.range(start, stop)` returns UTC days between *start* and *stop*.

## Intervals

<a name="second" href="#wiki-second">#</a> d3.time.**second**

Seconds (e.g., 01:23:45.0000 AM). Always 1,000 milliseconds long.

<a name="minute" href="#wiki-minute">#</a> d3.time.**minute**

Minutes (e.g., 01:02:00 AM). Most browsers do not support leap seconds, so minutes are almost always 60 seconds (6e4 milliseconds) long.

<a name="hour" href="#wiki-hour">#</a> d3.time.**hour**

Hours (e.g., 01:00 AM). 60 minutes long (36e5 milliseconds). Note that advancing time by one hour can return the same hour number, or skip an hour number, due to Daylight Savings Time.

<a name="day" href="#wiki-day">#</a> d3.time.**day**

Days (e.g., February 7, 2012 at 12:00 AM). Most days are 24 hours long (864e5 milliseconds); however, with Daylight Savings Time, a day may be 23 or 25 hours long.

<a name="week" href="#wiki-week">#</a> d3.time.**week**

Alias for d3.time.[sunday](#wiki-sunday). A week is always 7 days, but ranges between 167 and 169 hours depending on Daylight Savings Time.

<a name="sunday" href="#wiki-sunday">#</a> d3.time.**sunday**

Sunday-based weeks (e.g., February 5, 2012 at 12:00 AM).

<a name="monday" href="#wiki-monday">#</a> d3.time.**monday**

Monday-based weeks (e.g., February 6, 2012 at 12:00 AM). 

<a name="tueday" href="#wiki-tueday">#</a> d3.time.**tueday**

Tueday-based weeks (e.g., February 7, 2012 at 12:00 AM). 

<a name="wednesday" href="#wiki-wednesday">#</a> d3.time.**wednesday**

Wednesday-based weeks (e.g., February 8, 2012 at 12:00 AM). 

<a name="thursday" href="#wiki-thursday">#</a> d3.time.**thursday**

Thursday-based weeks (e.g., February 9, 2012 at 12:00 AM). 

<a name="friday" href="#wiki-friday">#</a> d3.time.**friday**

Friday-based weeks (e.g., February 10, 2012 at 12:00 AM). 

<a name="saturday" href="#wiki-saturday">#</a> d3.time.**saturday**

Saturday-based weeks (e.g., February 11, 2012 at 12:00 AM). 

<a name="month" href="#wiki-month">#</a> d3.time.**month**

Months (e.g., February 1, 2012 at 12:00 AM). Ranges between 28 and 31 days.

<a name="year" href="#wiki-year">#</a> d3.time.**year**

Years (e.g., January 1, 2012 at 12:00 AM). Normal years are 365 days long; leap years are 366.

## Aliases

<a name="days" href="#wiki-days">#</a> d3.time.<b>days</b>(<i>start</i>, <i>stop</i>[, <i>step</i>])

Alias for d3.time.[day](#wiki-day).[range](#wiki-interval_range). Returns the day boundaries (midnight) after or equal to *start* and before *stop*. If *step* is specified, then every *step*'th date will be returned, based on the day of the month. For example, a *step* of 2 will return the 1st, 3rd, 5th *etc.* of the month.

<a name="hours" href="#wiki-hours">#</a> d3.time.<b>hours</b>(<i>start</i>, <i>stop</i>[, <i>step</i>])

Alias for d3.time.[hour](#wiki-hour).[range](#wiki-interval_range). Returns the hour boundaries (e.g., 01 AM) after or equal to *start* and before *stop*. If *step* is specified, then every *step*'th hour will be returned, based on the hour of the day. For example, a *step* of 3 will return 9 PM, 12 AM, 3 AM, *etc.*

<a name="minutes" href="#wiki-minutes">#</a> d3.time.<b>minutes</b>(<i>start</i>, <i>stop</i>[, <i>step</i>])

Alias for d3.time.[minute](#wiki-minute).[range](#wiki-interval_range). Returns the minute boundaries (e.g., 01:23 AM) after or equal to *start* and before *stop*. If *step* is specified, then every *step*'th minute will be returned, based on the minute of the hour. For example, a *step* of 15 will return 9:45 PM, 10:00 PM, 10:15 PM, *etc.*

<a name="months" href="#wiki-months">#</a> d3.time.<b>months</b>(<i>start</i>, <i>stop</i>[, <i>step</i>])

Alias for d3.time.[month](#wiki-month).[range](#wiki-interval_range). Returns the month boundaries (e.g., January 01) after or equal to *start* and before *stop*. If *step* is specified, then every *step*'th month will be returned, based on the month of the year. For example, a *step* of 3 will return January, April, July, *etc.*

<a name="seconds" href="#wiki-seconds">#</a> d3.time.<b>seconds</b>(<i>start</i>, <i>stop</i>[, <i>step</i>])

Alias for d3.time.[second](#wiki-second).[range](#wiki-interval_range). Returns the second boundaries (e.g., 01:23:45 AM) after or equal to *start* and before *stop*. If *step* is specified, then every *step*'th second will be returned, based on the second of the minute. For example, a *step* of 15 will return 9:01:45 PM, 9:02:00 PM, 9:02:15 PM, *etc.*

<a name="weeks" href="#wiki-weeks">#</a> d3.time.<b>weeks</b>(<i>start</i>, <i>stop</i>[, <i>step</i>])

Alias for d3.time.[sunday](#wiki-sunday).[range](#wiki-interval_range). Returns the week boundaries (midnight Sunday) after or equal to *start* and before *stop*. If *step* is specified, then every *step*'th week will be returned, based on the week of the year. For example, a *step* of 4 will return January 2, January 30, February 27, *etc.*

<a name="years" href="#wiki-years">#</a> d3.time.<b>years</b>(<i>start</i>, <i>stop</i>[, <i>step</i>])

Alias for d3.time.[year](#wiki-year).[range](#wiki-interval_range). Returns the year boundaries (midnight January 1st) after or equal to *start* and before *stop*. If *step* is specified, then every *step*'th year will be returned. For example, a *step* of 5 will return 2010, 2015, 2020, *etc.*

## Math

<a name="dayOfYear" href="#wiki-dayOfYear">#</a> d3.time.**dayOfYear**(*date*)

Returns the day number for the given date. The first day of the year (January 1) is always the 0th day. Unlike the [d3.time.format](Time-Formatting)'s %j directive, dayOfYear is 0-based rather than 1-based.

<a name="weekOfYear" href="#wiki-weekOfYear">#</a> d3.time.**weekOfYear**(*date*)

Alias for [sundayOfYear](#wiki-sundayOfYear).

<a name="sundayOfYear" href="#wiki-sundayOfYear">#</a> d3.time.**sundayOfYear**(*date*)

Returns the Sunday-based week number for the given date. The first day of the year (January 1) is always the 0th week. Equivalent to [d3.time.format](Time-Formatting)'s %U directive.

<a name="mondayOfYear" href="#wiki-mondayOfYear">#</a> d3.time.**mondayOfYear**(*date*)

Returns the Monday-based week number for the given date. The first day of the year (January 1) is always the 0th week. Equivalent to [d3.time.format](Time-Formatting)'s %W directive.

<a name="tuesdayOfYear" href="#wiki-tuesdayOfYear">#</a> d3.time.**tuesdayOfYear**(*date*)

Returns the Tuesday-based week number for the given date. The first day of the year (January 1) is always the 0th week.

<a name="wednesdayOfYear" href="#wiki-wednesdayOfYear">#</a> d3.time.**wednesdayOfYear**(*date*)

Returns the Wednesday-based week number for the given date. The first day of the year (January 1) is always the 0th week.

<a name="thursdayOfYear" href="#wiki-thursdayOfYear">#</a> d3.time.**thursdayOfYear**(*date*)

Returns the Thursday-based week number for the given date. The first day of the year (January 1) is always the 0th week.

<a name="fridayOfYear" href="#wiki-fridayOfYear">#</a> d3.time.**fridayOfYear**(*date*)

Returns the Friday-based week number for the given date. The first day of the year (January 1) is always the 0th week.

<a name="saturdayOfYear" href="#wiki-saturdayOfYear">#</a> d3.time.**saturdayOfYear**(*date*)

Returns the Saturday-based week number for the given date. The first day of the year (January 1) is always the 0th week.