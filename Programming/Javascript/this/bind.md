A method from `Function.prototype`.

bind( ) will...
- return a 'copy' of a function
- where `this` is set to the specified value

Syntax:

```javascript
let boundfunc = aFunction.bind(context); // returns function-like "exotic object"
```

Demo:

```javascript
let user = {
  firstName: "John"
};

function exclaim(thing) {
// this = user <-------- this is what exclaim.bind(user) does
  alert(this.firstName + 'loves' + thing);
}

let exclaimUser = exclaim.bind(user);

exclaimUser("pizza!"); // John loves pizza!
```