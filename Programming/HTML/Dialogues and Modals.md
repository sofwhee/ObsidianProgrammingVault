
**Modal dialog boxes** interrupt interaction with the rest of the page being inert. 
**Non-modal dialog boxes** allow interaction with the rest of the page.

JavaScript should be used to display the `<dialog>` element.
- Use the [`.showModal()`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLDialogElement/showModal ".showModal()") method to display a modal dialog
- [`.show()`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLDialogElement/show ".show()") method to display a non-modal dialog
- The dialog box can be closed using the [`.close()`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLDialogElement/close ".close()") method
- Close with [`dialog`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/form#method) method when submitting a `<form>` inside `<dialog>`

*(Modal dialogs can also be closed by pressing the Esc key.)*

### Creating a modal dialog

First make the dialog element...

```html
<dialog>
  <button autofocus>Close</button>
  <p>This modal dialog has a groovy backdrop!</p>
</dialog>
```

Then the button to show the dialog...

```html
<button>Show the dialog</button>
```

We can style the backdrop of the dialog by using the [`::backdrop`](https://developer.mozilla.org/en-US/docs/Web/CSS/::backdrop) pseudo-element.

```CSS
::backdrop {
  background-image: linear-gradient(
    45deg,
    magenta,
    rebeccapurple,
    dodgerblue,
    green
  );
  opacity: 0.75;
}
```

Now add JavaScript for the dialog button. 

(Here the dialog is opened modally using the `.showModal()` method and closed using the `.close()` method.)

```javascript
const dialog = document.querySelector("dialog");
const showButton = document.querySelector("dialog + button"); // sibling
const closeButton = document.querySelector("dialog button"); // descendant

// "Show the dialog" button opens the dialog modally
showButton.addEventListener("click", () => {
  dialog.showModal();
});

// "Close" button closes the dialog
closeButton.addEventListener("click", () => {
  dialog.close();
});
```

![[Pasted image 20250105142206.png]]

### ReturnValue (How to close dialog with a form)

`returnValue` is the empty string **or** the value of the button that submits the form within the `<dialog>` element, if there is one.

```html
<!-- A modal dialog containing a form -->
<dialog id="favDialog">
  <form>
    <p>
      <label>
        Favorite animal:
        <select>
          <option value="default">Choose…</option>
          <option>Brine shrimp</option>
          <option>Red panda</option>
          <option>Spider monkey</option>
        </select>
      </label>
    </p>
    <div>
      <button value="cancel" formmethod="dialog">Cancel</button>
      <button id="confirmBtn" value="default">Confirm</button>
    </div>
  </form>
</dialog>
<p>
  <button id="showDialog">Show the dialog</button>
</p>
<output></output>
```

```javascript
const showButton = document.getElementById("showDialog");
const favDialog = document.getElementById("favDialog");
const outputBox = document.querySelector("output");
const selectEl = favDialog.querySelector("select");
const confirmBtn = favDialog.querySelector("#confirmBtn");

// "Show the dialog" button opens the <dialog> modally
showButton.addEventListener("click", () => {
  favDialog.showModal();
});

// "Cancel" button closes the dialog without submitting because of [formmethod="dialog"], triggering a close event.
favDialog.addEventListener("close", (e) => {
  outputBox.value =
    favDialog.returnValue === "default"
      ? "No return value."
      : `ReturnValue: ${favDialog.returnValue}.`; // Have to check for "default" rather than empty string
});

// Prevent the "confirm" button from the default behavior of submitting the form, and close the dialog with the `close()` method, which triggers the "close" event.
confirmBtn.addEventListener("click", (event) => {
  event.preventDefault(); // We don't want to submit this fake form
  favDialog.close(selectEl.value); // Have to send the select box value here.
});
```

![[Pasted image 20250105142433.png]]
![[Pasted image 20250105142440.png]]
![[Pasted image 20250105142446.png]]

