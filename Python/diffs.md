- [Difference between Python 3 and Python 2](#difference-between-python-3-and-python-2)
  - [`print` keyword](#print-keyword)
  - [Storage of Strings](#storage-of-strings)
  - [Division of Integers](#division-of-integers)
  - [Exceptions](#exceptions)
  - [Variable Leakage](#variable-leakage)
  - [Iteration](#iteration)
  - [Ease of Syntax](#ease-of-syntax)
  - [Libraries](#libraries)
  - [Usage in today’s times](#usage-in-todays-times)
  - [Application](#application)
- [List vs NumPy Array](#list-vs-numpy-array)
  - [Typing](#typing)
  - [Mutability vs Immutability](#mutability-vs-immutability)
  - [Numerical operation](#numerical-operation)
  - [Memory Efficiency](#memory-efficiency)
  - [Build-in Methods](#build-in-methods)


# Difference between Python 3 and Python 2
## `print` keyword
Python3:

```python
print("Hello, World!")
```

Python2:
```python
print "Hello, World!"
```

## Storage of Strings
**Python 3**:

In Python 3, strings are Unicode by default. There is no separate Unicode string type, and the `str` type represents Unicode characters. If you want to represent ASCII characters, you can use the `b` prefix for bytes.

```python
unicode_string = "Hello, World!"  # Unicode string
bytes_string = b"Hello, World!"  # ASCII/binary string
```

**Python 2**:

In Python 2, strings are represented as ASCII by default. Unicode strings are indicated by the `u` prefix, and they are stored separately from ASCII strings. The default string type is ASCII, which means that if you want to work with Unicode characters, you need to use the `u` prefix or the `unicode()` function.

```python
ascii_string = "Hello, World!"  # ASCII string
unicode_string = u"Hello, World!"  # Unicode string
```

## Division of Integers
**Python 3**:

On the division of two integers, we get a floating-point value in Python 3. For instance, 7/2 yields 3.5 in Python 3.

**Python 2**:
On the division of two integers, we get an integral value in Python 2. For instance, 7/2 yields 3 in Python 2.

## Exceptions
**Python 3**:

In Python 3, exceptions are enclosed in parentheses.

**Python 2**:

In Python 2, exceptions are enclosed in notations.

## Variable Leakage
In both Python 2 and Python 3, a variable declared within a loop remains accessible outside the loop's scope:

```python
for x in range(10):
    i = x

print(i)  # Output: 9
```

However, there is a subtle difference when it comes to list comprehensions. In Python 2, a variable defined within a list comprehension can be accessed from the outer scope, whereas in Python 3, it is confined to the comprehension's scope:

```python
# Python 2
result_2 = [x for x in range(5)]
print(x)  # Output: 4

# Python 3
result_3 = [x for x in range(5)]
# The next line would raise a NameError in Python 3
# print(x)
```

## Iteration
In Python 3, the new `Range()` function was introduced to perform iterations. In Python 2, the `xrange()` function has been defined for iterations.

## Ease of Syntax
Python 3:

Python 3 has an easier syntax compared to Python 2.

## Libraries
A lot of libraries are created in Python 3 to be strictly used with Python 3.

## Usage in today’s times
Python 2 is no longer in use since 2020.

## Application
Python 2 was mostly used to become a DevOps Engineer. It is no longer in use after 2020.



# List vs NumPy Array
## Typing
Lists in Python can hold elements of different data types. 

NumPy arrays have a fixed data type. All elements within a NumPy array must be of the same data type, which makes them more memory-efficient for numerical operations.

## Mutability vs Immutability
Python lists are highly flexible, allowing easy dynamic modifications, such as adding, removing, or modifying elements. They can change in size dynamically. In contrast, NumPy arrays, once created, have a fixed size, requiring the creation of a new array for resizing. NumPy arrays are mutable, meaning you can modify their elements in place.

## Numerical operation
NumPy arrays are designed for numerical operations and are more efficient than lists for mathematical computations. NumPy is implemented in C, making it faster for numerical operations. Lists are not optimized for numerical operations. If you need to perform extensive numerical computations, using a NumPy array might be more efficient.

## Memory Efficiency
NumPy arrays are more memory-efficient for large datasets, as they have a fixed data type and can be more compact in memory.

## Build-in Methods
Lists come with a variety of built-in methods, such as `append()`, `extend()`, `remove()`, `pop()`, etc., making them versatile and easy to work with.