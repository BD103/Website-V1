# Parser Module
## Function `grid(path)`
Splits a `.txt` file by line, then appends it to a list.

Example:

Text File
```txt
Hi there.
How are you?
```

Python File
```python
from bd103 import parser
x = parser.grid("textfile.txt")
print(x)
```

Returns as:
```txt
["Hi there.\n", "How are you?\n"]
```

## Function `space(text, identifier=" ")`
Splits the given string into a list by the identifier. The default is a space, but you may specify it.

> This function will soon be deprecated, as the `split()` built-in functions does the same thing.