# Load Module
## Function `loadbar(value, length=100)`
Creates a loadbar, but doesn't animate. Returns a variable, but doesn't actually print anything. Meant to be attached to a variable in a statement like the following:
```python
i = 0
while i <= length:
  dothing(i)
  print(loadbar(i, length=length), end="\r")
  i += 1
  #time.sleep(0.1) # if you want a delay
print()
```

For an example, [go to my image flipper, and look at the flip() function](https://repl.it/@BD103/Image-Flipper#flip.py).

## Function `load(length=100)`
Creates a standard loadbar, sleeping for 0.1 seconds between loads. This is completely for asthetic, and doesn't actually represent anything. Look at the `loadbar()` function for actual interactivity.

## Dependencies
This module uses the `time` and `os` modules. All are built-in, so there are no other downloads.