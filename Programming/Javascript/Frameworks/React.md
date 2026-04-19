Build reusable components simply.

# Summary
## Component

In React, it is a JavaScript function that returns HTML through the JSX syntax.

```Javascript
function Item() {
 return <p></p>
}
```

If you want to pass data into a **component** you use...

### Props

```Javascript
function Item(props) {
// use { } to pass data in with props
 return <p>{ props.text }</p>
}
```

## Reactivity

If the value of the **props** changes, React code will "react" to update the UI.

## Hook

Give a component its own **internal state.**

A hook is a function that returns two things...
- A value
- A function to change that value

```Javascript
import { useState } from 'react';

function Item() {
	// count = read (reactive state)
	// setCount = write (will change the state)

	// In the template, count will always show the most recent value.
	// Can bind setCount to a button or something so User can change count's state.
	const [count, setCount ] = useState(0);

}
```

React has plenty of **built-in hooks** to handle common use cases.

# Online Component Library

**Gatsby** - Need a static site?
**Next.js** - Need Server-side-Rendering?
**Spring** - Animation!
**Formik** - Forms!
**State management** - Redux, MOBX, FLUX, Recoil, XState...
**React Native** - Mobile apps!