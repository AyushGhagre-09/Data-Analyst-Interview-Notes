# Python Interview Questions

A collection of Python interview questions organized by difficulty level, with concise answers and examples.

---

# 🟢 Beginner Level

## 1. What is Python?
Python is a high-level, interpreted, general-purpose programming language known for readable syntax.

## 2. What are the key features of Python?
- Simple and readable syntax
- Dynamically typed
- Object-oriented
- Large standard library
- Cross-platform
- Supports multiple programming paradigms

## 3. What is a variable?
A variable is a name that refers to an object.

```python
age = 25
name = "Ayush"
```

## 4. What are common Python data types?
```text
int, float, str, bool, list, tuple, set, dict
```

## 5. What is dynamic typing?
Python determines an object's type at runtime.

```python
x = 10
x = "Hello"
```

## 6. What is type casting?
Converting a value from one type to another.

```python
x = "100"
num = int(x)
```

## 7. Difference between `=`, `==`, and `is`?
```text
=   → assignment
==  → value equality
is  → object identity
```

## 8. Mutable vs immutable objects?
Mutable objects can be changed after creation: `list`, `dict`, `set`.

Immutable objects cannot be changed after creation: `int`, `float`, `str`, `tuple`, `bool`.

## 9. What is a list?
An ordered, mutable collection.

```python
numbers = [10, 20, 30]
```

## 10. What is a tuple?
An ordered, immutable collection.

```python
numbers = (10, 20, 30)
```

## 11. What is a set?
An unordered collection of unique elements.

```python
numbers = {10, 20, 30}
```

## 12. What is a dictionary?
A collection of key-value pairs.

```python
student = {"name": "Ayush", "age": 25}
```

## 13. Difference between list, tuple, set, and dictionary?
| Type | Ordered | Mutable | Duplicates |
|---|---|---|---|
| List | Yes | Yes | Yes |
| Tuple | Yes | No | Yes |
| Set | No | Yes | No |
| Dictionary | Yes* | Yes | Keys: No |

*Dictionaries preserve insertion order in modern Python.

## 14. What is indexing?
Accessing an element by position.

```python
numbers = [10, 20, 30]
numbers[0]
# 10
```

## 15. What is slicing?
Selecting a portion of a sequence.

```python
numbers[1:4]
```

General syntax:
```python
[start:stop:step]
```

## 16. What is negative indexing?
Indexing from the end.

```python
numbers[-1]
```

## 17. What is `if-elif-else`?
Used for conditional execution.

```python
if age >= 18:
    print("Adult")
else:
    print("Minor")
```

## 18. Difference between `for` and `while`?
```text
for   → commonly iterates over a sequence/range
while → runs while a condition is True
```

## 19. What are `break`, `continue`, and `pass`?
```text
break    → exits the loop
continue → skips the current iteration
pass     → does nothing; placeholder
```

## 20. What is a function?
A reusable block of code.

```python
def add(a, b):
    return a + b
```

## 21. Parameter vs argument?
```python
def add(a, b):   # parameters
    return a + b

add(10, 20)      # arguments
```

## 22. Difference between `print()` and `return`?
```text
print() → displays a value
return  → sends a value back from a function
```

## 23. What is a default argument?
A parameter with a predefined value.

```python
def greet(name="User"):
    print(name)
```

## 24. What is a keyword argument?
An argument passed using the parameter name.

```python
student(age=25, name="Ayush")
```

## 25. What is a lambda function?
A small anonymous function.

```python
square = lambda x: x * x
square(5)
# 25
```

---

# 🟡 Intermediate Level

## 26. What is list comprehension?
A concise way to create lists.

```python
squares = [x**2 for x in range(5)]
```

## 27. What is dictionary comprehension?
A concise way to create dictionaries.

```python
squares = {x: x**2 for x in range(5)}
```

## 28. Difference between `append()` and `extend()`?
```python
numbers = [1, 2]
numbers.append([3, 4])
# [1, 2, [3, 4]]
```

`append()` adds the argument as one element.

```python
numbers = [1, 2]
numbers.extend([3, 4])
# [1, 2, 3, 4]
```

`extend()` adds elements individually.

## 29. Difference between `remove()`, `pop()`, and `del`?
```text
remove() → removes a specified value
pop()    → removes and returns an element
del      → deletes an item, slice, or variable
```

## 30. Difference between `sort()` and `sorted()`?
```python
numbers.sort()
```
Sorts in place.

```python
sorted(numbers)
```
Returns a new sorted list.

## 31. What is unpacking?
Assigning elements of an iterable to multiple variables.

```python
a, b, c = [10, 20, 30]
```

## 32. What are `*args`?
Accepts a variable number of positional arguments.

```python
def add(*args):
    return sum(args)
```

Inside the function, `args` is a tuple.

## 33. What are `**kwargs`?
Accepts a variable number of keyword arguments.

```python
def show(**kwargs):
    print(kwargs)
```

Inside the function, `kwargs` is a dictionary.

## 34. What is variable scope?
Scope defines where a variable can be accessed.

A common model is **LEGB**:
```text
Local → Enclosing → Global → Built-in
```

## 35. What is a local variable?
A variable created inside a function.

```python
def test():
    x = 10
```

## 36. What is a global variable?
A variable defined outside a function.

```python
x = 10

def test():
    print(x)
```

## 37. What is exception handling?
Handling runtime errors using `try` and `except`.

```python
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero")
```

## 38. What are `try`, `except`, `else`, and `finally`?
```text
try     → code that may raise an exception
except  → handles the exception
else    → runs if no exception occurs
finally → runs whether an exception occurs or not
```

## 39. What is `raise`?
Used to explicitly raise an exception.

```python
raise ValueError("Invalid value")
```

## 40. What is a module?
A Python file containing reusable code.

```python
import math
```

## 41. What is a package?
A way of organizing related Python modules into a directory structure.

## 42. What is `__name__ == "__main__"`?
It checks whether a file is being run directly.

```python
if __name__ == "__main__":
    print("Program started")
```

## 43. What is shallow copy?
Creates a new outer object, while nested objects may still be shared.

```python
import copy
b = copy.copy(a)
```

## 44. What is deep copy?
Recursively copies nested objects.

```python
import copy
b = copy.deepcopy(a)
```

## 45. Assignment vs copy?
```python
b = a
```
Both names refer to the same object.

```python
b = a.copy()
```
Creates a separate copy when supported.

## 46. What is an iterator?
An object that returns values one at a time using `__next__()`.

```python
numbers = iter([10, 20, 30])
next(numbers)
# 10
```

## 47. What is a generator?
A function that produces values lazily using `yield`.

```python
def numbers():
    yield 1
    yield 2
```

## 48. Difference between `yield` and `return`?
```text
return → ends the function and returns a value
yield  → pauses the function and produces a value
```

## 49. What is `map()`?
Applies a function to each item.

```python
result = list(map(lambda x: x * 2, [1, 2, 3]))
```

## 50. What is `filter()`?
Keeps elements for which a condition is true.

```python
result = list(filter(lambda x: x % 2 == 0, [1, 2, 3, 4]))
```

## 51. What is `zip()`?
Combines elements from multiple iterables.

```python
list(zip(["A", "B"], [20, 25]))
# [('A', 20), ('B', 25)]
```

---

# 🔴 Advanced Level

## 52. What is OOP?
Object-Oriented Programming organizes programs around classes and objects.

Main concepts:
```text
Encapsulation
Inheritance
Polymorphism
Abstraction
```

## 53. What is a class?
A blueprint for creating objects.

```python
class Student:
    pass
```

## 54. What is an object?
An instance of a class.

```python
student1 = Student()
```

## 55. What is `__init__()`?
Initializes object attributes when an object is created.

```python
class Student:
    def __init__(self, name):
        self.name = name
```

## 56. What is `self`?
Refers to the current object instance.

## 57. What is inheritance?
Allows a child class to acquire attributes and methods from a parent class.

```python
class Animal:
    def speak(self):
        print("Sound")

class Dog(Animal):
    pass
```

## 58. What is polymorphism?
The same interface can behave differently for different objects.

## 59. What is encapsulation?
Bundling data and methods together while controlling access to internal details.

## 60. What is abstraction?
Exposing important functionality while hiding unnecessary implementation details.

## 61. What is method overriding?
A child class provides its own implementation of a parent method.

```python
class Animal:
    def speak(self):
        print("Sound")

class Dog(Animal):
    def speak(self):
        print("Bark")
```

## 62. What is multiple inheritance?
A class inherits from more than one parent class.

```python
class A:
    pass

class B:
    pass

class C(A, B):
    pass
```

## 63. What is MRO?
MRO stands for **Method Resolution Order**. It defines the order in which Python searches classes for methods and attributes.

```python
C.mro()
```

## 64. What are magic/dunder methods?
Special methods whose names begin and end with double underscores.

Examples:
```python
__init__()
__str__()
__len__()
```

## 65. What is a decorator?
A function that modifies or extends another function's behavior.

```python
def decorator(func):
    def wrapper():
        print("Before")
        func()
    return wrapper
```

## 66. What is a closure?
A function that remembers variables from its enclosing scope.

```python
def outer(x):
    def inner():
        return x
    return inner

f = outer(10)
f()
# 10
```

## 67. What is a context manager?
Manages setup and cleanup automatically, commonly with `with`.

```python
with open("file.txt") as f:
    data = f.read()
```

## 68. What is garbage collection?
Automatic reclamation of memory from objects that are no longer needed.

## 69. What is reference counting?
Python tracks how many references point to an object. When an object is no longer reachable, its memory can be reclaimed.

## 70. What is the GIL?
The Global Interpreter Lock in CPython allows only one thread at a time to execute Python bytecode within a process.

## 71. Multithreading vs multiprocessing?
```text
Multithreading  → multiple threads in one process
Multiprocessing → multiple processes
```

## 72. What is a virtual environment?
An isolated Python environment for a project.

```bash
python -m venv venv
```

## 73. What is `pip`?
Python's package installer.

```bash
pip install pandas
```

## 74. What is PEP 8?
PEP 8 is the Python style guide for readable and consistent code.

## 75. What is the difference between `del` and garbage collection?
`del` removes a name/reference. Garbage collection is the broader process of reclaiming memory from objects that are no longer reachable.

---

# ⭐ Most Important Python Interview Topics

- Python basics and data types
- Mutable vs immutable
- List, tuple, set, dictionary
- Indexing and slicing
- Conditions and loops
- Functions
- Parameters and arguments
- `return` vs `print()`
- Lambda functions
- List/dictionary comprehensions
- `append()` vs `extend()`
- `sort()` vs `sorted()`
- `*args` and `**kwargs`
- Scope and LEGB
- Exception handling
- Modules and packages
- Shallow vs deep copy
- Iterators and generators
- `yield` vs `return`
- `map()`, `filter()`, `zip()`
- OOP concepts
- Classes and objects
- `self` and `__init__()`
- Inheritance
- Polymorphism
- Encapsulation
- Abstraction
- Method overriding
- Decorators
- Context managers
- GIL
- Multithreading vs multiprocessing
- Virtual environments

---

# 📌 Suggested Preparation Order

```text
Beginner
   ↓
Data Types
   ↓
Lists / Tuples / Sets / Dictionaries
   ↓
Indexing & Slicing
   ↓
Conditions & Loops
   ↓
Functions
   ↓
Intermediate
   ↓
Comprehensions
   ↓
Lambda / map / filter / zip
   ↓
Exception Handling
   ↓
Scope
   ↓
Copying
   ↓
Iterators & Generators
   ↓
Advanced
   ↓
OOP
   ↓
Inheritance / Polymorphism
   ↓
Decorators
   ↓
Context Managers
   ↓
GIL / Multithreading / Multiprocessing
```

> **Interview Tip:** For each important topic, prepare the **definition + syntax + small code example + output**. For Data Analyst interviews, give extra attention to lists, dictionaries, functions, comprehensions, exception handling, OOP basics, and Python coding problems.
