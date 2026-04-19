(Consider making [[Package JSON (or npm) scripts]] for each bundling tool)
( may be incomplete... )

In your project folder:

```bash
// install webpack
npm install --save-dev webpack webpack-cli

// make files
touch src/index.html src/index.js src/styles.css src/template.html

// generate dist
npx webpack

npm install --save-dev html-webpack-plugin
npm install --save-dev style-loader css-loader
npm install --save-dev html-loader
npm install --save-dev webpack-dev-server
npm install --save-dev webpack-merge

// test
npx webpack serve
```

webpack.config.js
```javascript
const path = require("path");
const HtmlWebpackPlugin = require("html-webpack-plugin");

module.exports = {
  mode: "development",
  entry: "./src/index.js",
  output: {
    filename: "index.js",
    path: path.resolve(__dirname, "dist"),
    clean: true,
  },
  devtool: "eval-source-map",
  devServer: {
    watchFiles: ["./src/template.html"],
  },
  plugins: [
    new HtmlWebpackPlugin({
      template: "./src/template.html",
    }),
  ],
  module: {
    rules: [
      {
        test: /\.(png|svg|jpg|jpeg|gif)$/i,
        type: "asset/resource",
      },
      {
        test: /\.html$/i,
        loader: "html-loader",
      },
      {
        test: /\.css$/i,
        use: ["style-loader", "css-loader"],
      },
    ],
  },
};
```

index.js
```javascript
import "./styles.css";

// webpack image bundling rules:
// need to import images in order to manipulate with JS
// example: import odinImage from "./odin.png";
```

`package.json`
```diff
  {
    "name": "development",
    "version": "1.0.0",
    "description": "",
    "main": "src/index.js",
    "scripts": {
+     "start": "webpack serve --open --config webpack.dev.js",
+     "build": "webpack --config webpack.prod.js"
    },
	...
  }
```

webpack.prod.js
```javascript
  const { merge } = require('webpack-merge');
  const common = require('./webpack.common.js');

  module.exports = merge(common, {
    mode: 'production',
   devtool: 'source-map',
  });
```

Upload to github and choose to make a gitignore from a template.

For JavaScript projects, there is a `node` template that includes `node_modules` and `dist`.