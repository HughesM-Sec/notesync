# Raising Exceptions in Python

Raising exceptions allows you to trigger specific error conditions in your code. This is useful for indicating when something unexpected or incorrect occurs in your program.

## Basic Syntax

To raise an exception, use the `raise` keyword:

```python
raise ExceptionType("Error message")
```

## Raising Built-in Exceptions

Python has many built-in exceptions that you can raise:

```python
# Raising a ValueError
x = -5
if x < 0:
    raise ValueError("x cannot be negative")

# Raising a TypeError
def add(a, b):
    if not (isinstance(a, (int, float)) and isinstance(b, (int, float))):
        raise TypeError("Both arguments must be numbers")
    return a + b
```

## Raising Custom Exceptions

You can raise your own custom exceptions:

```python
class ValueTooHighError(Exception):
    pass

def check_value(x):
    if x > 100:
        raise ValueTooHighError("Value is too high")
```

## Re-raising Exceptions

You can catch an exception and then re-raise it:

```python
try:
    # Some code that might raise an exception
    result = 10 / 0
except ZeroDivisionError:
    print("Logging the error")
    raise  # Re-raises the caught exception
```

## Raising from Another Exception

You can raise a new exception from a caught exception, maintaining the traceback:

```python
try:
    1 / 0
except ZeroDivisionError as e:
    raise ValueError("Invalid operation") from e
```

## Raising Exceptions with Additional Information

You can include additional information when raising an exception:

```python
def process_data(data):
    if not data:
        raise ValueError("Empty data set", {"data_length": 0})

try:
    process_data([])
except ValueError as e:
    print(f"Error: {e.args[0]}")
    print(f"Additional info: {e.args[1]}")
```

## Best Practices for Raising Exceptions

1. Use built-in exceptions when appropriate.
2. Create custom exceptions for application-specific errors.
3. Provide clear and informative error messages.
4. Include relevant data in the exception when possible.
5. Raise exceptions as early as possible when an error condition is detected.

## Example: Combining Exception Raising and Handling

```python
class InsufficientFundsError(Exception):
    def __init__(self, balance, amount):
        self.balance = balance
        self.amount = amount
        super().__init__(f"Insufficient funds: balance={balance}, amount={amount}")

def withdraw(balance, amount):
    if amount > balance:
        raise InsufficientFundsError(balance, amount)
    return balance - amount

try:
    new_balance = withdraw(100, 150)
except InsufficientFundsError as e:
    print(f"Error: {e}")
    print(f"Current balance: {e.balance}, Attempted withdrawal: {e.amount}")
else:
    print(f"New balance: {new_balance}")
```

This example demonstrates creating a custom exception, raising it with specific information, and then handling it with detailed error reporting.


[[Exception Handling]]