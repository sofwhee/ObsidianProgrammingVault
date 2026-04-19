HTML is responsive. **Until** you change that with CSS.
So, it's really more about *maintaining* responsiveness.

320px is as small as you need to go.

Supporting super-wide screens:
- Max width for *all* content
- Center it all on the page

Maintaining responsiveness:
- Avoid fixed width and height (try max-width, min-height)
- Avoid heights altogether
	- Except headers and footers maybe
	- use margin and padding instead
- Smaller fixed widths are probably ok. Like a 250px sidebar.
- Percentages can be problematic
	- Margins of the element will change with screen size
	- Instead, use static widths with breakpoints and flexbox to center
	- Percentages can be useful (height 100% to make child fill parent height, width 100% for elements that don't expand by default)

Responsive Images
- Suggested to just use things that automate/abstract this process.
- Don't define both a width and a height. (give flexible width and `auto` height.)
- If you don't want shrinking at all, use `background-size` and/or `object-fit`.
	- `background-size: cover` resizes the image to fill container while cropping as little as possible.
	- `object-fit` is similar, but for img tags.
		- You set a width and height, then tell an image how it's supposed to achieve that.
- For best control, just use different images for different screen sizes using the `picture` tag.
	- ``` HTML
	  <picture>
	    <source srcset="party.webp">
	    <img src="party.jpg" alt="A cake fallback for you old web browsers.">
	  </picture>
	  ```
- You can do this with img tags too though. (2x, 4x, etc, are pixel-density)
	- ```HTML
	  <img
		  alt="A baby smiling"
		  src="defaultbaby-lowres.jpg"
		  alt="baby-highres.jpg 2x">	
	  Serves different sizes of the same image.
	  ```
- You can also just use CSS to change the src of `background-image`.

![[Pasted image 20260403141320.png]]
https://css-tricks.com/a-guide-to-the-responsive-images-syntax-in-html/

Media Queries:
- You may not need any. Make as few as possible.
- Limit them
	- mobile = 500px
	- Tablet = 500-1000px
	- Normal > 1000px
	- Super wide 2000px