To save you from having to manually edit your config every time you want to switch moves...
You can have two different configuration files.

`webpack.dev.js` `webpack.prod.js`

Then have your build and dev [[Package JSON (or npm) scripts]] specify which config files to use.
(`--config` searches for `webpack.config.js` )

```json
"build": "webpack --config webpack.prod.js",
"dev": "webpack serve --config webpack.dev.js"
```