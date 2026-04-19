Website-wide reusable CSS code.

```
@mixin stuff-i-want {
	color: red;
	border: black;
}
```

With variables:
```
@mixin bordered($color, $width) {
	border: $width solid $color;
}

.myArticle {  
	@include bordered(blue, 1px);  // Call mixin with two values
}  
  
.myNotes {  
	@include bordered(red, 2px); // Call mixin with two values
}
```

Include:
```
.charinfo {
	@include stuff-i-want;
	background-color: green;
}
```

