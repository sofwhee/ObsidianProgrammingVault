While the module pattern used to play a big part in helping us manage this, the release of ES6 (sometimes referred to as ES2015) gave us actual “modules” and thus they are often referred to as “ES6 modules” or “ESM”.

This allows us more control over what is in our scope.

(A top-level variable in a module will not be accessible in the global scope.)

There isn’t really a universally agreed-upon rule for when to use either named or default.

named export: `export { }`

```javascript
export const greeting = "Hello, Odinite!";
export const farewell = "Bye bye, Odinite!";
```

```javascript
const greeting = "Hello, Odinite!";
const farewell = "Bye bye, Odinite!";
export { greeting, farewell };
```

Default export:  `export default { }`

Something exported this way does not have a name attached to it, so when you import it somewhere, you can decide what name to give it.

a file can only default export a single thing.

```javascript
export default "Hello, Odinite!";
```

```javascript
const greeting = "Hello, Odinite!";
export default greeting;
```

import

```javascript
import { greeting, farewell } from "./one.js";
```

```javascript
import helloOdinite from "./one.js";
```