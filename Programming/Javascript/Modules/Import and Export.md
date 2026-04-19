## Import

```javascript
// two.js
import { greeting, farewell } from "./one.js";

console.log(greeting); // "Hello, Odinite!"
console.log(farewell); // "Bye bye, Odinite!"
```

## Export

You can use both default and named exports in the same file.

Two styles.

```javascript
// one.js
export const greeting = "Hello, Odinite!";
export const farewell = "Bye bye, Odinite!";
```

```javascript
// one.js
const greeting = "Hello, Odinite!";
const farewell = "Bye bye, Odinite!";
export { greeting, farewell };
```
## Default export

Why default? Because upon `import`, you can name them!

Limit of one default export per file.

```javascript
// one.js
export default "Hello, Odinite!";
```

```javascript
// one.js
const greeting = "Hello, Odinite!";
export default greeting;
```