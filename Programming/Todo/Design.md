User actions
- CRUD todos / projects and all properties
- Move todos from one project to another

A To do list website.

Helps user remember stuff they wanna do.
Fast UI

# Features:

- **To do list items**
	- A todo is a box that displays a Title, a Description, a Priority level, and a due date!
	- You can CRUD them with buttons
	- Edit by clicking on the info you want to edit
	- Each is held within a project so you have different to do lists
- **Project**
	- Has a title, description, priority level, and a due date too.
	- If you delete these, they move all todo items to the default project
	- You can mode todo list items from one project to another
- **Default project**
	- Just like a project, but it is made automatically if no projects exist, and cannot be deleted

# Visual design:
- **Projects**
	- **Tabs**
		- Tabs of color-coded projects at top
		- Each tab can have a little icon that shows how high of a priority it is (no icon for normal)
		- Clicking title of a tab will open it (closed)
		- Clicking title of a tab will edit it (open)
		- When a tab is opened, it grows to cover screen in its color with an animation
			- (could be just cover with colour, then everything fades in as it populates)
	- **Content**
		- Editable project traits at top
	- **Todos area**
		- Scrollable div for todo items
		- drag and drop todos
		- holding a todo does an animation
		- letting it go does an animation and moves it wherever placed in order for todos
		- holding a todo over another project tab will open it so you can place it down in there
		- hold over Project selects Project?
- **Todos**
	- title, duedate, priority, short desc, notes on side, checkmark box
	- putting mouse over checkmark gives a low opacity checkmark
	- clicking checkmark does checkmark animation
	- then it explodes or something
	- color coded, maybe even shape designed to show priority level
	- clicking a todo opens it in an animation
	- once todo opened, all crud options are accessible

# HTML:
```html
<div id="container">
	<div id="title"></div>
	<div id="projectTabs">
		%% javascript generated %%
		<div class="tab" id="tab1"><div class="priorityGraphic"></div></div>
 		<div class="tab" id="tab2"></div>
 		<div class="tab" id="tab3"></div>
		%% end %%
	</div>
	%% js generated %%
	<div class="projectTodos">
		<div class="projectDetails">
			<div class="projectDetailsLeft">
				<div class="priorityButtons">
					<button class="priorityButton priority1"></button>
					<button class="priorityButton priority2"></button>
					<button class="priorityButton priority3"></button>
					<button class="priorityButton priority4"></button>
					<button class="priorityButton priority5"></button>
				</div>
				<button class="newTodoButton"></div>
			</div>
			<div class="projectDetailsMid">
				<div class="descBox"></div>
			</div>
			<div class="projectDetailsRight">
				<div class="dueDate"></div>
			</div>
		</div>
		<div class="todos">
			<div class="todo">
				<div class="todoLeft">
					<div class="dueDate"></div>
					<div class="checkbox"></div>
					<div class="task"></div>
				</div>
				<div class="todoMid">
					<div class="priorityButtons">
						<button class="priorityButton priority1"></button>
						<button class="priorityButton priority2"></button>
						<button class="priorityButton priority3"></button>
						<button class="priorityButton priority4"></button>
						<button class="priorityButton priority5"></button>
					</div>
				</div>
				<div class="todoRight">
					<div class="descBox"></div>
				</div>
			</div
		</div>
	</div>
	%% end %%
</div>
```
# CSS

![[Website.png]]

HTML CSS:
```html
define page-margin
(100 vh 100 vw)
<container div>
	(container height = 1/12 vh)
	(container padding top/bottom = 1/3 page-margin)
	(size of website name is static)
	<Website name container> <website name>
	(height 1/3 1/8vh, 1+1/2 page-margin)
	(flex box, space between)
	<Project tabs div>
		<class project tab id 1 (js)> <project priority graphic>
 		<class project tab id 2 (js)>
 		<class project tab id 3 (js)>
	(height 7/8 vh) 
	(margin top 0, rest page-margin, padding sides page-margin)
 	<class project todos id 1 (js)>
		(height determined by elements)
		(padding top-bottom 1/6th of 1/8vh)
		(flex)
		<project details>
			(width 1/4 of parent, so 25%)
			<left div>
				(copy from todos)
				<priority buttons>
				(need to draw)
				<new todo button>
			(width 1/2 of parent, so 50%)
			<mid div>
				<desc> 
			(width 1/4 of parent, 25%)
			<right div>		
				<due date>
		(look up how to do a scrollable window that doesn't move)
		<scrollable todos>
			(flex, space-between)
			(min-height todo-height)
			(max height based on desc box height)
			(margin-bottom todo-height)
			<todo 1 div>
				<left todo div>
					(make height not affect margins somehow)
					(width static)
					<due date div> <date> <hour>
					(height todo-height)
					(width static)
					<checkbox>
					(height todo-height)
					(width flex)
					<title>
					(width static)
					(flex, gap)
				<mid todo div>
					<priority buttons> <pri 1> <pri 2> <pri 3> <pri 4> <pri 5>
				<right todo div>
					(width static)
					<desc div>
		<scrollbar>
```

Colours:

![[Pasted image 20250316133932.png]]