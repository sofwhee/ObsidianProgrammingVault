https://javascript.info/promise-basics

**Promises** are a way to write async code that still appears as though it is executing in a top-down way, and handles more types of errors due to encouraged use of `try/catch` style error handling.

`promise` "loads" an object, `then` "fires" the object out (to microtask queue).
## Analogy

Imagine that you’re a top singer, and fans ask day and night for your upcoming song.

To get some relief, you promise to send it to them when it’s published. You give your fans a list. They can fill in their email addresses, so that when the song becomes available, all subscribed parties instantly receive it. And even if something goes very wrong, say, a fire in the studio, so that you can’t publish the song, they will still be notified.
## `promise`

A method of telling the program to wait until an async function is finished.
A promise is an object that may produce a value at some point in the future when called.

``` javascript
var promiseVar = new Promise(function(resolve, reject)) {

	if(promiseFunctionResolveCondition) {
		resolve('Success!);
	}
	else {
		reject('Shit!');
	}
}
```

## `then`

```javascript
promiseVar.then(function(result)) {
	// do stuff with 'result'
}).catch(function() {
	// error :(
}).finally(function() {
	// executes regardless of success or failure
});
```

![[Pasted image 20250505123045.png]]
## Example

```javascript
const myData = getData() // if this is refactored to return a Promise...

myData.then(function(data){ // .then() tells it to wait until the promise is resolved
  const pieceOfData = data['whatever'] // and THEN run the function inside
})
```

## Visualizations

https://www.youtube.com/watch?v=Xs1EMmBLpn4

![[Pasted image 20250505124405.png]]![[Pasted image 20250505124850.png]]