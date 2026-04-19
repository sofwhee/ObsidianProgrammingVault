1. `npm install --save-dev jest`
2. `<filetotest>.test.js` Make a jest file for a JS file.
3. `package.json` addition:
```javascript
{  
	"scripts": {  
	"test": "jest --verbose"  
	}  
}
```

4. `npm test` and Jest will print a message.

## Add Types

`npm install @types/jest --save-dev`
`touch jsconfig.json`
```javascript
{
	"typeAcquisition": { "include": [ "jest" ] }
}
```

## Wallaby.JS

A paid vscode extension that tells you if tests are passing without looking at terminal!?

![[Pasted image 20250201143235.png]]
## Jest with Webpack

https://jestjs.io/docs/webpack
### Static Assets

**Images**:
	If the project requires `<filetype>`, replace it with what's in `fileMock.js` (`'test-file-stub'`)
**Stylesheets:**
	if the project requires `<extension>`, replace it with `styleMock.js` (`'{}'`)

**jest.config.js**
```javascript
module.exports = {
  moduleNameMapper: {
  // If the project requires one of these filetypes...
  // replace it with what's in fileMock.js ('test-file-stub')
    '\\.(jpg|jpeg|png|gif|eot|otf|webp|svg|ttf|woff|woff2|mp4|webm|wav|mp3|m4a|aac|oga)$':
      '<rootDir>/__mocks__/fileMock.js',
  // if the extension is css or less, call styleMock.js
    '\\.(css|less)$': '<rootDir>/__mocks__/styleMock.js',
  },
};
```

**__mocks__/styleMock.js**
`module.exports = {};`

**__mocks__/fileMock.js**
`module.exports = 'test-file-stub';`

### Mocking CSS Modules

#### `identity-obj-proxy`

`identity-obj-proxy` forces anything that calls `style.<nameofstyle>` to return its own name.
(eg, `styles.foobar === 'foobar'`)

`npm install --save-dev identity-obj-proxy`

**jest.config.js**
```javascript
module.exports = {
  moduleNameMapper: {
    '\\.(jpg|jpeg|png|gif|eot|otf|webp|svg|ttf|woff|woff2|mp4|webm|wav|mp3|m4a|aac|oga)$':
      '<rootDir>/__mocks__/fileMock.js',
    '\\.(css|less)$': 'identity-obj-proxy',
  },
};
```

#### Jest transform

A transformer returns the base name of a file (`require('logo.png');` returns `'logo'`)

### Configuring Jest to Find our Files

Configure `moduleDirectories` and `moduleFileExtensions`.

For webpack's `modules`, and `extensions` options there are direct analogs in Jest's `moduleDirectories` and `moduleFileExtensions` options.

`<rootDir>` is a special token that gets replaced by Jest with the root of your project.

**jest.config.js**
```javascript
module.exports = {
  modulePaths: ['/shared/vendor/modules'],
  moduleFileExtensions: ['js', 'jsx'],
  moduleDirectories: ['node_modules', 'bower_components', 'shared'],

  moduleNameMapper: {
    '\\.(css|less)$': '<rootDir>/__mocks__/styleMock.js',
    '\\.(gif|ttf|eot|svg)$': '<rootDir>/__mocks__/fileMock.js',

    '^react(.*)$': '<rootDir>/vendor/react-master$1',
    '^config$': '<rootDir>/configs/app-config.js',
  },
};
```