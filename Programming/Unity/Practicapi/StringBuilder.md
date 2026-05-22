StringBuilder is a MUCH faster way of building strings.

Normal Strings are built together with concatenation by...
Making a new copy of the total string with each concatenation
Then bringing that copy over to each new concatenation
That's very inefficient.

StringBuilder instead, just continuously adds them to an existing string

The performance difference is huge:
If you're making a long string of 500,000 contact names
String takes 7.5 mins
StringBuilder takes 54 **seconds**.

![[Pasted image 20260503093109.png]]