```javascript
delete arr[1]
```

****Example 3:**** In this example, delete arr[0] removes the element at index 0, leaving an empty slot. The array retains its original length, but index 0 is now undefined.

```javascript 
let arr = [1, 2, 3]  console.log(delete arr[0]); //true console.log(arr); //[empty, 2, 3]     
```