Functions are object instances of the Function type.

`Function.call()`
`Function.apply()`

Let you set the `this` value when calling a function.

```javascript
function getBrand(prefix) {
    console.log(prefix + this.brand);
}

let honda = {
    brand: 'Honda'
};
let audi = {
    brand: 'Audi'
};

getBrand.call(honda, "It's a "); // It's a Honda
getBrand.call(audi, "It's an "); // It's an Audi

getBrand.apply(honda, ["It's a "]); // "It's a Honda"
getBrand.apply(audi, ["It's an "]); // "It's a Audi"
```