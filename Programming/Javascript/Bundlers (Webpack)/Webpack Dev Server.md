`webpack-dev-server`: So you don't have to run `npx webpack` with every change.

(like the Live Preview VSCode extension, where it automatically refreshes your web page whenever you save a change.)

It works by bundling your code behind the scenes (as if we ran `npx webpack`, but without saving the files to `dist`)

It does this **every time you save a file that’s used in the bundle.**

Use a **source map** so that any error messages reference files and lines from our development code and not the jumbled mess inside our single bundled `.js` file!

By default, `webpack-dev-server` will only auto-restart when it detects any changes to files we import into our JavaScript bundle, so our HTML template will be ignored! All we need to do is add it to the dev server’s array of watched files - nice and simple!

 The webpack-dev-server only reads your webpack configuration when you start it. If you change the **webpack config file while the dev server is running**, it will not reflect those config changes. Use **Ctrl + C** in the terminal to kill it then rerun `npx webpack serve` to apply the new config.

## Install

```bash
npm install --save-dev webpack-dev-server
```

Once installed, in our `webpack.config.js`, we only need to add a couple more properties somewhere in the configuration object (the order of these properties does not matter):

```javascript
// webpack.config.js
const path = require("path");
const HtmlWebpackPlugin = require("html-webpack-plugin");

module.exports = {
  mode: "development",
  entry: "./src/index.js",
  output: {
    filename: "main.js",
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
        test: /\.css$/i,
        use: ["style-loader", "css-loader"],
      },
      {
        test: /\.html$/i,
        loader: "html-loader",
      },
      {
        test: /\.(png|svg|jpg|jpeg|gif)$/i,
        type: "asset/resource",
      },
    ],
  },
};
```

Add a **source map** by setting `eval-source-map` as a `devtool` option.

(If we don’t do this, any error messages we get won’t necessarily match up to the correct files and line numbers from our development code.)

Add HTML to the dev server’s array of watched files (if you want it to update when you change the HTML template)

Once set up, `npx webpack serve` will host our web page on `http://localhost:8080/`