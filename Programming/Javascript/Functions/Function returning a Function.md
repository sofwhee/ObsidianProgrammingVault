A **"pause button"** in a function. A **"saved state"**. "**Press play**" by calling it again!.

If you return a function, you have essentially "paused" the function.
Everything, variables declared, calculations done, are in a "saved state"

```javascript
function makeAdding (firstNumber) {
  // "first" is scoped within the makeAdding function
  const first = firstNumber;
  return function resulting (secondNumber) {
    // "second" is scoped within the resulting function
    const second = secondNumber;
    return first + second;
  }
}
// but we've not seen an example of a "function"
// being returned, thus far - how do we use it?

const add5 = makeAdding(5);

// "add5" is now like a loaded gun without a bullet.
// it's the function "resulting" waiting for its (secondNumber) arg

// Think about it like pressing pause on a function and waiting for a new input...
console.log(add5(2)) // logs 7
```