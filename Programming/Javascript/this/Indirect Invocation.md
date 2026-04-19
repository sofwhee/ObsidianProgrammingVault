Calling a function using its object methods. ([[Functions are Objects]])

Use `function.call` or `function.apply` to set `this` value.

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

