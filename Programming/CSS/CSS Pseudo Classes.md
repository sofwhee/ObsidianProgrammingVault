
```CSS
.joinBtn {
  width: 10em;
  height: 5ex;
  background-color: gold;
  border: 2px solid firebrick;
  border-radius: 10px;
  font-weight: bold;
  color: black;
  cursor: pointer;
}

.joinBtn:hover {
  background-color: bisque;
}
```

## [User action pseudo-classes](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes#user_action_pseudo-classes)

These pseudo-classes require some interaction by the user in order for them to apply, such as holding a mouse pointer over an element.

[`:hover`](https://developer.mozilla.org/en-US/docs/Web/CSS/:hover)

Matches when a user designates an item with a pointing device, such as holding the mouse pointer over the item.

[`:active`](https://developer.mozilla.org/en-US/docs/Web/CSS/:active)

Matches when an item is being activated by the user. For example, when the item is clicked on.

[`:focus`](https://developer.mozilla.org/en-US/docs/Web/CSS/:focus)

Matches when an element has focus.

[`:focus-visible`](https://developer.mozilla.org/en-US/docs/Web/CSS/:focus-visible)

Matches when an element has focus and the user agent identifies that the element should be visibly focused.

[`:focus-within`](https://developer.mozilla.org/en-US/docs/Web/CSS/:focus-within)

Matches an element to which [`:focus`](https://developer.mozilla.org/en-US/docs/Web/CSS/:focus) applies, plus any element that has a descendant to which [`:focus`](https://developer.mozilla.org/en-US/docs/Web/CSS/:focus) applies.