Open to extension.
Closed to modification.

Allows its behaviour to be extended without modifying its source code.

Don't **always** do this, it would be way "too much". (Too much of what? idk)

#### How?

If you have too many conditionals for a piece of logic, try breaking off those conditionals into their own Classes / Functions / Modules.

### Example

Questions are objects in an array. 
Unique logic for each one is held inside `printQuiz`.

To follow Open/Close, we want `printQuiz` to do just one thing, and the objects to handle the unique logic within themselves rather than exporting it to the function.

**Before:**

```javascript
function printQuiz(questions) {
	switch (question.type) {
		// print question.description
		case 'boolean':
		// distinct logic
		case 'multipleChoice':
		// distinct logic
		case 'text':
		// distinct logic
	}
}
```

```javascript
const questions = [{ type: 'boolean' }, { type: 'multipleChoice'}, //...]
```

**After:**

```javascript
function printQuiz(questions) {
	questions.forEach(question => {
		question.printQuestionChoices()
	})
}
```

```javascript
Class BooleanQuestion {
	// unique logic
}

Class MultipleChoiceQuestion {
	// unique logic
}

const questions = [
	new BooleanQuestion('boolean question description'),
	new MultipleChoiceQuestion('description', ['arf', 'meow', 'wan']),
	// etc...
]
```