Inside an object's method, `this` returns the object itself.

```javascript
let car = {
    brand: 'Honda',
    getBrand: function () {
        return this.brand;
    }
}

console.log(car.getBrand()); // Honda
```
