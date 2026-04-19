- The arrow function does not create its own execution context. 
- It inherits `this` from the outer function.

```javascript
let getThis = () => this;
console.log(getThis() === window); // true
```