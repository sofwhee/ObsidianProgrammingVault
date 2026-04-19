Webpack runs in NodeJS, not the browser. Use CommonJS syntax.

```bash
mkdir src && touch src/index.js src/greeting.js
```
```javascript
// index.js
import { greeting } from "./greeting.js";

console.log(greeting);
```

```javascript
// greeting.js
export const greeting = "Hello, Odinite!";
```

```javascript
// webpack.config.js
const path = require("path");

module.exports = {
  mode: "development",
  entry: "./src/index.js",
  output: {
    filename: "main.js",
    path: path.resolve(__dirname, "dist"),
    clean: true,
  },
};
```

```bash
npx webpack
```