![[Pasted image 20250115153141.png]]

DAX is good for read-heavy apps

DAX is only good for eventually consistent reads, so don't use it with banking apps, etc. where the info always needs to be perfectly up to date.