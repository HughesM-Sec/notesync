# Python Tuples

## Introduction
Tuples in Python are ordered, immutable sequences that can hold elements of different types. They are similar to lists but cannot be changed after creation. Tuples are defined by enclosing elements in parentheses `()`, with elements separated by commas.

## Creating Tuples

There are several ways to create tuples in Python:

1. Using parentheses with elements:
   ```python
   my_tuple = (1, 2, 3, 4, 5)
   mixed_tuple = (1, "hello", 3.14, True)
   ```

2. Using the `tuple()` function:
   ```python
   my_tuple = tuple([1, 2, 3, 4, 5])
   string_tuple = tuple("Hello")  # Creates ('H', 'e', 'l', 'l', 'o')
   ```

3. Creating a single-element tuple (note the comma):
   ```python
   single_tuple = (42,)
   # Without the comma, it's not a tuple: not_a_tuple = (42)
   ```

4. Creating an empty tuple:
   ```python
   empty_tuple = ()
   also_empty = tuple()
   ```

## Accessing Elements

Like lists, Python uses zero-based indexing for tuples. You can access elements using indexing, negative indexing, or slicing.

1. Indexing (0-based):
   ```python
   my_tuple = ('apple', 'banana', 'cherry', 'date')
   print(my_tuple[0])  # Output: 'apple'
   print(my_tuple[2])  # Output: 'cherry'
   ```

2. Negative indexing (counts from the end):
   ```python
   print(my_tuple[-1])  # Output: 'date' (last element)
   print(my_tuple[-2])  # Output: 'cherry' (second to last element)
   ```

3. Slicing (getting a range of elements):
   ```python
   print(my_tuple[1:3])  # Output: ('banana', 'cherry')
   print(my_tuple[:2])   # Output: ('apple', 'banana')
   print(my_tuple[2:])   # Output: ('cherry', 'date')
   print(my_tuple[::2])  # Output: ('apple', 'cherry') (every 2nd element)
   ```

## Tuple Operations

Although tuples are immutable, there are several operations you can perform with them:

1. Concatenation:
   ```python
   tuple1 = (1, 2, 3)
   tuple2 = (4, 5, 6)
   combined = tuple1 + tuple2
   print(combined)  # Output: (1, 2, 3, 4, 5, 6)
   ```

2. Repetition:
   ```python
   repeated = tuple1 * 3
   print(repeated)  # Output: (1, 2, 3, 1, 2, 3, 1, 2, 3)
   ```

3. Membership testing:
   ```python
   print(2 in tuple1)  # Output: True
   print(5 in tuple1)  # Output: False
   ```

## Tuple Methods

Tuples have only two built-in methods:

1. `count(x)`: Returns the number of occurrences of an element
   ```python
   my_tuple = (1, 2, 2, 3, 2, 4)
   print(my_tuple.count(2))  # Output: 3
   ```

2. `index(x)`: Returns the index of the first occurrence of an element
   ```python
   print(my_tuple.index(3))  # Output: 3
   ```

## Tuple Packing and Unpacking

Tuple packing is the process of putting multiple values into a tuple. Tuple unpacking is the reverse process.

1. Tuple packing:
   ```python
   packed_tuple = 1, 2, 3  # Parentheses are optional
   print(packed_tuple)  # Output: (1, 2, 3)
   ```

2. Tuple unpacking:
   ```python
   a, b, c = packed_tuple
   print(a, b, c)  # Output: 1 2 3
   ```

3. Using * for extended unpacking:
   ```python
   first, *rest = (1, 2, 3, 4, 5)
   print(first)  # Output: 1
   print(rest)   # Output: [2, 3, 4, 5]
   ```

## Tuples vs. Lists

Tuples have several advantages over lists in certain situations:

1. Immutability: Tuples cannot be changed after creation, making them useful for constant data.
2. Performance: Tuples are slightly faster than lists for accessing elements.
3. As dictionary keys: Tuples can be used as dictionary keys (if they contain only immutable elements), while lists cannot.
4. Multiple return values: Functions often return tuples to group multiple return values.

Example of using a tuple as a dictionary key:
```python
locations = {(40.7128, 74.0060): "New York City",
             (51.5074, 0.1278): "London",
             (48.8566, 2.3522): "Paris"}
print(locations[(40.7128, 74.0060)])  # Output: New York City
```

## Named Tuples

For more readable code, Python's `collections` module provides `namedtuple`, which allows you to create tuple subclasses with named fields:

```python
from collections import namedtuple

Point = namedtuple('Point', ['x', 'y'])
p = Point(11, y=22)
print(p.x, p.y)  # Output: 11 22
print(p)  # Output: Point(x=11, y=22)
```

## Practice Assignment

Create a Python script that does the following:

1. Create a tuple containing the names of five countries.
2. Use tuple unpacking to assign each country to a separate variable.
3. Create a list of tuples where each tuple contains a country name and its length.
4. Sort the list of tuples based on the length of the country names (shortest to longest).
5. Create a dictionary where the country names are keys and their lengths are values.
6. Find and print the country with the longest name using the dictionary.
7. Use a named tuple to represent a Country with 'name' and 'population' fields. Create a list of 3 countries using this named tuple.