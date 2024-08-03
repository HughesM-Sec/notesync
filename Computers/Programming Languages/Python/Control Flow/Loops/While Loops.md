
While loops execute a block of code as long as a specified condition is true. They can run indefinitely or a specific number of times based on the condition.

## Basic Syntax
```python
while condition:
    # code to be executed
```

### Simple Example:
```python
n = 2
while n <= 1000:
    print(n)
    n = n + n
```
### Output:
```
2
4
8
16
32
64
128
256
512
```

This script starts at 2 and doubles the number until it's no longer smaller than 1000.

## Infinite Loops

While loops can run indefinitely if the condition always evaluates to True:
```python
while True:
    print("This will run forever unless interrupted")
```
Note: Use Ctrl+C to interrupt an infinite loop in most environments.

## Loop Control with break
You can use `break` to exit a while loop prematurely:
```python
count = 0
while True:
    print(count)
    count += 1
    if count >= 5:
        break
```
## Using continue

The `continue` statement skips the rest of the current iteration:
```python
i = 0
while i < 5:
    i += 1
    if i == 3:
        continue
    print(i)
```
### Output:
```
1
2
4
5
```

## else Clause

While loops can have an else clause that executes when the condition becomes false:
```python
count = 0
while count < 3:
    print(count)
    count += 1
else:
    print("Loop completed")
```

## Common Pitfalls

1. Forgetting to update the loop variable can lead to infinite loops.
2. Ensure the condition will eventually become false to avoid unintended infinite loops.

## Use Cases

- Reading input until a specific condition is met
- Implementing game loops
- Performing tasks with an unknown number of iterations


[[Loops]]