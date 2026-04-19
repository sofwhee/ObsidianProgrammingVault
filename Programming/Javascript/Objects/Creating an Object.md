
Object Constructor function:

```javascript
function Player(name, marker) {
  this.name = name;
  this.marker = marker;
}
```

Make an object by calling the Object Constructor function with `new` and putting its returned object into a variable.

```javascript
const player = new Player('steve', 'X');
console.log(player.name); // 'steve'
```

You can define an object with a constant instead of a function
(suboptimal, don't do this)

```javascript
const playerOne = {
  name: "tim",
  marker: "X"
};

const playerTwo = {
  name: "jenn",
  marker: "O"
};
```