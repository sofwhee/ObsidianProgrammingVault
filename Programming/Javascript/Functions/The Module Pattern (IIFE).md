The pattern of wrapping a factory function inside an [[IIFE (immediately invoked function expression)]]

Simple example:
```javascript
const calculator = (function () {
  const add = (a, b) => a + b;
  const sub = (a, b) => a - b;
  const mul = (a, b) => a * b;
  const div = (a, b) => a / b;
  return { add, sub, mul, div };
})();

calculator.add(3,5); // 8
calculator.sub(6,2); // 4
calculator.mul(14,5534); // 77476
```

Syntax:
```javascript
const SomeModule = (function( ) { 
	// variables
	let aVariable = value;
	let anArray = array;
	let anObject = anObject;
	
	// functions
	const someFunction = (args) => {
		// function code...
		return result
	};

	const anotherFunction = () => {
		// more code
	}

	return {
		someFunction,
		anotherFunction,
		aVariable,
		anArray,
		anObject
	}
}) ();
```

**accessing a module is actually accessing whatever it returns**.

```javascript
const Formatter = (function() {
  const log = (message) => console.log(`[${Date.now()}] Logger: ${message}`);

  const makeUppercase = (text) => {
    log("Making uppercase");
    return text.toUpperCase();
  };  

  return {
    makeUppercase,
  }
})();

console.log(Formatter.makeUppercase("tomek"));
// Start
// [15515124125] Logger: Making uppercase
// TOMEK
```