1. [[CommonJS]] exports, not ES6 exports in your files.
	1. `"module.exports = <thing>"` not `export { <thing> }`
2. Make sure `package.json` is set up with "test".
```javascript
"scripts": {
	"test": "jest"
}
```
3. Make a Tests folder in root directory
4. Make a `filename.ttesest.js` to match the file to test.
5. `npm test`

Syntax: 

```javascript
const sum = require('../src/sum');
// test / it
test('adds 1 + 2 to equal 3', () => {
  expect(sum(1, 2)).toBe(3);
});
```

```javascript
// this will run
test('adds 1 + 2 to equal 3');
// this will hold off on test
test.todo('adds 1 + 2 to equal 3');
```

```javascript
describe('My function', () => {

	// tests..

})
```

```javascript
beforeEach(() => {  
return initializeCityDatabase();  
});
```