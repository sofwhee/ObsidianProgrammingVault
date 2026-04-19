Callback as in 'call you back later.'

Functions are **declared** immediately.
Normal functions are **invoked** immediately, from top to bottom.
Callback functions are **invoked** when a function that 'calls it back' finishes.

```javascript
myDiv.addEventListener("click", callbackFunction(){})
// all functions declared
// addEventListener finishes -> callbackFunction invoked
```

## Callback Hell

Pyramid shape.
Lots of `})`.
Happens when you write JS where execution happens visually from top to bottom.

```javascript
fs.readdir(source, function (err, files) {
  if (err) {
    console.log('Error finding files: ' + err)
  } else {
    files.forEach(function (filename, fileIndex) {
      console.log(filename)
      gm(source + filename).size(function (err, values) {
        if (err) {
          console.log('Error identifying file size: ' + err)
        } else {
          console.log(filename + ' : ' + values)
          aspect = (values.width / values.height)
          widths.forEach(function (width, widthIndex) {
            height = Math.round(width / aspect)
            console.log('resizing ' + filename + 'to ' + height + 'x' + height)
            this.resize(width, height).write(dest + 'w' + width + '_' + filename, function(err) {
              if (err) console.log('Error writing file: ' + err)
            })
          }.bind(this))
        }
      })
    })
  }
})
```

Avoid by
- Don't nest functions. Give them names and place them at the top level.
- Modularize. 
- Don't skip error handling.
- Create a module with reusable functions to reduce cognitive load, increase readability.

## Error handling
With callbacks the most popular way to handle errors is the Node.js style where the first argument to the callback is always reserved for an error.

Having the first argument be the `error` is a simple convention that encourages you to remember to handle your errors. If it was the second argument you could write code like `function handleFile (file) { }` and more easily ignore the error.

Code linters can also be configured to help you remember to handle callback errors. The simplest one to use is called [standard](http://standardjs.com/). All you have to do is run `$ standard` in your code folder and it will show you every callback in your code with an unhandled error.

```javascript
 var fs = require('fs')

 fs.readFile('/Does/not/exist', handleFile)

 function handleFile (error, file) {
   if (error) return console.error('Uhoh, there was an error', error)
   // otherwise, continue on and use `file` in your code
 }
```