```Javascript
splice(start)
splice(start, deleteCount)
splice(start, deleteCount, item1)
splice(start, deleteCount, item1, item2)
splice(start, deleteCount, item1, item2, /* …, */ itemN)
```

```javascript
const months = ['Jan', 'March', 'April', 'June'];
months.splice(1, 0, 'Feb');
// Inserts at index 1
console.log(months);
// Expected output: Array ["Jan", "Feb", "March", "April", "June"]

months.splice(4, 1, 'May');
// Replaces 1 element at index 4
console.log(months);
// Expected output: Array ["Jan", "Feb", "March", "April", "May"]
```

[`deleteCount` Optional](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice#deletecount)

An integer indicating the number of elements in the array to remove from `start`.

If `deleteCount` is omitted, or if its value is greater than or equal to the number of elements after the position specified by `start`, then all the elements from `start` to the end of the array will be deleted. However, if you wish to pass any `itemN` parameter, you should pass `Infinity` as `deleteCount` to delet, 1e all elements after `start`, because an explicit `undefined` gets [converted](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number#integer_conversion) to `0`.

If `deleteCount` is `0` or negative, no elements are removed. In this case, you should specify at least one new element (see below).

[`item1`, …, `itemN` Optional](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice#item1)

The elements to add to the array, beginning from `start`.

If you do not specify any elements, `splice()` will only remove elements from the array.

### [Return value](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice#return_value)

An array containing the deleted elements.

If only one element is removed, an array of one element is returned.

If no elements are removed, an empty array is returned.