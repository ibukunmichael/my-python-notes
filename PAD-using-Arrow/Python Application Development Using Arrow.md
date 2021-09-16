# **Python Application Development Using Arrow** # 
 <!--images-->
![Getting Started](arrow1.png)

Arrow is a Python module for working with date and time. Comparing to the built-in date and time tools, it makes much easier to create, manipulate, format and convert dates, times, and timestamps. It is a Python library that offers a sensible, human-friendly approach to creating, manipulating, formatting and converting dates, times, and timestamps. It implements and updates the datetime type, plugging gaps in functionality, and provides an intelligent module API that supports many common creation scenarios. Simply put, it helps you work with dates and times with fewer imports and a lot less code.
### Why Arrow? ###
Python’s standard library and some other low-level modules have near-complete date, time and timezone functionality but don’t work very well from a usability perspective:
- Too many modules: datetime, time, calendar, dateutil, pytz and more
- Too many types: date, time, datetime, tzinfo, timedelta, relativedelta, etc.
- Timezones and timestamp conversions are verbose and unpleasant
- Timezone naivety is the norm
- Gaps in functionality: ISO-8601 parsing, time spans, humanization
**Features**
- Fully implemented, drop-in replacement for datetime
- Supports Python 2.6, 2.7, 3.3, 3.4 and 3.5
- Timezone-aware & UTC by default
- Provides super-simple creation options for many common input scenarios
- Updated .replace method with support for relative offsets, including weeks
- Formats and parses strings automatically
- Partial ISO-8601 support
- Timezone conversion
- Timestamp available as a property
- Generates time spans, ranges, floors and ceilings in time frames from year to microsecond
- Humanizes and supports a growing list of contributed locales
- Extensible for your own Arrow-derived types

### UTC time versus Local time ###
There is a pragmatic need for one global time. One global time helps to avoid confusion about time zones and daylight saving time. The UTC (Universal Coordinated time) is the primary time standard. UTC is used in aviation, weather forecasts, flight plans, air traffic control clearances, and maps. Unlike local time, UTC does not change with a change of seasons.
Local time is a time in a particular region or time zone.

### Installation ###
Installing Arrow is quite simple:
```{r, engine='shell', count_lines}
$ pip install arrow
```
**Example**
```{r, engine='shell', count_lines}
>>> import arrow
>>> utc = arrow.utcnow()
>>> utc
<Arrow [2018-05-11T21:23:58.970460+00:00]>
>>> utc = utc.shift(hours=-1)
>>> utc
<Arrow [2018-05-11T20:23:58.970460+00:00]>
>>> local = utc.to('US/Pacific')
>>> local
<Arrow [2018-05-11T13:23:58.970460-07:00]>
>>> arrow.get('2018-05-11T21:23:58.970460+00:00')
<Arrow [2018-05-11T21:23:58.970460+00:00]>
>>> local.timestamp
1368303838
>>> local.format()
'2018-05-11 13:23:58 -07:00'
>>> local.format('YYYY-MM-DD HH:mm:ss ZZ')
'2018-05-11 13:23:58 -07:00'
>>> local.humanize()
'an hour ago'
>>> local.humanize(locale='ko_kr')
```
### **Daylight saving time** ###
Daylight saving time (DST) is the practice of advancing clocks during summer months so that evening daylight lasts longer. The time is adjusted forward one hour in the beginning of spring and adjusted backward in the autumn to standard time.

**Try:**
```python
import arrow
now = arrow.now()
print(now.format("YYYY-MM-DD HH:mm:ss ZZ"))
print(now.dst())
```
### Humanizing date and time ###
On social web sites we can often see terms such as 'an hour ago' or '5 min ago', which provide quick information for humans about when the post was created or modified. Arrow contains a ```humanize()```method to create such terms.
**Try:**
```python
import arrow
now = arrow.now()
d1 = now.shift(minutes=-15).humanize()
print(d1)
d2 = now.shift(hours=5).humanize()
print(d2)
```
This example humanizes two dates. 
**Output:**
```{r, engine='shell', count_lines}
15 minutes ago
in 4 hours
```