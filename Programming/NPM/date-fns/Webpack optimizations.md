You can remove unused language from dynamic import.

Use ContextReplacementPlugin. https://webpack.js.org/plugins/context-replacement-plugin/

## Example

- Your config.js file exports a list of the supported locales for your project
- `export const supportedLocales = ["en-US", "de", "pl", "it"];`
- Then you have a function that takes one of those locales, and runs an import function where the .js filename is the locale provided. 
- (in this case it replaces a javascript filename at the end of the filepath.)
- (`date-fns-locale/locale/${locale}.js').
- (make sure to find out where YOUR locales are kept so you write this import correctly!)
- Then, in `webpack.config.js` 
	- you import the list of supported locales from `config.js`
	- export a default config that resolves to an alias "date-fns-locale" 
	- provide the path
	- then provide the plugin ContextReplacementPlugin, doing stuff I don't understand!

In this example, you have a single place where the supported locales sit.

in `config.js`
```javascript
// `see date-fns/src/locale` for available locales 
export const supportedLocales = ["en-US", "de", "pl", "it"];
```

We could also have a function that formats the date:

```javascript
const getLocale = (locale) => import(`date-fns-locale/locale/${locale}.js`); // or require() if using CommonJS

const formatDate = (date, formatStyle, locale) => {
  return format(date, formatStyle, {
    locale: getLocale(locale).default,
  });
};
```

`webpack.config.js`
```javascript
import webpack from "webpack"; import { supportedLocales } from "./config.js"; 
export default config = { 
	resolve: { 
		alias: { 
			"date-fns-locale": path.dirname(require.resolve("date-fns/package.json")), 
		}, 
	}, 
	plugins: [ 
		new webpack.ContextReplacementPlugin(
			/date-fns[/\\]locale/, 
			new RegExp(`(${locales.join("|")})\.js$`), 
		), 
	], 
};
```
