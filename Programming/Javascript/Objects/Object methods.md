#### `object`.valueOf() 

Get an object's description.

```javascript
player1.valueOf(); // Output: Object { name: "steve", marker: "X", sayName: sayName() }
```

#### `Object`.entries(object1)

Get an iterable key-value array of an object's properties.

```javascript
const object1 = {
  a: 'somestring',
  b: 42,
};

for (const [key, value] of Object.entries(object1)) {
  console.log(`${key}: ${value}`);
}

// Expected output:
// "a: somestring"
// "b: 42"
```

#### `object`.hasOwnProperty('valueOf')

Check if a given method originates within the object.

```javascript
player1.hasOwnProperty('valueOf'); // false
Object.prototype.hasOwnProperty('valueOf'); // true
Object.prototype.hasOwnProperty('hasOwnProperty'); // true
```