1. Run the following command to install HtmlWebpackPlugin (also as a dev dependency):

```bash
npm install --save-dev html-webpack-plugin
```

2. Create a `template.html` inside `src` (you can name this file whatever you want)

3. Inside our `webpack.config.js` make sure our Webpack configuration has access to HtmlWebpackPlugin
4. Add it as a plugin to the configuration object. 

5. Inside the HtmlWebpackPlugin constructor call, we pass in any options. For now, we’re only interested in the `template` option.
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
  plugins: [
    new HtmlWebpackPlugin({
      template: "./src/template.html",
    }),
  ],
};
```

6. If we provide the path to our src/template.html file as a template, when we run npx webpack again, you’ll notice our dist directory not only contains a main.js file but an index.html file as well (it can’t combine them into one file). 
7. You’ll also notice that HtmlWebpackPlugin has automatically added a deferred script tag to our index.html file - what a darling!
8. Any changes to HTML we make, we can just rerun Webpack to generate fresh `dist` code.