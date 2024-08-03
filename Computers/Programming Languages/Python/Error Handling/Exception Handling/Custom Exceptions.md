# Custom Exceptions in Python

Custom exceptions allow you to define your own error types specific to your application's needs. They help in creating more meaningful and precise error handling.

## Basic Syntax

To create a custom exception, define a new class that inherits from the built-in Exception class or any of its subclasses:

```python
class CustomError(Exception):
    pass
```

## Creating a Custom Exception with Additional Information

You can add attributes and methods to your custom exception:
```python
class ValueTooHighError(Exception):
    def __init__(self, message, value):
        self.message = message
        self.value = value
    
    def __str__(self):
        return f'{self.message}: {self.value}'
```

## Raising Custom Exceptions

Raise your custom exception like any built-in exception:
```python
def check_value(x):
	if x > 100:
		raise ValueTooHighError("Value is too high", x)
	print("Value is acceptable")
try:
	check_value(200)
except ValueTooHighError as error:
	print(error)
```

## Handling Custom Exceptions
Handle custom exceptions in try/except blocks:
```python
try:
	# Code that might raise your custom exception
	check_value(150)
except ValueTooHighError as e:
	print(f"Caught an error: {e}")
```


## Extending Built-in Exceptions
You can create custom exceptions that extend built-in exceptions:
```python
class NetworkError(IOError):
    def __init__(self, message, status_code):
        super().__init__(f'{status_code}: {message}')
        self.status_code = status_code
```

## Best Practices

1. Name your custom exceptions with the suffix "Error" for clarity.
2. Create a base exception for your module/application, then derive specific exceptions from it.
3. Keep your exception classes simple and focused.
4. Document your custom exceptions thoroughly.
## Example: Custom Exception Hierarchy
```python
class AppBaseException(Exception):
    """Base exception for the application"""

class DatabaseError(AppBaseException):
    """Raised when a database-related error occurs"""

class NetworkError(AppBaseException):
    """Raised when a network-related error occurs"""

class InputError(AppBaseException):
    """Raised when invalid input is provided"""
    def __init__(self, message, input_value):
        super().__init__(message)
        self.input_value = input_value
```
This structure allows for more specific error handling:
```python
try:
    # Some code that might raise these exceptions
    pass
except DatabaseError:
    print("A database error occurred")
except NetworkError:
    print("A network error occurred")
except InputError as e:
    print(f"Invalid input: {e.input_value}")
except AppBaseException:
    print("An application-specific error occurred")
```

[[Exception Handling]]