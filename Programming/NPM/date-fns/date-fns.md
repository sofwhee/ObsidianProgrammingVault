It's like Lodash for dates! (gives a bunch of helpful methods for manipulating data)

It has FP (Functional Programming) friendly variations. https://date-fns.org/v4.1.0/docs/FP-Guide


### install
`npm install date-fns --save`

### import
```javascript
// Just an example of some functions you can import
import { format, formatDistance, formatRelative, subDays } from 'date-fns';

// FP variation:

import { addDays, format } from "date-fns/fp";
```

### usage

```javascript
import { format, compareAsc } from "date-fns";

format(new Date(2014, 1, 11), "MM/dd/yyyy");
//=> '02/11/2014'

const dates = [
  new Date(1995, 6, 2),
  new Date(1987, 1, 11),
  new Date(1989, 6, 10),
];
dates.sort(compareAsc);
//=> [
//   Wed Feb 11 1987 00:00:00,
//   Mon Jul 10 1989 00:00:00,
//   Sun Jul 02 1995 00:00:00
// ]
```

```javascript
import { format, formatDistance, formatRelative, subDays } from 'date-fns'

format(new Date(), "'Today is a' eeee")
//=> "Today is a Tuesday"

formatDistance(subDays(new Date(), 3), new Date(), { addSuffix: true })
//=> "3 days ago"

formatRelative(subDays(new Date(), 3), new Date())
//=> "last Friday at 7:26 p.m."
```

## Submodules

To use submodules, install the npm package and then import a function from a submodule.

```javascript
// The main submodule:
import { addDays } from "date-fns";

// FP variation:
import { addDays, format } from "date-fns/fp";
```

L18n submodule (Internationalization)
```javascript
import { formatRelative, subDays } from 'date-fns'
import { es, ru } from 'date-fns/locale'

formatRelative(subDays(new Date(), 3), new Date())
//=> "last Friday at 7:26 p.m."

formatRelative(subDays(new Date(), 3), new Date(), { locale: es })
//=> "el viernes pasado a las 19:26"

formatRelative(subDays(new Date(), 3), new Date(), { locale: ru })
//=> "в прошлую пятницу в 19:26"
```