# [Text Dump Engine](https://repl.it/@BD103/Text-Dump-Engine)
## What is it?
This engine (really just a module) is a handy way to save all your `print()` code into one file. It loads a `.json` file, then builds a `.py` file from that.

## How do I use it?
Very good question. First go to the project page (click the title) then fork it or download it (with the three dots).

### Editing the JSON
Here is a sample JSON text dump:

```json
{
  "greeting": [
    "Hello there my friend!",
    "How are you today?",
    "I hope you are well.",
    "See you around!"
  ],
  "puns": [
    "Nobody:",
    "",
    "That random stoplight:",
    "You have to stop."
  ]
}
```

This file builds to a Python file that looks like this:
```python
def greeting():
  print("Hello there my friend!")
  input()
  print("How are you today?)
  input()
  print("I hope you are well.")
  input()
  print("See you around!")
def puns():
  print("Nobody:")
  input()
  print("")
  input()
  print("That random stoplight:")
  input()
  print("You have to stop.")
```

Do you see? Keys in the JSON file become function names. Items in the array attached to the key becomes the text printed to the screen.

This JSON file is called `textdump.json`, and it is in the folder called `engine/`. The rules for editing the JSON goes by the following:

1. It must follow JSON syntax rules
2. You may have as many keys as you like
3. A key's value must be an array / list
4. The list may have as many values as necessary

### Importing the Engine
Now here comes the true brilliance of the module. You don't need to run any `init()` functions! By importing the file that supplies the text functions, it automatically rebuilds and reloads the file! So basically, you can just import `text.py` without worry! Here is a sample import function:
```python
from engine.text import *
```

The `import *` allows you to just run the function name without having to worry about the namespace. You can see the program below.

-------

<iframe height="400px" width="100%" src="https://repl.it/@BD103/Text-Dump-Engine?lite=true" scrolling="no" frameborder="no" allowtransparency="true" allowfullscreen="true" sandbox="allow-forms allow-pointer-lock allow-popups allow-same-origin allow-scripts allow-modals"></iframe>