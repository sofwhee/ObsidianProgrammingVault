Playerprefs
- Store single variables one by one
- Only stores small amount of data and is not secure

JSON / XML
- Super Simple
- Easy to Modify
- Edit in Text Editor
- Makes Game Moddable
- Simple database for games
- Not secure because they're easy to modify

Custom Binary Files
- Hard to read and modify because they're in binary
**Instructions:**
- Start by making a class that stores the data we want with public variables
- Unity-specific variables aren't serializable
	- They can just be represented with the four basic data types
- Make a binary formatter
- Output it to file in game files
- Then do the same in reverse when loading

Filestream
stream of data contained in a file
must be closed after usage with stream.Close()