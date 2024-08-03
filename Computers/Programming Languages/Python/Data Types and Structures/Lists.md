# Python Lists

## Introduction
Lists in Python are ordered, mutable sequences that can hold elements of different types. They are one of the most versatile and commonly used data structures in Python. Lists are defined by enclosing elements in square brackets `[]`, with elements separated by commas.

## Creating Lists
There are several ways to create lists in Python:

1. Using square brackets:
   ```python
   my_list = [1, 2, 3, 4, 5]
   mixed_list = [1, "hello", 3.14, True]
   ```

2. Using the `list()` function:
   ```python
   my_list = list("Hello")  # Creates ['H', 'e', 'l', 'l', 'o']
   number_list = list(range(5))  # Creates [0, 1, 2, 3, 4]
   ```

3. Creating an empty list:
   ```python
   empty_list1 = []
   empty_list2 = list()
   ```

## Accessing Elements
Python uses zero-based indexing for lists. You can access elements using indexing, negative indexing, or slicing.

1. Indexing (0-based):
   ```python
   my_list = ['apple', 'banana', 'cherry', 'date']
   print(my_list[0])  # Output: 'apple'
   print(my_list[2])  # Output: 'cherry'
   ```

2. Negative indexing (counts from the end):
   ```python
   print(my_list[-1])  # Output: 'date' (last element)
   print(my_list[-2])  # Output: 'cherry' (second to last element)
   ```

3. Slicing (getting a range of elements):
   ```python
   print(my_list[1:3])  # Output: ['banana', 'cherry']
   print(my_list[:2])   # Output: ['apple', 'banana']
   print(my_list[2:])   # Output: ['cherry', 'date']
   print(my_list[::2])  # Output: ['apple', 'cherry'] (every 2nd element)
   ```

## Common List Methods
Python lists come with many built-in methods. Here are some of the most commonly used ones:

1. `append(x)`: Add an element to the end
   ```python
   fruits = ['apple', 'banana']
   fruits.append('cherry')
   print(fruits)  # Output: ['apple', 'banana', 'cherry']
   ```

2. `extend(iterable)`: Add all elements from an iterable
   ```python
   fruits = ['apple', 'banana']
   more_fruits = ['cherry', 'date']
   fruits.extend(more_fruits)
   print(fruits)  # Output: ['apple', 'banana', 'cherry', 'date']
   ```

3. `insert(i, x)`: Insert an element at a specific position
   ```python
   fruits = ['apple', 'banana', 'cherry']
   fruits.insert(1, 'blueberry')
   print(fruits)  # Output: ['apple', 'blueberry', 'banana', 'cherry']
   ```

4. `remove(x)`: Remove the first occurrence of an element
   ```python
   fruits = ['apple', 'banana', 'cherry', 'banana']
   fruits.remove('banana')
   print(fruits)  # Output: ['apple', 'cherry', 'banana']
   ```

5. `pop([i])`: Remove and return an element (last by default)
   ```python
   fruits = ['apple', 'banana', 'cherry']
   popped = fruits.pop(1)
   print(popped)  # Output: 'banana'
   print(fruits)  # Output: ['apple', 'cherry']
   ```

6. `clear()`: Remove all elements
   ```python
   fruits = ['apple', 'banana', 'cherry']
   fruits.clear()
   print(fruits)  # Output: []
   ```

7. `index(x)`: Return the index of the first occurrence of an element
   ```python
   fruits = ['apple', 'banana', 'cherry', 'banana']
   print(fruits.index('banana'))  # Output: 1
   ```

8. `count(x)`: Count occurrences of an element
   ```python
   fruits = ['apple', 'banana', 'cherry', 'banana']
   print(fruits.count('banana'))  # Output: 2
   ```

9. `sort()`: Sort the list in-place
   ```python
   numbers = [3, 1, 4, 1, 5, 9, 2]
   numbers.sort()
   print(numbers)  # Output: [1, 1, 2, 3, 4, 5, 9]
   
   # Sort in descending order
   numbers.sort(reverse=True)
   print(numbers)  # Output: [9, 5, 4, 3, 2, 1, 1]
   ```

10. `reverse()`: Reverse the list in-place
    ```python
    fruits = ['apple', 'banana', 'cherry']
    fruits.reverse()
    print(fruits)  # Output: ['cherry', 'banana', 'apple']
    ```

## List Comprehensions
List comprehensions provide a concise way to create lists based on existing lists or other iterables. They combine a `for` loop and a conditional statement into a single line of code.

Basic syntax:
```python
new_list = [expression for item in iterable if condition]
```

Examples:
1. Create a list of squares:
   ```python
   squares = [x**2 for x in range(10)]
   print(squares)  # Output: [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
   ```

2. Create a list of even numbers:
   ```python
   evens = [x for x in range(20) if x % 2 == 0]
   print(evens)  # Output: [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]
   ```

3. Create a list of tuples (number, square) for even numbers:
   ```python
   even_squares = [(x, x**2) for x in range(10) if x % 2 == 0]
   print(even_squares)  # Output: [(0, 0), (2, 4), (4, 16), (6, 36), (8, 64)]
   ```

## Practice Assignment

Create a Python script that does the following:

1. Initialize a list of your favorite fruits.
2. Add a new fruit to the end of the list.
3. Insert a fruit at the beginning of the list.
4. Remove a fruit from the list.
5. Sort the list alphabetically.
6. Create a new list containing only fruits that start with the letter 'a' (case-insensitive) using a list comprehension.
7. Print the final lists.

Example solution:
```python
# Initialize a list of favorite fruits
fruits = ['banana', 'apple', 'mango', 'kiwi']

# Add a new fruit to the end of the list
fruits.append('strawberry')

# Insert a fruit at the beginning of the list
fruits.insert(0, 'pineapple')

# Remove a fruit from the list
fruits.remove('kiwi')

# Sort the list alphabetically
fruits.sort()

# Create a new list with fruits starting with 'a' (case-insensitive)
a_fruits = [fruit for fruit in fruits if fruit.lower().startswith('a')]

# Print the final lists
print("All fruits:", fruits)
print("Fruits starting with 'a':", a_fruits)
```

Try to complete this assignment on your own, and then compare your solution with the example provided. This exercise will help reinforce your understanding of list operations and list comprehensions.