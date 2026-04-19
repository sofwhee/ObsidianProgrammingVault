![[Website.png]]

## HTML CSS:
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