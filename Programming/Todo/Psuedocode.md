# Project Tabs

Messy version:

- make tab divs
- need to know how many projects to make tabs for
- find out how many projects there are
- store projects in a list
- for each project in list, make a tab div
- "make a tab div" should be a function
	- function:
		- make a div with class "tab"
		- give project a graphic div inside based on its priority
			- project needs to have multiple traits associated with it that can be ref'd
			- make a project class with traits
			- whenever a project is made, make it with class and store it in list
			- need a list of graphics that coincide with different priority levels
				- graphics should be svgs
		- graphic should be an img maybe?
			- research what type of div this kind of icon should be
		- if priority is normal then show = none? maybe?
- "make all tab divs" should be a function so it can be reused when needed maybe?
- or maybe i shouldn't make functions unless absolutely necessary, for composition's sake
- the less nesting, the better
- grab projectTabs div
- put tab divs in projectTabs div
- maybe i should write down my thought process in a file
	- I thought about going with OOP, but i've been reading a lot about composition over inheritance, and wanted to practice that instead
	- Functional programming + OOP seems like something that is often suggested by respected web developers, so I decided FPOOP would be interesting, and not just because it's a funny name (because it is).
	- I considered the value of OOP for making testable code
	- I read up on modern philosophies regarding testing in programs
	- It seems like the advice is to test wisely, rather than going for full coverage
	- generally the amount of usefulness for tests seems to be relative to the complexity of the operation, the more complex the operation, the more useful it might be to test
	- on the other hand, end-to-end tests can be unreliable because many variables can change in a way that are hard to control in a testing environment
	- still it's something to consider moving forward

Chronological version:

1. Projects CRUD (not DOM)
	1. Make class for Projects.
	2. Set up Projects DB
	3. Set up CRUD functions for Projects DB
		1. Create, Read, Update, Delete
2. function: makeDefaultProject
	- Checks if any project exists, and if not, make one with default params.
3. DOM function: makeProjectTabs
	1. Iterate through every project in DB (arg)
	2. Create a tab for each one in the DOM
		1. Make an "addProjectTab" function. (I am going to re use this for when the user decides to add one themselves during website usage)
			1. Args: destDiv(element) projectNumber(number)
			2. Create div. Class "tab". Id "tab(integer)" (arg)
			3. Inside the div, add an img(?) element with class "priorityIcon".
				1. Add CSS class "priority(whatever)"
				2. Apply SVG assets via said class
				3. Get SVG assets for use here
			4. Append div to original element (arg)
		2. for each one, addProjectTab(destDiv, projectNumber)
4. DOM functions for Project CRUD
	1. Design all CRUD buttons
	2. Create
		1. "Create New +" text in dark grey
		2. A transparent projectTab with no project functionality
		3. Sits inside projectTabs div
		4. Hovering highlights it
		5. Clicking brings up a form to create a new Project
			1. Create a function that builds this form (createProjectForm)
			2. takes destDiv(element) as arg
			3. look up form stuff to make div with
			4. make event listeners
				1. no need for reusable functions yet
				2. try to keep code local and tolerate repetition for readability
			5. Submitting with valid info will create a new tab, close the form, and make it the active project
	3. Read
		1. Clicking a tab will open it up and update the page with its info
		2. might want tests for this one
	4. Update
		1. You can edit anything by clicking on it while the project page is up
		2. Pressing enter will submit it and update the page
		3. Likely will need to use localStorage
		4. good idea to research this before writing this bit
	5. Delete
		1. X button on the right side of project tab
		2. clicking it runs an event which deletes project in DB, updates website elements, and selects the next project
		3. will need to research updating website elements. maybe local storage?

# Project Todos and Details

Messy Version:
- function makeProjectTodosElement(project)
- make projectTodos element
	- let projectTodosElement = create div, class "projectTodos"
	- let projectDetailsElement = create div, class "projectDetails"
	- Create projectDetailsLeft, projectDetailsMid, projectDetailsRight elements and fill them up with stuff, then append them to projectDetails Element
	- For projectDetailsLeft:
		- let projectDetailsLeftElement = create div, class "projectDetailsLeft"
		- let priorityButtonsElement = create div, class "priorityButtons"
		- for loop 5 times where i = loop number
			- let priorityButtonElement = create button, class "priorityButton priority#{i}"
			- priorityButtonsElement.append(priorityButtonElement)
		- let newTodoButtonElement = create button,  class "newTodoButton"
		- projectDetailsLeftElement.append(priortyButtonsElement, newTodoButtonElement)
	- projectDetailsMid:
		- let projectDetailsMidElement = create div, class "projectDetailsMid"
		- let descBoxElement = create div, class "descBox"
		- descBoxElement.innerText = project.desc
	- projectDetailsRight:
		- dueDate div
			- populate its date with Project.dueDate
			- event listener to be editable with clicking
- todos div
	- Project.todos.forEach
	- todo div
		- todoLeft, todoMid, TodoRight
		- todoLeft
			- dueDate div
				- populate its date with todo.dueDate
				- event listener to be editable with clicking
			- checkBox div
				- event listener to delete todo (in DOM and database and project.todos)
			- task div 
				- populate with task name
				- event listener to edit with clicking
		- todoMid
			- Priority buttons again
		- todoRight
			- descBox for todo.desc this time

Research:
Event listener to edit with clicking
Make page update everything if something is changed (React?)

Chronological version:

# Simulation in Psuedocode

Version 1. No animations. No hovers.

Page loads
Title loads
- Needs a title div
- add title div into HTML with title of website in text
- research what type of element div should be
- styling: refer to CSS obsidian notes
Project tabs load
- find list of projects
- if it's empty, make a blank project
- for each project that exists, make a tab for it
- always have a project priority icon bubble. if it's normal priority, CSS stylings will make it display none
- icon bubbles should not change behavior in CSS of anything outside of them. they should be outside project flow
Project details elements load
- this is going to be a bunch of elements which provide details of the project associated with the project's tab, and also can be edited with clicks as if it were an active form.
- When a different project tab is selected, the elements will empty and be refilled by the details of the next project. The background will change colour to the same as the project tab selected.
- copy the HTML from the obsidian project to the real one
- load the first project's values into the elements
Select another project tab
- load the project's values into the elements
- change the element's colour to the project's color
New project button
- placed to the left of first project tab
- clicking opens a form
- close button and submit button
- submit creates a new project, new project tab, closes form, and selects new project tab
Edit project title
- when project is open, clicking on the tab again will allow you to rename it
- pressing enter will submit the new name
- look up how to do this online
Edit project description
- same