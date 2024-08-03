
# Strings in Python

Strings are sequences of characters in Python, used to represent text. They are immutable, meaning once created, their contents cannot be changed.

## Creating Strings

Strings can be created using single quotes, double quotes, or triple quotes:

```python
single_quoted = 'Hello, World!'
double_quoted = "Python Programming"
multi_line = '''This is a
multi-line string'''
```

## String Operations
## Concatenation

### Joining strings together:
```python
first_name = "John"
last_name = "Doe"
full_name = first_name + " " + last_name #"John Doe"
```

## Repetition
### Repeating a string:
```python
echo = "Hello" * 3 # "HelloHelloHello"
```

## Indexing and Slicing
### Accessing characters or substrings:
```python
text = "Python"
first_char = text[0] # "P" (Important to note: Python starts at 0, instead of 1)
substring = text[1:4] # "yth"
reversed_text = text[::-1] # "nohtyP"
```

## String Methods
### len()
### Get the length of a string:
```python
length = len("Python")  # 6
```
### upper(), lower(), title()

### Changing case:
```python
text = 'python programming'
print(text.upper()) # "PYTHON PROGRAMMING"
print(text.title()) # "Python Programming"
```

## strip(), lstrip(), rstrip()
### Removing Whitespace:
```python
padded = " hello "
print(padded.strip()) # "hello"
```

## replace()
### Replacing substrings:
```python
text = "Hello, World!"
new_text = text.replace("World", "Python") # Hello, Python!"
```

## split() and join()
### Splitting and joining strings:
```python
words = "Python is awesome".split() # ['Python', 'is', 'awesome']
sentence = " ".join(words) # "Python is awesome"
```

## String Formatting
### f-strings (Python 3.6+)
```python
name = "Alice"
age = 30
print(f"{name} is {age} years old") # "Alice is 30 years old"
```

## format() method
```python
name = "Alice"
age = 30
print("{} is {} years old".format(name,age)) # "Alice is 30 years old"
```

## %-formatting(older style)
```python
print("%s is %d years old" % (name, age))
```

## Escape Characters
### Special characters in strings:
```python
print("Line 1\nLine 2") # Newline
print("Tab\tspaced") # Tab
print("\"Quoted\"") # Quotes
```

### Example:
```python
name = "Alice"
age = 30
print(f"{name} is \n{age} years old") # "Alice is 30 years old"
print("{} is \t{} years old".format(name,age))
print("\"%s is %d years old\"" % (name, age))
```
Result:
```
Alice is
30 years old

Alice is    30 years old


"Alice is 30 years old"
```

## String Checks
### Useful methods for checking string contents:
```python
text = "Python3.9"
print(text.isalpha())   # False (contains numbers and a period)
print(text.isalnum())   # False (contains a period)
print(text.startswith("Py"))  # True
print(text.endswith("9"))     # True

# Additional examples for clarity:
print("python39".isalnum())   # True
print("python 39".isalnum())  # False (space is not alphanumeric)
print("python!".isalnum())    # False (exclamation mark is not alphanumeric)
print("python3.9".isalnum())  # False (period is not alphanumeric)
```


## Raw Strings
### Strings that treat backslashes at literal characters:
```python
path = r"C:\Users\JohnDoe\Documents"
```

## Best Practices

1. Use f-strings for string formatting when possible (Python 3.6+).
2. Be mindful of string immutability; create new strings instead of trying to modify existing ones.
3. Use appropriate string methods instead of manual operations for better readability and efficiency.
4. Consider using raw strings for file paths or regular expressions to avoid escape character issues.