# Useful Constants

They're mostly time conversion. They all basically tell you how many seconds are in a year or an hour or whatever.

https://date-fns.org/v4.1.0/docs/constants

`constructFromSymbol`
Symbol enabling Date extensions to inherit properties from the reference date.

Dunno what that means...

# Probably useful helpers

https://date-fns.org/v4.1.0/docs/add
#### isPast
Is the given date in the past?
#### isFuture
Is in the future?
#### isDate
Is the given value a date?
#### isValid
Is the given date valid?
#### isExists
Does the given date exist?

```javascript
const result = isExists(2018, 1, 31) //=> false
```
#### isMatch
Validates date string against a format.

```javascript
const result = isMatch('02/11/2014', 'MM/dd/yyyy') //=> true
```

#### format
Format the date.
https://date-fns.org/v4.1.0/docs/format
```javascript
const result = format(new Date(2014, 1, 11), 'MM/dd/yyyy') 
//=> '02/11/2014'
const result = format(new Date(2014, 6, 2, 15), "h 'o''clock'") 
//=> "3 o'clock"
const result = format(new Date(2025, 3, 19, 14), "MMM d E..EEE")
//=> "FEB 4 Wed"
const result = format(new Date(2025, 3, 19, 14), "MMM d yyyy")
//=> "FEB 4 2025"
```

#### `formatRelative(date, baseDate, options?)`

| Distance to the base date | Result                  |
| ------------------------- | ----------------------- |
| Previous 6 days           | last Sunday at 04:30 AM |
| Last day                  | yesterday at 04:30 AM   |
| Same day                  | today at 04:30 AM       |
| Next day                  | tomorrow at 04:30 AM    |
| Next 6 days               | Sunday at 04:30 AM      |
| Other                     | 12/31/2017              |

```javascript
// subDays = subtract days from a given date
const result = formatRelative(subDays(new Date(), 6), new Date()) 
//=> "last Thursday at 12:45 AM"
```

####