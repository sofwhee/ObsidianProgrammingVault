```javascript
editableElement.addEventListener('click', function() {
	this.contentEditable = "true"
	this.focus() // This starts the editing on first click by focusing element
})
```

enter to exit editing

```javascript
editableElement.addEventListener('keydown', function(event) {
	// note: function(event) is required instead of function()
	// since we're referencing the event in the function
	if(event.key === 'Enter') {
		event.preventDefault() // stops it from making a newline on "enter"
		this.contentEditable = "false" // so you don't leave it typing mode
	}
})
```

save whatever you've edited to an object
(there's probably a better way to do this)

```javascript
editableElement.addEventListener('input' function() {
	object.propertyYouWannaChange = this.innerText
})
```