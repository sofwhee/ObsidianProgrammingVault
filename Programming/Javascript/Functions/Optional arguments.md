```javascript
// ES6
function myFunc(a, b = 0) {
   // function body
}
```

```javascript
// ES5
function myFunc(a,b) {
  b = b || 0;

  // b will be set either to b or to 0.
}
```