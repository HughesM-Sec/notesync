# Try/Except Blocks in Python

Try/except blocks are used for exception handling in Python. They allow you to gracefully handle errors and exceptions that might occur during program execution.

## Basic Syntax

```python
try:
    # Code that might raise an exception
    result = 10 / 0
except ZeroDivisionError:
    # Code to handle the specific exception
    print("Cannot divide by zero!")
```

## Multiple Except Blocks

You can handle different types of exceptions separately:

```python
try:
    x = int(input("Enter a number: "))
    result = 10 / x
except ValueError:
    print("That's not a valid number!")
except ZeroDivisionError:
    print("Cannot divide by zero!")
```

## Catching Multiple Exceptions in One Except Block

```python
try:
    # Some code
    pass
except (TypeError, ValueError):
    print("A TypeError or ValueError occurred.")
```

## Using a Generic Except Block

While not recommended for most cases, you can catch all exceptions:

```python
try:
    # Some code
    pass
except Exception as e:
    print(f"An error occurred: {e}")
```

## The Else Clause

The `else` clause is executed if no exception occurs:

```python
try:
    result = 10 / 2
except ZeroDivisionError:
    print("Division by zero!")
else:
    print(f"The result is {result}")
```

## The Finally Clause

The `finally` clause is always executed, regardless of whether an exception occurred:

```python
try:
    file = open("example.txt", "r")
    # Some file operations
except FileNotFoundError:
    print("File not found!")
finally:
    file.close()  # This will always execute
```

## Raising Exceptions

You can raise exceptions manually using the `raise` keyword:

```python
x = -5
if x < 0:
    raise ValueError("x cannot be negative")
```

## Getting Exception Information

You can get detailed information about the exception:

```python
try:
    1 / 0
except ZeroDivisionError as e:
    print(f"Error message: {e}")
    print(f"Error type: {type(e).__name__}")
```

## Best Practices

1. Always catch specific exceptions rather than using a bare `except` clause.
2. Keep the code inside the `try` block focused on operations that may raise exceptions.
3. Use the `finally` clause for cleanup operations.
4. Avoid catching and silencing all exceptions unless absolutely necessary.
5. Use logging instead of print statements in production code for better error tracking.

## Example: Combining Multiple Concepts

```python
import logging

def divide(x, y):
    try:
        result = x / y
    except ZeroDivisionError:
        logging.error("Division by zero!")
        raise
    else:
        logging.info(f"Division successful, result: {result}")
        return result
    finally:
        logging.info("Division operation completed")

try:
    divide(10, 0)
except ZeroDivisionError:
    print("Please provide a non-zero divisor.")
```

This example demonstrates logging, re-raising exceptions, and using try/except both inside a function and when calling it.


[[Exception Handling]]