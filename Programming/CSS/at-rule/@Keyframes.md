```css
@keyframes slide-in { 
	from { transform: translateX(0%); } to { transform: translateX(100%); } 
}
```

Define a named animation by describing defining CSS styles for intermediate steps (or keyframes) in the animation sequence

To use keyframes, create a `@keyframes` rule with a name that is then used by the [`animation-name`](https://developer.mozilla.org/en-US/docs/Web/CSS/animation-name) property to match an animation to its keyframe declaration. Each `@keyframes` rule contains a style list of keyframe selectors, which specify percentages along the animation when the keyframe occurs, and a block containing the styles for that keyframe.

You can list the keyframe percentages in any order; they will be handled in the order they should occur.

JavaScript can access the `@keyframes` at-rule with the CSS object model interface [`CSSKeyframesRule`](https://developer.mozilla.org/en-US/docs/Web/API/CSSKeyframesRule).