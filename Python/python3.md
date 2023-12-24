- [variables scope](#variables-scope)
  - [list comprehension scope](#list-comprehension-scope)
  - [class Scope](#class-scope)
  - [enclosing (nonlocal) scope](#enclosing-nonlocal-scope)
  - [local scope](#local-scope)
  - [global scope](#global-scope)
- [data types](#data-types)
  - [numeric types](#numeric-types)
  - [sequence types](#sequence-types)
  - [set types](#set-types)
  - [mapping type](#mapping-type)
  - [boolean type](#boolean-type)
  - [Binary Types](#binary-types)
  - [None Type](#none-type)
  - [Custom Types](#custom-types)
- [Characteristics](#characteristics)
  - [dynamically typed language](#dynamically-typed-language)
  - [interpreted language](#interpreted-language)


# variables scope
## list comprehension scope
Variables defined within a list comprehension have their own scope in Python 3. They are not accessible outside the comprehension.

```python
# This would raise a NameError in Python 3
# print(x)  
result = [x for x in range(5)]
```

## class Scope
Variables declared inside a class but outside any method have class scope. They are accessible within the class and its instances.

```python
class MyClass:
    class_variable = 40

    def print_class_variable(self):
        print(self.class_variable)

obj = MyClass()
obj.print_class_variable()  # Output: 40
```

## enclosing (nonlocal) scope
When a function is nested inside another function, the inner function has access to variables in the outer (enclosing) function's scope using the `nonlocal` keyword.

```python
def outer_function():
    outer_variable = 30

    def inner_function():
        nonlocal outer_variable
        print(outer_variable)

    inner_function()

outer_function()  # Output: 30
```

## local scope
Variables declared inside a function or a block (like an if statement or a loop) have a local scope. They are only accessible within that function or block.

```python
def my_function():
    local_variable = 20
    print(local_variable)

my_function()  # Output: 20
# This would raise a NameError since local_variable is not accessible here
# print(local_variable)
```

Local scope objects can be synced with global scope objects using keywords such as global.

```python
# Global variable
global_variable = 10

def modify_global_variable():
    # Use the global keyword to indicate that we want to refer to the global variable
    global global_variable
    # Modify the global variable
    global_variable = 20

# Call the function to modify the global variable
modify_global_variable()

# Print the modified global variable
print(global_variable)
```

## global scope
Variables declared outside of any function or class have a global scope. They can be accessed from any part of the code, both within and outside functions or classes.

```python
global_variable = 10

def my_function():
    print(global_variable)

my_function()  # Output: 10
```


# data types
## numeric types
- `int`: Integer type (e.g., `42`)
- `float`: Floating-point type (e.g., `3.14`)
- `complex`: Complex number type (e.g., `2 + 3j`)

## sequence types
- `str`: String type (e.g., `'Hello, World!'`)
- `list`: List type (e.g., `[1, 2, 3]`)
- `tuple`: Tuple type (e.g., `(1, 2, 3)`)
- `range`: Range type (e.g., `range(5)`)

## set types
- `set`: Set type (e.g., `{1, 2, 3}`)
- `frozenset`: Immutable set type

## mapping type
- `dict`: Dictionary type (e.g., `{'key': 'value'}`)
  
## boolean type
- `bool`: Boolean type (`True` or `False`)

## Binary Types
- `bytes`: Immutable sequence of bytes (e.g., `b'hello'`)
- `bytearray`: Mutable sequence of bytes
- `memoryview`: A view object that exposes an array’s buffer interface

## None Type
- `None`: Represents the absence of a value or a null value

## Custom Types
- User-defined classes and objects

# Characteristics
## dynamically typed language
Type-checking can be done at two stages:

- Static - Data Types are checked before execution.
- Dynamic - Data Types are checked during execution.
  
Python is an interpreted language, executes each statement line by line and thus type-checking is done on the fly, during execution. Hence, Python is a Dynamically Typed Language.

## interpreted language
An Interpreted language executes its statements line by line. Languages such as Python, Javascript, R, PHP, and Ruby are prime examples of Interpreted languages. Programs written in an interpreted language runs directly from the source code, with no intermediary compilation step. ????

