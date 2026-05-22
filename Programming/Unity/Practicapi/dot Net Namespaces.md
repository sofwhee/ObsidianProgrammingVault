Linq
- Convenient
- Slower and allocates more memory

(Use Mathf instead for Unity, because it uses float.)
(if you're using Unity's burst compiler, use `math` under unity mathematics namespace)
(it's much faster since it uses our full cpu)
Math
- Pow
- Sqrt
- Cos/Sin
- Pi
- Abs
- Floor
- Round

System.IO (input, output)
- File
- Directory
- FileStream
- StreamReader
- StreamWriter
- Path

```C#
var directoryPath = @"C:\Assets";
var filePath = Path.Combine(directoryPath, "SwordConfig.txt");

if (!Directory.Exists(directoryPath))
{
	Directory.CreateDirectory(directoryPath);
}

var swordConfig = "Legendary sword!";
File.WriteAllText(filePath, swordConfig);
```

System.Text
- Lets you manipulate text
- Regex
- [[StringBuilder]]

[[System.Reflection]]
- It lets us cheat by analyzing our own code
- By getting a Field, or Serialized Field for example

[[Attributes]]