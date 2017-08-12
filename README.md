### remoteTime.js

is a simple jQuery plugin that attaches a clock to a `<div>` or `<span>`. The plugin makes use of Google Maps' Geocode and Timezone APIs to show the time in the given location.

#### Usage
Include jQuery. Instantiate the pugin on your jQuery object like so...

	$("#LATime").remoteTime({
		key: "your API key",
		location: "Los Angeles, California",
		format: "m/d/y g:i:s a"
	});
#### Parameters
There are only 3 parameters, all passed as properties of a single object, all required.

 - **`key`** A Google API key with both geocode and timezone services enabled.
 - **`location`** A string representing a location. Can be an address or zip code or just about anything. Google's best guess will be used, so less ambiguous locations (addresses) are preferred.
 - **`format`** A string representing the format to be used to display the time. See the Formatting section below.
#### Formatting
I wrote [this function](https://gist.github.com/Pamblam/4d33935d712903da10c7366c20157d21) for some reason a while back that uses a subset of the [PHP date shorthand](http://php.net/manual/en/function.date.php) to format a date string in Javascript the same way PHP does. A slightly modified version of this function is doing the formatting in this plugin.

The following characters are recognized in the format parameter string:

| format character  | Description | Example returned values |
| ------------- | ------------- | -------------- |
| **Day**  | **--**  | **--** |
| *d*  | Day of the month, 2 digits with leading zeros | 01 to 31 |
| *D* | A textual representation of a day, three letters  | Mon through Sun |
| *j* | Day of the month without leading zeros | 1 to 31 |
| *l* (lowercase 'L') | A full textual representation of the day of the week | Sunday through Saturday |
| *w*  | Numeric representation of the day of the week | 0 (for Sunday) through 6 (for Saturday) |
| **Month** | **--** | **--** |
| *F* | A full textual representation of a month, such as January or March | January through December |
| *m* | Numeric representation of a month, with leading zeros | 01 through 12 |
| *M* | A short textual representation of a month, three letters | Jan through Dec |
| *n* | Numeric representation of a month, without leading zeros | 1 through 12 |
| **Year** | **--** | **--** |
| *Y* | A full numeric representation of a year, 4 digits | Examples: 1999 or 2003 |
| *y* | A two digit representation of a year | Examples: 99 or 03 |
| **Time** | **--** | **--** |
| *a* | Lowercase Ante meridiem and Post meridiem | am or pm |
| *A* | Uppercase Ante meridiem and Post meridiem | AM or PM |
| *g* | 12-hour format of an hour without leading zeros | 1 through 12 |
| *G* | 24-hour format of an hour without leading zeros | 0 through 23 |
| *h* | 12-hour format of an hour with leading zeros | 01 through 12 |
| *H* | 24-hour format of an hour with leading zeros | 00 through 23 |
| *i* | Minutes with leading zeros | 00 to 59 |
| *s* | Seconds, with leading zeros | 00 through 59 |

Unrecognized characters as well as characters immediately preceded by a `\` in the format string will be printed as-is.
 

