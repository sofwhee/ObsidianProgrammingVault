ES6
```javascript
function Car(brand) {
    if (!new.target) {
        throw Error('Must use the new operator to call the function');
    }
    this.brand = brand;
}
```

Old
```javascript
function Car(brand) {
    if (!(this instanceof Car)) {
        throw Error('Must use the new operator to call the function');
    }
    this.brand = brand;
}
```