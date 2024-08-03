`# For Loops A for loop is used to iterate over a sequence (like a list, tuple, string, or range) or other iterable objects.  ## Basic Syntax ```python for item in iterable:     # code to be executed for each item`

## Iterating Over Lists

Lists are sequences that contain multiple items in a variable. They are created using square brackets.

### EXAMPLE:

```python
classmates = ["Mikey", "Sophia", "Terry", "Thomas", "Lily"]
for friend in classmates:
    print(friend)
```

### Output:

```
Mikey
Sophia
Terry
Thomas
Lily
```

## Using range() Function

You can iterate through a range of numbers using the range() function.

```python
for n in range(3):
	print(n)
```

### Output:

`0 1 2`

## Additional range() Usage

- range(stop): Generates numbers from 0 to stop-1
- range(start, stop): Generates numbers from start to stop-1
- range(start, stop, step): Generates numbers from start to stop-1, incrementing by step

### EXAMPLE:

```python
for i in range(2, 8, 2):
    print(i)
```

### Output:

```
2
4 
6
```

## Iterating Over Strings

For loops can iterate over characters in a string:

```python
for char in "Python":
    print(char)
```

## Enumerate Function

Use enumerate() to get both the index and value:

```python
fruits = ["apple", "banana", "cherry"]
for index, fruit in enumerate(fruits):
    print(f"Index {index}: {fruit}")
```

## Loop Control

- `break`: Exits the loop prematurely
- `continue`: Skips the rest of the current iteration
- `else` clause: Executed when the loop completes normally (not via break)

### EXAMPLE:

```python
for num in range(10):
    if num == 5:
        break
    print(num)
else:
    print("Loop completed normally")
```


[[Loops]]