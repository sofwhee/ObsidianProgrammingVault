```javascript
addEventListener(type, listener)
addEventListener(type, listener, options)
addEventListener(type, listener, useCapture)
```

## Parameters?

`addEventListener` expects a function object as the callback, you instead call the function and pass its return value. You can do:

```
element.addEventListener("click", () => add_to_cart(element))
```

But you can also identify the HTML element that was clicked on using the event argument that is passed to the callback:

```
element.addEventListener("click", (e) => add_to_cart(e.target))
```

Or you can call the function within the event listener callback:

```
element.addEventListener('click', event => { add_to_cart(element) })
```

Example

```html
<table id="outside">
  <tr>
    <td id="t1">one</td>
  </tr>
  <tr>
    <td id="t2">two</td>
  </tr>
</table>
```

```javascript
// Function to change the content of t2
function modifyText() {
  const t2 = document.getElementById("t2");
  const isNodeThree = t2.firstChild.nodeValue === "three";
  t2.firstChild.nodeValue = isNodeThree ? "two" : "three";
}

// Add event listener to table
const el = document.getElementById("outside");
el.addEventListener("click", modifyText, false);
```

`type` - A case-sensitive string representing the [event type](https://developer.mozilla.org/en-US/docs/Web/Events) to listen for.

`listener` - The object that receives a notification (an object that implements the [`Event`](https://developer.mozilla.org/en-US/docs/Web/API/Event) interface) when an event of the functspecified type occurs. This must be `null`, an object with a `handleEvent()` method, or a JavaScript [function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions). See [The event listener callback](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener#the_event_listener_callback) for details on the callback itself.

`options`
 - `capture`
	 - A boolean value indicating that events of this type will be dispatched to the registered `listener` before being dispatched to any `EventTarget` beneath it in the DOM tree. If not specified, defaults to `false`.
 - `once`
	 - A boolean value indicating that the `listener` should be invoked at most once after being added. If `true`, the `listener` would be automatically removed when invoked. If not specified, defaults to `false`.
 - `passive`
	 - A boolean value that, if `true`, indicates that the function specified by `listener` will never call [`preventDefault()`](https://developer.mozilla.org/en-US/docs/Web/API/Event/preventDefault "preventDefault()"). If a passive listener calls `preventDefault()`, nothing will happen and a console warning may be generated.
	 - If this option is not specified it defaults to `false` – except that in browsers other than Safari, it defaults to `true` for [`wheel`](https://developer.mozilla.org/en-US/docs/Web/API/Element/wheel_event "wheel"), [`mousewheel`](https://developer.mozilla.org/en-US/docs/Web/API/Element/mousewheel_event "mousewheel"), [`touchstart`](https://developer.mozilla.org/en-US/docs/Web/API/Element/touchstart_event "touchstart") and [`touchmove`](https://developer.mozilla.org/en-US/docs/Web/API/Element/touchmove_event "touchmove") events. See [Using passive listeners](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener#using_passive_listeners) to learn more.
 - `signal`
	 - An [`AbortSignal`](https://developer.mozilla.org/en-US/docs/Web/API/AbortSignal). The listener will be removed when the given `AbortSignal` object's [`abort()`](https://developer.mozilla.org/en-US/docs/Web/API/AbortController/abort "abort()") method is called. If not specified, no `AbortSignal` is associated with the listener.

```javascript
function handleEvent(event) {
  if (event.type === "fullscreenchange") {
    /* handle a full screen toggle */
  } else {
    /* handle a full screen toggle error */
  }
}
```

`this` - Reference to the `element`. Same value as `currentTarget` property of `event`.

```javascript
my_element.addEventListener("click", function (e) {
  console.log(this.className); // logs the className of my_element
  console.log(e.currentTarget === this); // logs `true`
});

// arrow functions do not have their own 'this' context
my_element.addEventListener("click", (e) => {
  console.log(this.className); // WARNING: `this` is not `my_element`
  console.log(e.currentTarget === this); // logs `false`
});
```

You can specify `this` using bind().