- Actions that occur on your webpage, such as mouse-clicks or key-presses.
- A way to manipulate the DOM dynamically on demand.
- Using JS, we can make our webpage listen to and react to these events.
- 
There are three primary ways to go about this:

- You can specify function attributes directly on your HTML elements.
- You can set properties in the form of `on<eventType>`, such as `onclick` or `onmousedown`, on the DOM nodes in your JavaScript.
- You can attach event listeners to the DOM nodes in your JavaScript.

Event listeners are definitely the preferred method, but you will regularly see the others in use.