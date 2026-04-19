#Sass 

Used to DRY within Sass files.

i.e. resets, variables, colors, fonts, font-sizes, etc.

`_colors.scss`

```
$myPink: #EE82EE;  
$myBlue: #4169E1;  
$myGreen: #8FBC8F;
```

Then to import:
```
@import "colors";

body {
	color: $myBlue;
}
```