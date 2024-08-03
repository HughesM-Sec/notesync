# If-Else Statements in Python

If-Else statements are used for conditional execution in Python. They allow your program to make decisions and execute different code blocks based on specified conditions.

## Basic Syntax

```python
if condition:
    # Code to execute if condition is True
else:
    # Code to execute if condition is False
```

## Simple If Statement

```python
x = 10
if x > 5:
    print("x is greater than 5")
```

## If-Else Statement

```python
age = 18
if age >= 18:
    print("You are an adult")
else:
    print("You are a minor")
```

## If-Elif-Else Statement

Use `elif` (short for "else if") to check multiple conditions:

```python
score = 75
if score >= 90:
    print("A")
elif score >= 80:
    print("B")
elif score >= 70:
    print("C")
elif score >= 60:
    print("D")
else:
    print("F")
```

## Nested If Statements

You can nest if statements inside other if statements:

```python
x = 10
y = 5
if x > 5:
    if y > 2:
        print("x is greater than 5 and y is greater than 2")
    else:
        print("x is greater than 5 but y is not greater than 2")
```

## Ternary Operator (Conditional Expression)

A shorthand way to write simple if-else statements:

```python
age = 20
status = "adult" if age >= 18 else "minor"
print(status)
```

## Using Logical Operators

You can use `and`, `or`, and `not` to combine conditions:

```python
x = 5
y = 10
if x > 0 and y > 0:
    print("Both x and y are positive")

if x > 0 or y > 0:
    print("At least one of x or y is positive")

if not x > 10:
    print("x is not greater than 10")
```

## Truthy and Falsy Values

In Python, certain values are considered "falsy":
- False
- None
- 0
- 0.0
- '' (empty string)
- [] (empty list)
- {} (empty dictionary)
- set() (empty set)

All other values are considered "truthy". You can use this in if statements:

```python
name = ""
if name:
    print("Name is not empty")
else:
    print("Name is empty")
```

## Best Practices

1. Keep conditions simple and readable.
2. Use elif for multiple conditions rather than nested if statements when possible.
3. Consider using a dictionary or match statement (Python 3.10+) for complex if-elif chains.
4. Be aware of the difference between `==` (comparison) and `=` (assignment).

## Example: Combining Concepts

```python
def grade_student(name, score):
    if not name:
        return "Error: Name cannot be empty"
    
    if not isinstance(score, (int, float)) or score < 0 or score > 100:
        return "Error: Invalid score"

    if score >= 90:
        grade = "A"
    elif score >= 80:
        grade = "B"
    elif score >= 70:
        grade = "C"
    elif score >= 60:
        grade = "D"
    else:
        grade = "F"

    return f"{name}'s grade: {grade}"

print(grade_student("Alice", 85))
print(grade_student("", 75))
print(grade_student("Bob", 105))
```

This example demonstrates input validation, multiple conditions, and returning different results based on conditions.

