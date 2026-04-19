We don’t just need one new package for CSS, we need _two_.

```bash
npm install --save-dev style-loader css-loader
```

`css-loader` will read any CSS files we import in a JavaScript file and store the result in a string.

`style-loader` then takes that string and actually adds the JavaScript code that will apply those styles to the page.

in our `webpack.config.js`, we need to add these loaders so Webpack knows what to do.

Since these aren’t plugins, they go in a separate section:

(All this does is tell Webpack that if it encounters an imported file ending with `.css`, it should use the listed loaders to process that CSS file.)

we put `css-loader` **at the end** of the array. We **must** set this order and not the reverse.

Webpack will run the loaders starting at the end, so we want it to read the CSS file into a string with `css-loader` first, then use `style-loader` to inject the JavaScript that applies the CSS in that string to the page. It wouldn’t work the same the other way round.

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
  module: {
    rules: [
      {
        test: /\.css$/i,
        use: ["style-loader", "css-loader"],
      },
    ],
  },
};
```

You can now import your CSS file into one of your JavaScript files.

We don’t need anything from the imported CSS file itself. Since our CSS and style loaders will handle all of that for us, we can just use a [side effect import](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import#import_a_module_for_its_side_effects_only).

```javascript
import "./styles.css";
import { greeting } from "./greeting.js";

console.log(greeting);
```

bundle with Webpack using `npx webpack`, then open `dist/index.html`

we don’t link our CSS file in our HTML template like we would’ve done before.

Eventually, it becomes easier to work with multiple smaller CSS files that you import in the modules they’re needed. There are even ways those files can be scoped only to those modules and not globally!