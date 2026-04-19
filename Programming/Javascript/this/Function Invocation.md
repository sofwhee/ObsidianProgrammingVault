Non-strict mode:
`this` references `global` object.

```Javascript
function show() {
	console.log(this === window); // true
}
```

Strict mode:
Using `this` inside a function returns undefined.

```javascript
"use strict";

function show() {
	console.log(this === undefined); // true
}
```