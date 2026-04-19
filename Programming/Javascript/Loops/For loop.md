```Javascript
for (let step = 0; step < 5; step++) {
  // Runs 5 times, with values of step 0 through 4.
  console.log("Walking east one step");
}
```


## .forEach

Best use for arrays.

```javascript
const array1 = ['a', 'b', 'c'];

array1.forEach((element) => console.log(element));

// Expected output: "a"
// Expected output: "b"
// Expected output: "c"

const items = ["item1", "item2", "item3"];
const copyItems = [];

// before
for (let i = 0; i < items.length; i++) {
  copyItems.push(items[i]);
}

// after
items.forEach((item) => {
  copyItems.push(item);
});
```

## For ... in

Iterates through a specified enumerable property of an object. (usually user-made)

```javascript
for (variable in object)
  statement
```

``` javascript
for (tires in car) ...
```

Preferably not used for arrays, as it will include any properties you add to them.

```javascript
const arr = [3, 5, 7];
arr.foo = "hello";

for (const i in arr) {
  console.log(i);
}
// "0" "1" "2" "foo"
```
## For ... of

Iterates over iterable objects (including Array, Map, Set, arguments object and so on).

```javascript
for (variable of iterable) ...
```

If used on arrays...

```javascript
const arr = [3, 5, 7];
arr.foo = "hello";

for (const i of arr) {
  console.log(i);
}
// Logs: 3 5 7
```