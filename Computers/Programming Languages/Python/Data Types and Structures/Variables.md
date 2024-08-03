# Variables in Python

Variables allow you to store and update data. A variable has a name and can store various types of data.

## Basic Variable Assignment

```python
name = "Matt"
age = 25
height = 1.75
is_student = True
```
 In these examples, we're storing different types of data:
- String to 'name'
- Integer to 'age'
- Float to 'height'
- Boolean to 'is_student'
## Using Variables
Variables can be used in various operations:
```python
# String concatenation
print("Hi, my name is " + name + ".")

# Using f-strings (Python 3.6+)
print(f"I am currently {age} years old.")
print(f"My height is {height} meters.")

# Boolean check
if is_student:
    print("I am a student.")
```

## Type Conversion
Converting between types:
```python
# Integer to String
age_str = str(age)
print("I am" + age_str + " years old.")

# String to Integer
number_str = "100"
number_int = int(number_str)
print(number_int + 50) # Outputs 150

# String to Float
pi_str = "3.14159"
pi_float = float(pi_str)
```

## Variable Naming Conventions

- Use lowercase letters, numbers, and underscores
- Start with a letter or underscore, not a number
- Be descriptive but concise
- Use snake_case for multiple words

Good examples:
```python
user_name = "John"
total_score = 100
is_game_over = False
```
## Dynamic Typing
Python is dynamically typed, meaning you can reassign variables to different types:
```python
x = 5
print(type(x))  # <class 'int'>
x = "hello"
print(type(x))  # <class 'str'>
```
## Multiple Assignment
You can assign multiple variables at once:
```python
a, b, c = 1, 2, 3
x = y = z = 0
```
## Constants
By convention, constants (variables that shouldn't change) are named in all caps:
```python
PI = 3.14159
MAX_SPEED = 120
```

## Best Practices
- Use meaningful names that describe the data they hold
- Avoid using reserved keywords as variable names
- Be consistent with naming conventions throughout your code
- Use type hints for clearer code (Python 3.5+)
```python
name: str = "Matt"
age: int = 25
```
- Avoid global variables when possible; use function parameters and return values instead


