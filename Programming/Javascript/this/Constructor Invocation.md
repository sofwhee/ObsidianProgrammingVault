(Using `new` on an [[Creating an Object|Object Constructor]])

`this` is set to the newly created object.

```javascript
function Car(brand) {
    this.brand = brand; // this === carobject
}

Car.prototype.getBrand = function () {
    return this.brand; // carobject.brand
}

let carobject = new Car('Honda');
console.log(carobject.getBrand()); // called by object instance, so `this` = carobject
```
