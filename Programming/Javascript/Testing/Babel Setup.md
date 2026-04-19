`npm install --save-dev babel-jest @babel/core @babel/preset-env`

Configure Babel to target your current version of Node by creating a `babel.config.js` file in the root of your project:

```javascript
module.exports = {  
	presets: [['@babel/preset-env', {targets: {node: 'current'}}]],  
};
```

## Using with webpack

you'll need to add `@babel/preset-env` like so:

`npm install --save-dev @babel/preset-env`

**.babelrc**
```javascript
{  
	"presets": ["@babel/preset-env"]  
}
```

If you updated `.babelrc` and Jest is not working as expected, try clearing the cache by running `jest --clearCache`.

If you use dynamic imports (`import('some-file.js').then(module => ...)`), you need to enable the `dynamic-import-node` plugin.

```javascript
{
  "presets": [["env", {"modules": false}]],

  "plugins": ["syntax-dynamic-import"],

  "env": {
    "test": {
      "plugins": ["dynamic-import-node"]
    }
  }
}
```