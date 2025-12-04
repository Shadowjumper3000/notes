# 1. Introduction

Python is a high-level, interpreted programming language known for its readability and simplicity. It supports multiple programming paradigms including procedural, object-oriented, and functional programming. Python is widely used for scripting, web development, data analysis, automation, and more.

### Basic Concepts for Beginners

- **Zero-Based Counting**: In Python (and many programming languages), counting starts at 0. This means the first element in a list or string has index 0.
```python
lst = ['a', 'b', 'c']
print(lst[0])  # 'a'
print(lst[1])  # 'b'
```
- **Variables**: Containers for storing data. You don’t need to declare their type explicitly.
```python
x = 10       # integer
name = "Alice"  # string
```
- **Comments**: Use `#` for single-line comments to explain code.
```python
# This is a comment
print("Hello, Python")  # Prints a message
```
- **Whitespace / Indentation**: Python uses indentation instead of curly braces `{}` to define code blocks.
```python
if x > 0:
    print("Positive")  # Indented under the if-statement
```
- **Basic Input/Output**:
```python
name = input("Enter your name: ")  # Read input from user
print("Hello,", name)               # Print output
```
**Basic Data Types**:

- Numbers (`int`, `float`)
- Text (`str`)
- Boolean (`True` / `False`)
- Collections (`list`, `tuple`, `set`, `dict`)

---

# 2. Data Types

## 2.1 Numeric Types

Python has several numeric types for representing numbers:

### Integers (`int`)

- Whole numbers, positive or negative, no decimal point.
- Arbitrary precision (limited only by memory).
```python
x = 10       # positive integer
y = -42      # negative integer
z = 0        # zero
print(type(x))  # <class 'int'>
```
### Operations:
```python
a = 5
b = 2
print(a + b)  # 7
print(a - b)  # 3
print(a * b)  # 10
print(a // b) # integer division -> 2
print(a % b)  # modulo -> 1
print(a ** b) # exponentiation -> 25
```
### Floating-Point Numbers (`float`)

- Numbers with a decimal point.
- Used for real numbers, limited precision (~15–17 digits).
```python
f1 = 3.14
f2 = -0.001
f3 = 2.0
print(type(f1))  # <class 'float'>
```
### Operations:
```python
print(f1 + f2)  # 3.139
print(f1 * f3)  # 6.28
print(f1 / f3)  # 1.57
```
- Note: Floating-point math may have rounding errors:
```python
0.1 + 0.2  # 0.30000000000000004
```
### Complex Numbers (`complex`)

- Represented as `a + bj`, where `j` is the imaginary unit.
- Useful for scientific computing and signal processing.
```python
c = 2 + 3j
print(c.real)  # 2.0
print(c.imag)  # 3.0
print(abs(c))  # magnitude -> sqrt(2^2 + 3^2) = 3.60555
```
### Type Conversion (Casting)

- Convert between numeric types using `int()`, `float()`, `complex()`:
```python
a = 10
b = float(a)    # 10.0
c = complex(a)  # 10 + 0j
```
- Be careful with `int()` on floats—it **truncates**, does not round:
```python
  int(3.9)  # 3
```
### Useful Functions

- `abs(x)` → absolute value
- `round(x, n)` → round to `n` decimal places
- `pow(a, b)` → a to the power b
- `divmod(a, b)` → quotient and remainder
## 2.2 Boolean
```python
flag = True
is_open = False
```
## 2.3 Strings
```python
s = "Hello, Python"
print(s[0])   # 'H'
print(s[0:5]) # 'Hello'
```
## 2.4 Data Structures
### Lists
```python
lst = [1, 2, 3, 4]
lst.append(5)
lst[0] = 10
```
### Tuples
```python
t = (1, 2, 3)
# Immutable
```
### Sets
```python
s = {1, 2, 3}
s.add(4)
```
### Dictionaries
```python
d = {"a": 1, "b": 2}
print(d["a"])
d["c"] = 3
```
---
# 3. Operators
## 3.1 Arithmetic Operators
```python
a = 10
b = 3
print(a + b)  # 13
print(a - b)  # 7
print(a * b)  # 30
print(a / b)  # 3.3333
print(a // b) # 3
print(a % b)  # 1
print(a ** b) # 1000
```
## 3.2 Comparison Operators
```python
print(a == b) # False
print(a != b) # True
print(a > b)  # True
print(a < b)  # False
```
## 3.3 Logical Operators
```python
print(a > 5 and b < 5)  # True
print(a > 5 or b > 5)   # True
print(not(a > b))        # False
```
## 3.4 Assignment Operators
```python
x = 5
x += 2  # x = 7
x *= 3  # x = 21
```
## 3.5 Membership and Identity
```python
print(3 in lst)    # True
print(4 not in lst) # False
print(a is b)      # False
```
---
# 4. Conditions
```python
x = 10
if x > 0:
    print("Positive")
elif x == 0:
    print("Zero")
else:
    print("Negative")
```
---
# 5. Loops
## 5.1 For Loop
```python
for i in range(5):
    print(i)
```
## 5.2 While Loop
```python
x = 0
while x < 5:
    print(x)
    x += 1

    break stops the loop

    continue skips to next iteration

    else can run after a loop completes without break
```
---
# 6. Functions
```python
def add(a, b):
    return a + b

result = add(2, 3)
print(result)
```
---
# 7. Time and Space Complexity
## 7.1 Time Complexity
```python
    O(1) – constant time

    O(n) – linear time

    O(n^2) – quadratic, e.g., nested loops

    O(log n) – logarithmic, e.g., binary search
```
## 7.2 Space Complexity
```python
    O(1) – constant extra space

    O(n) – linear space, e.g., storing a list of size n
```
### Examples:
```python
# Linear search
arr = [1, 2, 3, 4]
for x in arr:
    if x == 3:
        break  # O(n) time, O(1) space
        
# Binary search on sorted array
def binary_search(arr, target):
    low, high = 0, len(arr)-1
    while low <= high:
        mid = (low + high)//2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            low = mid + 1
        else:
            high = mid - 1
    return -1  # O(log n) time, O(1) space
```