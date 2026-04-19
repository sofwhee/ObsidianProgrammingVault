If you wanna make code private, use factory functions.

More control over what is accessible in global scope.

```javascript
function Cell() {
  let value = 0;

  // Accept a player's token to change the value of the cell
  const addToken = (player) => {
    value = player;
  };

  // How we will retrieve the current value of this cell through closure
  const getValue = () => value;

  return {
    addToken,
    getValue
  };
}
```

A modern replacement to Constructors.

Constructors can be confusing... so these were made.
No longer need to use the `new` keyword. `instanceof` works more predictably.

```javascript
// constructor
const User = function (name) {
  this.name = name;
  this.discordName = "@" + name;
}
// factory
function createUser (name) {
  const discordName = "@" + name;
  return { name, discordName };
}

const patrick = createUser("patrick")
patrick.name // "patrick"
patrick.discordName // "@patrick"
```

[[Object Shorthand]]

Recommended when you use a single instance of an object constructor.

Prototypal inheritance:

```javascript
function createPlayer (name, level) {
  const { getReputation, giveReputation } = createUser(name);

  const increaseLevel = () => level++;
  return { name, getReputation, giveReputation, increaseLevel };
}
```

(Object.assign version)

```javascript
function createPlayer (name, level) {
  const user = createUser(name);

  const increaseLevel = () => level++;
  return Object.assign({}, user, { increaseLevel });
}
```

## Getters and Setters

Use getters to protect variables.

`getValue = () => value;`