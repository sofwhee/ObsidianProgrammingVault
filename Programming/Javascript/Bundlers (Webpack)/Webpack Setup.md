1. In the `terminal` set up a new directory and go inside it
```bash
mkdir webpack-practice && cd webpack-practice
```
2. Install Webpack (here it is being saved as a dev dependency)
```bash
npm install --save-dev webpack webpack-cli
```
3. A `package.json` has been created (marked as dev dependencies)
4. A `node_modules` directory has been made
	1. Where Webpacks actual code (and other stuff) lives
5. A `package-lock.json` was auto-generated
	1. Tracks specific package info
6. Work in `src`, Webpack outputs files into `dist`
7. Create a `src` directory
	1. You can put stuff like `index.js` in it.
8. In `root` (outside of `src`) make `webpack.config.js`

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

9. Run webpack so it makes a `dist` file.
```bash
npx webpack
```

[[Bundling Javascript (Webpack)]]
[[Bundling HTML (Webpack)]]
[[Bundling CSS (Webpack)]]
[[Bundling Images (Webpack)]]
[[Webpack Dev Server]]