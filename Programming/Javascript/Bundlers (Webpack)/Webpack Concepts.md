## Entry (point)

It indicates which module webpack should use to begin building out its internal **dependency graph.** Default: `./src/index.js`

**webpack.config.js**
```js
module.exports = {
  entry: './path/to/my/entry/file.js',
};
```
## Output

Where to emit the *bundles* and how to name them. Main output file default: `./dist/main.js` Any other file default: `./dist`

`output.filename` = bundle name
`output.path` = bundle destination

**webpack.config.js**
```javascript
const path = require('path');

module.exports = {
  entry: './path/to/my/entry/file.js',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'my-first-webpack.bundle.js',
  },
};
```

## Loaders

Webpack only understands JS and JSON files. Loaders let it process other types into valid modules that can be consumed by your application and added to the dependency graph. 

`rules` 
	`test` property identifies which file(s) to be transformed
	`use` property indicates which loader to use

**webpack.config.js**
```javascript
const path = require('path');

module.exports = {
  output: {
    filename: 'my-first-webpack.bundle.js',
  },
  module: {
    rules: [{ test: /\.txt$/, use: 'raw-loader' }],
  },
};

// "Hey webpack compiler, when you come across a path that resolves to a '.txt' file inside of a `require()`/`import` statement, **use** the `raw-loader` to transform it before you add it to the bundle."
```

## Plugins

[plugin interface](https://webpack.js.org/api/plugins)

- Bundle optimization
- Asset management
- Injection of Environment variables
- other things!

`require()` and add to `plugins` array. Create a plugin instance with `new`.

**webpack.config.js**
```javascript
const HtmlWebpackPlugin = require('html-webpack-plugin');
const webpack = require('webpack'); //to access built-in plugins

module.exports = {
  module: {
    rules: [{ test: /\.txt$/, use: 'raw-loader' }],
  },
  plugins: [new HtmlWebpackPlugin({ template: './src/index.html' })],
};

// the `html-webpack-plugin` generates an HTML file for your application and automatically injects all your generated bundles into this file.
```

## Mode

```javascript
module.exports = {
  mode: 'production',
};
```

Set `mode` to either `development`, `production`, or `none`. Default: `production`.