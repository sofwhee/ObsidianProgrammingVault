Favor composition over inheritance.

Some think inheritance is a terrible pattern and should never be used.

In JavaScript, you can use a combination of:
- Make a bunch of functions to assign to objects.
- `Object.assign()` those functions where needed.

```javascript
dog           = pooper + barker
cat           = pooper + meower
cleaningRobot = driver + cleaner
murderRobot   = driver + killer
murderRobotDo = driver + killer + barker
```

```javascript
const barker = (state) => ({
	bark: () => console.log('Woof, I am ' + state.name)
})

const driver = (state) => ({
	drive: () => state.position = state.position + state.speed
})

// etc
```

```javascript
const murderRobotDog = (name) => {
  let state = {
	  name,
	  speed: 100,
	  position: 0
  }

  return Object.assign(
    {},
    barker(state),
    driver(state),
    killer(state)
    )
}
```