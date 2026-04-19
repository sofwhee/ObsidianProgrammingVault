Process assets and move them from `/src` to `/dist`/`/build`

## CSS

To `import` a CSS file from within a JavaScript module, install `style-loader` and `css-loader` to `module` config. (`style-loader` comes first, then `css-loader` or else you get errors.)

```bash
npm install --save-dev style-loader css-loader
```

**webpack.config.js**
```diff
 const path = require('path');

 module.exports = {
   entry: './src/index.js',
   output: {
     filename: 'bundle.js',
     path: path.resolve(__dirname, 'dist'),
   },
+  module: {
+    rules: [
+      {
+        test: /\.css$/i,
+        use: ['style-loader', 'css-loader'],
+      },
+    ],
+  },
 };
```

A `<style>` tag with the stringified css will be inserted into the `<head>` of your html file.

### Example

```diff
  webpack-demo
  |- package.json
  |- package-lock.json
  |- webpack.config.js
  |- /dist
    |- bundle.js
    |- index.html
  |- /src
+   |- style.css
    |- index.js
  |- /node_modules
```

```css
.hello {
  color: red;
}
```

**src/index.js**
```diff
 import _ from 'lodash';
+import './style.css';

 function component() {
   const element = document.createElement('div');

   // Lodash, now imported by this script
   element.innerHTML = _.join(['Hello', 'webpack'], ' ');
+  element.classList.add('hello');

   return element;
 }

 document.body.appendChild(component());
```

```bash
npm run build
```

## Loading Images

Use the built-in [Asset Modules](https://webpack.js.org/guides/asset-modules/).

**webpack.config.js**
```javascript
 const path = require('path');

 module.exports = {
   entry: ...,
   output: {...},
   module: {
     rules: [{ test: ..., use: [...],},
+      {
+        test: /\.(png|svg|jpg|jpeg|gif)$/i,
+        type: 'asset/resource',
+      },
...
```

Let's add an image...

```javascript
 import _ from 'lodash';
 import './style.css';
+import Icon from './icon.png';
```

```javascript
 function component() {
   const element = document.createElement('div');

   // Lodash, now imported by this script
   element.innerHTML = _.join(['Hello', 'webpack'], ' ');
   element.classList.add('hello');

+  // Add the image to our existing div.
+  const myIcon = new Image();
+  myIcon.src = Icon;
+
+  element.appendChild(myIcon);
+
   return element;
 }

 document.body.appendChild(component());
```

```CSS
 .hello {
   color: red;
+  background: url('./icon.png');
 }
```

```bash
npm run build
```

You'll see that the actual filename has changed to something like `29822eaa871e8eadeaa4.png`. This means webpack found our file in the `src` folder and processed it!

## Loading Fonts

