## Habit
- Set break timers
- Open linux, project, CSS HTML JS
- Find where you left off (read most recent note. if not present, look at website and decide what to do next from top down in elements list)
- Write down thing you want to do
	- break it down into steps until you don't know what the next step is
	- write pseudocode
- do thing
- git commit
- repeat writing down, doing thing, and git commit until time is out or project done

## Notes

Revisit chrome tips from fireship
think about what YOU would want from a todo website.

Figure out how to make date objects
figure out how to make duedate dropdowns

date format:

WED
FEB 4

WED FEB 4

Feb 4 Wed

if over one year away, replace day with year

Feb 4 2026

```javascript
const result = format(new Date(2025, 3, 19, 14), "MMM d E..EEE")
//=> "FEB 4 Wed"

// if date is 1+ year away
const result = format(new Date(2025, 3, 19, 14), "MMM d yyyy")
//=> "FEB 4 2025"

// if date is today
const result = isToday(new Date(2025, 3, 19, 14)) //=> true
const result = format(new Date(2025, 3, 19, 14), "p")
// => "2:00 PM"

// if date is tomorrow
const result = isToday(new Date(2025, 3, 19, 14)) //=> true
const result = format(new Date(2025, 3, 19, 14), "'Tomorrow' p")
// => "Tomorrow 2:00 PM"

// if date is yesterday
const result = isYesterday(new Date(2025, 3, 19, 14)) //=> true
const result = format(new Date(2025, 3, 19, 14), "'Yesterday' p")
// => "Yesterday 2:00 PM"

// if date is past
// turn it red
```

Consider writing more useful notes if you can't find what you need.

Gallery website

3/27/2025

- ~~Figure out where i Left off~~
- ~~reading the list~~
- ~~struck off stuff i did~~
- ~~going to do step 9~~
- ~~oh no, need to start website but forgot how~~
- ~~it's an npm script~~
- ~~made bookmarks to more easily reach notes in obsidian~~
- ~~read npm scripts so i know how to test website by running it~~
- Fill out DOM with javascript-made elements
- Elements yet to be made:
	- ~~Project Tab priority icons~~
		- Project Tab Titles spacing is weird, wish I could take the tabIcons out of the flex flow so titles could fill up their tabs fully
		- Tab Titles should shrink in size the longer they are, and/or have a char limit
	- ~~Date on right side of project details~~
		- ~~make the element in the right place~~
		- ~~make its contents~~
		- ~~style to look right~~
	- ~~Description box~~
		- ~~populate with desc~~
		---- current point ---
	- ~~Todo list~~
		- ~~fix priority buttons element not fitting icons in it~~
		- ~~todos work. now style desc boxes a bit more~~
- ~~How to make date on right side of project details~~
	- ~~make the element show up by drawing from project's date variable~~


4/26/2025

7/11/2025

- Go down the list of buttons on page from top-bottom left-right, giving them event handlers that do stuff
	- ~~For project tabs, make async function that says "if project tab is active, clicking on the tab again will make the title editable"~~
	- Figured out something better!

- figure out how to clean up my addEventHandler stuff. It's cluttering up everything and making it hard to deal with...
- can't seem to figure out how to DRY with add event handlers.