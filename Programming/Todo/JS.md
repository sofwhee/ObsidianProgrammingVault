## Prepare Knowledge

#### Learn LocalStorage
12. Read about localStorage usage
13. Practice with tutorials
#### Refresh Webpack knowledge
14. Read about whether GIT commits are done when using webpack
#### Learn about interfaces (dependency inversion)
15. We plan to have our JS and external APIs (DOM) rely on our own UI logic module

## Set up

16. Make project folder
	1. index.js, styles.css, index.html
17. Set up webpack (bundler)
	1. Do all setups in [[Webpack Setup]] and then make a [[Github/Template Repositories|Template Repositories]]
18. [[Jest Setup]]
	1. [[JSDOM]]
	2. Run sample tests
		1. 1. [[Using Jest]]
		2. [[Common Jest Matchers]]
	3. tests folder
		1. index.jest.js
19. Save this all as a template or something
20. Make JS test files as expected
	2. projects.test.js
	3. todos.test.js
	4. userInterface.test.js
	5. DOMLogic.test.js
	6. etc
21. Research info that may be useful to know before starting
	1. localStorage articles and tutorials
		1. write down notes in obsidian
	2. Webpack git committing
		1. note down in obsidian
	3. Webpack commands to write down in a file
		1. save in obsidian
	4. Google and study
		1. "reddit javascript how to stop user typing when character limit reached"
		2. Dependency Inversion in Javascript
		3. Javascript Dependency Inversion Interfaces
		4. Javascript dependency inversion tutorials
		5. Javascript interfaces tutorials

**REMEMBER TO GIT COMMIT AFTER EVERY CHUNK OF CODE**
## JS
### Projects
22. ~~Start by writing tests in `projects.test.js`~~
	1. ~~Refer to [[#Create Project]]~~
	2. ~~Write all tests you want it to pass~~
	3. ~~Comment out all tests but the first~~
23. ~~Code to make tests pass in `projects.js`~~
	1. [[Composition vs Inheritance]]
	2. [[Single Responsibility]]
	3. [[Avoiding Coupling]]
	4. [[Open Closed]]

```
After writing tests for projects, I realized I need to first figure out how to test Object.assign functions.

After writing tests for objectAssignments.js, I realized I need to first test validators (userInterface)

I realize now I don't really need test validators, validations are handled by the **Constraint Validation API.**
```
#### Create Todos
24. ~~Since we want to favor composition, we could try testing out the composition tricks i learned with the robot dogs and such~~
25. ~~then testing should mostly be handled!~~
26. ~~the only new thing would be that todos show up differently in the UI, and maybe have a different character limit?~~
```
I realized I want to demonstrate knowledge of OOP here, so I will not be doing composition.
```

#### Create User Interface Logic (no DOM)
27. We want to abstract all the logic here away from APIs so we can test it easily
28. ~~TDD these functions~~
29. ~~limitStopper - function to prevent user from typing more if char limit reached~~
30. ~~validDateDrop - function to give valid date dropdown~~
31. ~~validDropDown - function to give valid dropdown options for property~~
```
These are handled by the Constraint Validation API
```

# Pause

Okay, I'm realizing I was wrong about all this. TDD was not the way to go for a lot of this because so much of this doesn't need to be tested. Or at least I did it wrong. Also, I learned that SOLID is only for OOP. Not FP. but all dev should be FPOOP according to some.

So how do I do it right?

Well, what do I *want* to test?

Let's break it down more!

## Break it down more

Todo object
3. props
Project object
4. props
DOM logic without DOM interactions (DOM logic module?)
5. Create
6. Read
7. Update
8. Delete