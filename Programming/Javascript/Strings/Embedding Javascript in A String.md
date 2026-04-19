Inside a template literal (backticks \` ), you can wrap JavaScript variables or expressions inside `${ }`, and the result will be included in the string:

```javascript
const name = "Chris";
const greeting = `Hello, ${name}`;
console.log(greeting); // "Hello, Chris"
```