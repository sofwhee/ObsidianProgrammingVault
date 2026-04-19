These all use CSS [[Selectors + Combinators]].
## Query

```javascript
// selects the .controls div
const controls = document.querySelector(".controls");

// selects nested button
const showButton = document.querySelector("dialog + button")
```

```javascript
element.querySelectorAll(selectors) // returns a NodeList
```

```javascript
document.getElementsByClassName("test");
```
## Create

```javascript
// document.createElement(tagName, [options])
const div = document.createElement("div");
```
## Append / Remove

```javascript
parentNode.appendChild(childNode) // appends childNode as last child of parentNode
```

```javascript
// inserts newNode into parentNode before referenceNode
parentNode.insertBefore(newNode, referenceNode)
```

```javascript
parentNode.removeChild(child) // removes child from parent. returns child ref
```

```javascript
parentNode.remove() // removes self
```

### Modify element properties

```javascript
// creates a new div referenced in the variable 'div'
const div = document.createElement("div");

// adds the indicated style rule to the element in the div variable
div.style.color = "blue";

// adds several style rules
div.style.cssText = "color: blue; background: white;";

// adds several style rules
div.setAttribute("style", "color: blue; background: white;");
```

``` javascript
// dot notation with kebab case: doesn't work as it attempts to subtract color from div.style.background
// equivalent to: div.style.background - color
div.style.background-color;

// dot notation with camelCase: works, accesses the div's background-color style
div.style.backgroundColor;

// bracket notation with kebab-case: also works
div.style["background-color"];

// bracket notation with camelCase: also works
div.style["backgroundColor"];
```

```javascript
// if id exists, update it to 'theDiv', else create an id with value "theDiv"
div.setAttribute("id", "theDiv");

// returns value of specified attribute, in this case "theDiv"
div.getAttribute("id");

// removes specified attribute
div.removeAttribute("id");
```

(It is often standard (and cleaner) to toggle a CSS style rather than adding and removing inline CSS.)

```javascript
// adds class "new" to your new div
div.classList.add("new");

// adds multiple classes
div.classList.add("new", "other");

// removes "new" class from div
div.classList.remove("new");

// if div doesn't have class "active" then add it, or if it does, then remove it
div.classList.toggle("active");
```

```javascript
// creates a text node containing "Hello World!" and inserts it in div
div.textContent = "Hello World!";
```

(Note that using `textContent` is preferred over `innerHTML` for adding text, as `innerHTML` should be used sparingly to avoid potential security risks.)

```javascript
// renders the HTML inside div
div.innerHTML = "<span>Hello World!</span>";
```

```javascript
div.innerText = "text"
```

data attributes

```javascript
// set data attribute
bookList.setAttribute('data-bookNumber', bookIndex)
// get data attribute
bookLIst.dataset.bookNumber; // "1"
```

```javascript
const article = document.querySelector("#electric-cars");
// The following would also work:
// const article = document.getElementById("electric-cars")

article.dataset.columns; // "3"
article.dataset.indexNumber; // "12314"
article.dataset.parent; // "cars"
```