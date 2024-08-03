# Python Dictionaries

## Introduction
Dictionaries in Python are unordered, mutable collections of key-value pairs. They are also known as associative arrays, hash tables, or hash maps in other programming languages. Dictionaries are defined by enclosing key-value pairs in curly braces `{}`, with each pair separated by commas.

## Creating Dictionaries

There are several ways to create dictionaries in Python:

1. Using curly braces with key-value pairs:
   ```python
   my_dict = {'name': 'John', 'age': 30, 'city': 'New York'}
   ```

2. Using the `dict()` constructor:
   ```python
   my_dict = dict(name='John', age=30, city='New York')
   ```

3. Using a list of tuples:
   ```python
   my_dict = dict([('name', 'John'), ('age', 30), ('city', 'New York')])
   ```

4. Creating an empty dictionary:
   ```python
   empty_dict1 = {}
   empty_dict2 = dict()
   ```

## Accessing and Modifying Elements

### Accessing Elements
You can access dictionary elements using square bracket notation or the `get()` method:

1. Using square brackets:
   ```python
   my_dict = {'name': 'John', 'age': 30, 'city': 'New York'}
   print(my_dict['name'])  # Output: John
   ```

2. Using the `get()` method (safer, as it doesn't raise an error for non-existent keys):
   ```python
   print(my_dict.get('age'))  # Output: 30
   print(my_dict.get('country', 'Not found'))  # Output: Not found
   ```

### Modifying Elements
Dictionaries are mutable, so you can add, modify, or remove key-value pairs:

1. Adding or modifying a key-value pair:
   ```python
   my_dict['occupation'] = 'Engineer'  # Adds a new key-value pair
   my_dict['age'] = 31  # Modifies an existing value
   ```

2. Updating multiple key-value pairs:
   ```python
   my_dict.update({'age': 32, 'country': 'USA'})
   ```

3. Removing a key-value pair:
   ```python
   del my_dict['city']  # Removes the 'city' key-value pair
   popped_value = my_dict.pop('age')  # Removes and returns the value
   ```

## Common Dictionary Methods

1. `keys()`: Returns a view of all keys
   ```python
   print(my_dict.keys())  # Output: dict_keys(['name', 'occupation', 'country'])
   ```

2. `values()`: Returns a view of all values
   ```python
   print(my_dict.values())  # Output: dict_values(['John', 'Engineer', 'USA'])
   ```

3. `items()`: Returns a view of all key-value pairs as tuples
   ```python
   print(my_dict.items())  # Output: dict_items([('name', 'John'), ('occupation', 'Engineer'), ('country', 'USA')])
   ```

4. `clear()`: Removes all items from the dictionary
   ```python
   my_dict.clear()
   print(my_dict)  # Output: {}
   ```

5. `copy()`: Returns a shallow copy of the dictionary
   ```python
   new_dict = my_dict.copy()
   ```

6. `setdefault(key, default)`: Returns the value of a key if it exists, otherwise inserts the key with the specified default value
   ```python
   print(my_dict.setdefault('name', 'Unknown'))  # Output: John
   print(my_dict.setdefault('age', 30))  # Output: 30 (and adds this key-value pair)
   ```

## Dictionary Comprehensions

Dictionary comprehensions provide a concise way to create dictionaries based on existing dictionaries or other iterables.

Basic syntax:
```python
new_dict = {key_expression: value_expression for item in iterable if condition}
```

Examples:

1. Create a dictionary of squares:
   ```python
   squares = {x: x**2 for x in range(5)}
   print(squares)  # Output: {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}
   ```

2. Create a dictionary of even numbers and their squares:
   ```python
   even_squares = {x: x**2 for x in range(10) if x % 2 == 0}
   print(even_squares)  # Output: {0: 0, 2: 4, 4: 16, 6: 36, 8: 64}
   ```

3. Swap keys and values in a dictionary:
   ```python
   original = {'a': 1, 'b': 2, 'c': 3}
   swapped = {v: k for k, v in original.items()}
   print(swapped)  # Output: {1: 'a', 2: 'b', 3: 'c'}
   ```

## Nested Dictionaries

Dictionaries can contain other dictionaries as values, allowing for complex data structures:

```python
employees = {
    'John': {'age': 30, 'position': 'Manager', 'salary': 50000},
    'Alice': {'age': 25, 'position': 'Developer', 'salary': 45000},
    'Bob': {'age': 35, 'position': 'Designer', 'salary': 48000}
}

print(employees['Alice']['position'])  # Output: Developer
```

## Practice Assignment

Create a Python script that does the following:

1. Create a dictionary representing a simple inventory system for a small store. Include at least 5 items with their prices.
2. Add a new item to the inventory.
3. Update the price of an existing item.
4. Remove an item from the inventory.
5. Print all items and their prices.
6. Create a new dictionary containing only items with prices under $10 using a dictionary comprehension.
7. Calculate and print the total value of the inventory.

