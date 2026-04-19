Complete list: https://jestjs.io/docs/expect
## Syntax:

```javascript
test('name of test', () => {  
	expect(a chosen value).toBe(result);
	// not:
	expect(a chosen value).not.toBe(result);
	// for multiple:
	expect(condition).toEqual({one: 1, two: 2});
	// loop:
	for (loop stuff) {
		expect(a + b).toBe(0);
	}
});
```

## `.not.<matcher>`

## `.toBe()`

Test exact equality.

```javascript
test('name of test', () => {  
	expect(condition).toBe(12);  
});
```

`.toBe...` types:
- Truthiness
	- `Null()`
	- `Undefined()`
	- `Defined()` opposite of `Undefined`
	- `Truthy()` 'if' statement treats as true
	- `Falsy()`
- Numerical comparisons
	- `GreaterThan()`
	- `GreaterThanOrEqual()`
	- `LessThan()`
	- `LessThanOrEqual()`
	- `CloseTo()` floating point equality (0.3 for example) 

## `.toEqual()`

Check value of an object.

Recursively checks every field of an object or array.

`toEqual` ignores 
- object keys with `undefined` properties
- `undefined` array items
- array sparseness
- object type mismatch. 

To take these into account use `toStrictEqual` instead.

## `.toMatch()` Strings

You can check strings against regular expressions.

```javascript
test('there is no I in team', () => {
  expect('team').not.toMatch(/I/);
});
```

## `.toContain()` Arrays / Iterables

Check for an item.

## `.toThrow()` Errors

The function that throws an exception needs to be invoked within a wrapping function otherwise the `toThrow` assertion will fail.

```javascript
function compileAndroidCode() {
  throw new Error('you are using the wrong JDK!');
}

test('compiling android goes as expected', () => {
  expect(() => compileAndroidCode()).toThrow();
  expect(() => compileAndroidCode()).toThrow(Error);

  // You can also use a string that must be contained in the error message or a regexp
  expect(() => compileAndroidCode()).toThrow('you are using the wrong JDK');
  expect(() => compileAndroidCode()).toThrow(/JDK/);

  // Or you can match an exact error message using a regexp like below
  expect(() => compileAndroidCode()).toThrow(/^you are using the wrong JDK$/); // Test fails
  expect(() => compileAndroidCode()).toThrow(/^you are using the wrong JDK!$/); // Test pass
});
```
