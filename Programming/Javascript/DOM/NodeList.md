
`Array.from()` or [[spread operator]] will turn the NodeList into an array if you need one.

`.forEach`

```javascript
const node = document.createElement("div");
const kid1 = document.createElement("p");
const kid2 = document.createTextNode("hey");
const kid3 = document.createElement("span");

node.appendChild(kid1);
node.appendChild(kid2);
node.appendChild(kid3);

const list = node.childNodes;

list.forEach(function (currentValue, currentIndex, listObj) {
  console.log(`${currentValue}, ${currentIndex}, ${this}`);
}, "myThisArg");
```

```
[object HTMLParagraphElement], 0, myThisArg
[object Text], 1, myThisArg
[object HTMLSpanElement], 2, myThisArg
```