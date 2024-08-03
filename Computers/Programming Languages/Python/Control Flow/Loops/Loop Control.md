# Loop Control Statements

Loop control statements alter the normal flow of loop execution. In Python, there are three main loop control statements: break, continue, and else.

## 1. break Statement

The `break` statement terminates the loop prematurely.

- When encountered inside a loop, it immediately ends the loop's execution.
- It's often used to exit a loop when a certain condition is met.

### EXAMPLE:
```python
for i in range(5):
    if i == 3:
        break
    print(i)
print("Loop ended")

```

### Output:
```
0
1
2
Loop ended
```

## 2. continue Statement

The `continue` statement skips the rest of the current iteration and moves to the next iteration of the loop.

- It's used when you want to skip specific elements in a loop.

EXAMPLE:
```python
for i in range(5):
    if i == 2:
        continue
    print(i)
```

### Output:
```
0
1
3
4
```

## 3. else Clause in Loops

The `else` clause in a loop is executed when the loop completes normally (i.e., not terminated by a break statement).

- It's useful for implementing search algorithms where you want to know if the search completed without finding a match.

### EXAMPLE:
```python
for i in range(5):
    print(i)
else:
    print("Loop completed normally")

# Contrast with:
for i in range(5):
    if i == 3:
        break
    print(i)
else:
    print("This won't be printed")
```

## Combining Control Statements

You can use these statements in combination for more complex flow control.

### EXAMPLE:
```python
numbers = [1, 3, 5, 7, 9, 2, 4, 6, 8, 10]
for num in numbers:
    if num % 2 == 0:
        print(f"First even number found: {num}")
        break
    elif num > 8:
        print("No even number found below 9")
        break
else:
    print("No even numbers in the list")
```

This example searches for the first even number, stops if a number greater than 8 is found, and uses the else clause to handle the case where no even numbers are present.

[[Loops]]