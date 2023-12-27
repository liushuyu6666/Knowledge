- [Variables Scope and Namespace](#variables-scope-and-namespace)
  - [all kinds of scope](#all-kinds-of-scope)
    - [list comprehension scope](#list-comprehension-scope)
    - [local scope](#local-scope)
    - [enclosing scope](#enclosing-scope)
    - [class Scope](#class-scope)
    - [global scope](#global-scope)
    - [build-in scope](#build-in-scope)
  - [scope resolution](#scope-resolution)
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
- [Modules, Package and Virtual Environment](#modules-package-and-virtual-environment)
  - [python module](#python-module)
  - [python package](#python-package)
  - [python virtual environment](#python-virtual-environment)
  - [build-in modules](#build-in-modules)
- [PEP (Python Enhancement Proposal)](#pep-python-enhancement-proposal)
  - [doc string](#doc-string)
- [JVM](#jvm)
  - [Python Memory Manager](#python-memory-manager)
    - [Object Allocation](#object-allocation)
    - [Reference Counting](#reference-counting)
    - [Garbage Collection](#garbage-collection)
    - [Memory Pool](#memory-pool)
    - [Memory Fragmentation](#memory-fragmentation)
- [Syntactic Sugar](#syntactic-sugar)
  - [Decorator](#decorator)
  - [Comprehensions](#comprehensions)
    - [Performing conditional filtering operations on the entire list](#performing-conditional-filtering-operations-on-the-entire-list)
    - [Combining multiple lists into one](#combining-multiple-lists-into-one)
    - [Flattening a multi-dimensional list](#flattening-a-multi-dimensional-list)
  - [Lambda function](#lambda-function)
- [Copy](#copy)
  - [shallow copy vs deep copy](#shallow-copy-vs-deep-copy)
- [iterable](#iterable)
  - [iterator](#iterator)
  - [generator](#generator)
  - [difference between iterator and generator](#difference-between-iterator-and-generator)
    - [Implementation](#implementation)
    - [Memory Usage](#memory-usage)
    - [syntax](#syntax)
  - [convert iterator to generator](#convert-iterator-to-generator)
- [data persistence](#data-persistence)
  - [python object serialization and deserialization](#python-object-serialization-and-deserialization)
    - [pickle](#pickle)
- [Command line and environment](#command-line-and-environment)
  - [PYTHONPATH](#pythonpath)
- [build-in functions](#build-in-functions)
- [python language services](#python-language-services)
  - [`.pyc`](#pyc)
- [operators](#operators)
  - [`*` asterisk operator](#-asterisk-operator)
- [argparse](#argparse)
  - [`*args`](#args)
  - [`**kwargs`](#kwargs)
- [OOP](#oop)
  - [inheritance](#inheritance)
    - [How do you access parent members in the child class?](#how-do-you-access-parent-members-in-the-child-class)
    - [How will you check if a class is a child of another class?](#how-will-you-check-if-a-class-is-a-child-of-another-class)


# Variables Scope and Namespace
In Python, a scope is a region of a program where a namespace is directly accessible. Namespaces define the mapping between names (variables, functions, classes, etc.) and their corresponding objects. 

## all kinds of scope
### list comprehension scope
Variables defined within a list comprehension have their own scope in Python 3. They are not accessible outside the comprehension.

```python
# This would raise a NameError in Python 3
# print(x)  
result = [x for x in range(5)]
```

### local scope
Variables declared inside a function or a block (like an if statement or a loop) have a local scope. They are only accessible within that function or block.

```python
def my_function():
    local_variable = 20
    print(local_variable)

my_function()  # Output: 20
# This would raise a NameError since local_variable is not accessible here
# print(local_variable)
```

Local scope objects can be overridden using the `global` keyword.

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

### enclosing scope
The enclosing scope is relevant when dealing with nested functions. It refers to the scope of the enclosing (outer) function in which a nested function is defined.

```python
def outer_function():
    outer_variable = 30

    def inner_function():
        nonlocal outer_variable
        print(outer_variable)

    inner_function()

outer_function()  # Output: 30
```

### class Scope
Variables declared inside a class but outside any method have class scope. They are accessible within the class and its instances.

```python
class MyClass:
    class_variable = 40

    def print_class_variable(self):
        print(self.class_variable)

obj = MyClass()
obj.print_class_variable()  # Output: 40
```

### global scope
Variables declared outside of any function or class have a global scope. They can be accessed from any part of the code, both within and outside functions or classes.

```python
global_variable = 10

def my_function():
    print(global_variable)

my_function()  # Output: 10
```

### build-in scope
The built-in scope contains names that are built into the Python language. These names are part of the Python standard library and include functions like `print()` and types like `list`.

## scope resolution
- Python modules namely 'math' and 'cmath' have a lot of functions that are common to both of them - `log10()`, `acos()`, `exp()` etc. To resolve this ambiguity, it is necessary to prefix them with their respective module, like `math.exp()` and `cmath.exp()`.
- Local scope objects can be overridden using the `global` keyword.



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

Both `set` and `frozenset` support set to set comparisons. Two sets are equal if and only if every element of each set is contained in the other (each is a subset of the other). A set is less than another set if and only if the first set is a proper subset of the second set (is a subset, but is not equal). A set is greater than another set if and only if the first set is a proper superset of the second set (is a superset, but is not equal).

Instances of `set` are compared to instances of `frozenset` based on their members. For example, `set('abc') == frozenset('abc')` returns `True` and so does `set('abc') in set([frozenset('abc')])`.

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


# Modules, Package and Virtual Environment
## python module
In a general sense, a Python module is often associated with a .py file. A Python module is a file containing Python code, and modules are typically organized into separate files to facilitate code organization, reuse, and maintainability.

## python package
In Python, a package is a way of organizing related Python modules into a directory hierarchy. A package can contain multiple Python files (modules) and subpackages, forming a hierarchical structure. This is a common practice for organizing code in larger Python projects.

## python virtual environment
A Python virtual environment provides an isolated and self-contained environment for a Python project, including its own Python interpreter and packages.

## build-in modules
- os
- math
- sys
- random
- re
- datetime
- JSON


# PEP (Python Enhancement Proposal)
A PEP is **an official design document** providing information to the Python community, or describing a new feature for Python or its processes. PEP 8 is especially important since it documents **the style guidelines** for Python Code. Apparently contributing to the Python open-source community requires you to follow these style guidelines sincerely and strictly.


## doc string
A `docstring` in Python is a string literal that occurs as the first statement in a module, function, class, or method definition. Its primary purpose is to provide documentation about the object it accompanies, such as the module, function, class, or method. `docstrings` are accessible through the `__doc__` attribute of the corresponding object.

Here's a simple example of a docstring in a Python function:

```python
def greet(name):
    """
    This function takes a name as an argument and prints a greeting message.
    
    Parameters:
    - name (str): The name of the person to greet.
    """
    print(f"Hello, {name}!")

# Accessing the docstring
print(greet.__doc__)
```

# JVM
## Python Memory Manager
The memory allocated by the manager is in form of a private heap space dedicated to Python. All Python objects are stored in this heap and being private, it is inaccessible to the programmer. The Python Memory Manager is an integral part of the Python Virtual Machine (PVM). It handles the management of the program's memory space, including 
1. the allocation of memory for objects, 
2. tracking of object references, and 
3. releasing memory that is no longer in use (garbage collection).

### Object Allocation
When you create objects in Python, such as integers, strings, lists, or custom objects, the memory manager is responsible for allocating memory to store those objects.

### Reference Counting
Python uses a reference counting mechanism to keep track of the number of references to each object. Every time a reference to an object is created (e.g., by assigning an object to a variable), the reference count is incremented. When a reference goes out of scope or is explicitly deleted, the reference count is decremented.

### Garbage Collection
In addition to reference counting, Python employs a garbage collector to identify and reclaim memory occupied by objects that are no longer reachable or referenced. This process helps automatically manage memory and prevent memory leaks.

### Memory Pool
Python uses a memory pool strategy to efficiently allocate and deallocate memory. **Small objects are grouped together in pools**, and the memory manager can allocate and deallocate entire blocks at a time, reducing the overhead associated with frequent small allocations.

### Memory Fragmentation
It organizes memory in a way that **minimizes fragmentation**, ensuring efficient use of available memory.

# Syntactic Sugar
## Decorator
In Python, a decorator is a special type of function that can be used to modify the behavior of another function or method. It can also access and manipulate the input variables of the function they decorate.

```python
def multiply_by(factor):  # The `multiply_by` decorator is defined to take a `factor` argument.
    def decorator(func):
        def wrapper(*args, **kwargs):  # The decorator returns a nested function (`wrapper`) that calls the original function (`func`) and then multiplies the result by the specified factor.
            result = func(*args, **kwargs)
            return result * factor
        return wrapper
    return decorator

# When the `@multiply_by(2)` syntax is used to apply the decorator to the `add_numbers` function, it effectively replaces `add_numbers` with the decorated version that multiplies the result by 2.
@multiply_by(2)
def add_numbers(a, b):
    return a + b

# Calling the decorated function
result = add_numbers(3, 4)

print("Result:", result)
```

output:

```txt
Result: 14
```


## Comprehensions
Comprehensions consist of list comprehension and dict comprehension.

### Performing conditional filtering operations on the entire list

```python
my_list = [2, 3, 5, 7, 11]
squared_list = [x**2 for x in my_list if x%2 != 0]    # list comprehension
squared_dict = {x : x**2 for x in my_list if x%2 != 0}    # dict comprehension
```

### Combining multiple lists into one

```python
a = [1, 2, 3]
b = [7, 8, 9]
[(x + y) for (x,y) in zip(a,b)]  # parallel iterators
# output => [8, 10, 12]
[(x,y) for x in a for y in b]    # nested iterators
# output => [(1, 7), (1, 8), (1, 9), (2, 7), (2, 8), (2, 9), (3, 7), (3, 8), (3, 9)] 
```

### Flattening a multi-dimensional list
```python
my_list = [[10,20,30],[40,50,60],[70,80,90]]
flattened = [x for temp in my_list for x in temp]
# output => [10, 20, 30, 40, 50, 60, 70, 80, 90]
```

## Lambda function
Lambda is an anonymous function in Python, that can accept any number of arguments, but can only have a single expression.

```python
# Without syntactic sugar
def add(x, y):
    return x + y

# With syntactic sugar (lambda function)
add = lambda x, y: x + y
```

# Copy

In Python, the assignment statement (`=` operator) does not copy objects. Instead, it creates a reference or a binding between the existing object and the target variable name. For example

```python
# Creating a list
original_list = [1, 2, 3]

# Assigning the list to a new variable
new_list = original_list

# Modifying the new list
new_list.append(4)

# Checking the original list
print(original_list)  # [1, 2, 3, 4]
```

However, for immutable objects (like integers, strings, and tuples), the `=` operator creates a new reference to the same object rather than copying the object itself. 

## shallow copy vs deep copy

When copying an array in Python, there are two main methods:

```python
import copy

original = []

shallow_copy = original[:]  # Shallow copy
deep_copy = copy.deepcopy(original)  # Deep copy
```

Shallow copying, done through `original[:]`, is notably faster than deep copying. In testing on Leetcode, shallow copying completes within approximately 1 second, whereas deep copying takes about 4 seconds.

However, a drawback of shallow copying is that while it creates a new list, any nested lists or objects within the original list remain referenced in the copied list. Modifications to these nested elements will affect both the original and copied lists, as they share the same objects.

# iterable
In Python, an iterable is an object that can be iterated (looped) over. It represents a collection of elements, and you can traverse through these elements one at a time.

## iterator
An iterator is an object. It remembers its state i.e., where it is during iteration. `__iter__()` method initializes an iterator. It has a `__next__()` method which returns the next item in iteration and points to the next element. Upon reaching the end of iterable object `__next__()` must return `StopIteration` exception.

## generator
In Python, a generator is a special type of iterable, similar to a list or a tuple. However, unlike lists and tuples, generators do not store all the values in memory at once. Instead, they generate values on the fly as you iterate over them. This makes generators more memory-efficient, especially for large datasets.

The `yield` statement is used in a function to turn it into a generator. When a function with `yield` is called, it returns a generator object. Here's how `yield` works in the code:

1. Function Definition:
```python
def simple_generator():
    yield 1
    yield 2
    yield 3
```

2. Generator Object Creation:
When you call the generator function, it doesn't execute immediately. Instead, it returns a generator object without running the code inside the function.

```python
my_generator = simple_generator()
```

3. Iteration:
When you iterate over the generator using a loop or the `next()` function, the function is executed until it encounters a `yield` statement. The value following `yield` is produced, and the function's state is saved.

```python
value1 = next(my_generator)  # Function runs until the first yield
print(value1)  # Output: 1

value2 = next(my_generator)  # Function resumes from the last yield
print(value2)  # Output: 2
```

4. Stop Iteration:
When the function completes or encounters a `return` statement, a `StopIteration` exception is raised to signal the end of the iteration.

```python
value3 = next(my_generator)  # Function resumes from the last yield
print(value3)  # Output: 3

# Further calls will raise StopIteration
```

5. Iteration with a Loop:
You can iterate over the generator using a for loop, and it will automatically handle the StopIteration exception.

```python
for value in my_generator:
    print(value)
```

## difference between iterator and generator
### Implementation
An iterator is an object that implements the iterator protocol by having `__iter__()` and `__next__()` methods. A generator is a special type of iterator created using a function with the `yield` statement. It automatically implements the iterator protocol.

### Memory Usage
Iterators can be memory-intensive as they might store the entire sequence of elements in memory. Generators are more memory-efficient as they produce values on-the-fly and do not store the entire sequence in memory.

### syntax
The creation of an iterator typically involves creating a class with the necessary methods. You have explicit control over the iteration process, and you can manually call the `__next__()` method to retrieve elements. 

Generators use a simpler syntax with functions and the `yield` keyword. Generators provide a convenient way to iterate over a sequence without explicitly defining an iterator class. The `yield` statement suspends the function's state between calls.

## convert iterator to generator
In many cases, an iterator can be converted into a generator, especially when the iterator is based on a class with an `__iter__()` method and a `__next__()` method. The process involves rewriting the class as a generator function using the `yield` statement.


# data persistence
## python object serialization and deserialization
Serializing an object refers to transforming it into a format that can be stored, so as to be able to deserialize it, later on, to obtain the original object.

### pickle
**pickling**: Pickling is the name of the serialization process in Python. Any object in Python can be serialized into a byte stream and dumped as a file in the memory. The process of pickling is compact but pickle objects can be compressed further. Moreover, pickle keeps track of the objects it has serialized and the serialization is portable across versions. The function used for the above process is `pickle.dump()`.

**unpickling**: Unpickling is the complete inverse of pickling. It deserializes the byte stream to recreate the objects stored in the file and loads the object to memory. The function used for the above process is `pickle.load()`.

# Command line and environment
## PYTHONPATH
`PYTHONPATH` is an environment variable in Python that tells the interpreter where to look for Python modules when you import them in your code. It is a list of directory names, with the Python interpreter searching for modules in the directories specified in the order they appear in the `PYTHONPATH`.

When you try to import a module in your Python script or interactive session, Python searches for that module in the following locations:

1. The current directory.
2. Directories listed in the `PYTHONPATH` environment variable.
3. 
If the module is not found in any of these locations, Python will raise an `ImportError`.

In general, when you are working with virtual environments in Python, it's often unnecessary and can even be counterproductive to set or modify the `PYTHONPATH` environment variable directly.

# build-in functions
1. `help()` function in Python is used to display the documentation of modules, classes, functions, keywords, etc. If no parameter is passed to the help() function, then an interactive help utility is launched on the console.
2. `dir()` function tries to return a valid list of attributes and methods of the object it is called upon. It behaves differently with different objects, as it aims to produce the most relevant data, rather than the complete information.

# python language services
## `.pyc`
A `.pyc` file is a compiled Python file. When you run a Python script or import a module, the Python interpreter translates the source code into bytecode, which is a lower-level representation of the code that is more efficiently executed by the Python interpreter. The bytecode is then stored in `.pyc` files to speed up future executions of the same code.

Here's a brief overview of how the process works:

1. Compilation: When a Python script or module is executed, the Python interpreter compiles the source code into a platform-independent bytecode.
2. Bytecode Files (`.pyc`): The resulting bytecode is saved to a `.pyc` file in a special `__pycache__` directory. This directory is created automatically in the same directory as the source file or in the Python's system-wide cache directory, depending on the Python version and configuration.
3. Timestamp Checking: Before executing a Python script or importing a module, the interpreter checks the timestamps of the source `.py` file and the corresponding `.pyc` file. If the source file has been modified more recently than the `.pyc` file, the Python interpreter recompiles the source code and updates the `.pyc` file.
4. Execution: If the `.pyc` file is up-to-date, the interpreter uses the bytecode from the `.pyc` file for faster execution instead of recompiling the source code.

Python only generates `.pyc` files for modules that are explicitly imported in your code. When you execute a Python script directly, without importing it as a module in another script, the interpreter does not create a corresponding `.pyc` file.

1. Files You Run Directly: If you run a Python script directly (e.g., using `python script.py` from the command line), and the script does not import any modules, Python does not generate a `.pyc` file for that script.
```python
# script.py
print("Hello, World!")
```
If you run `python script.py`, Python doesn't create a `__pycache__` directory or a `.pyc` file for `script.py` because it's not imported as a module.
2. Files You Import: When you import a module in another script, Python creates a `.pyc` file for the imported module. This `.pyc` file is stored in a `__pycache__` directory, either in the same directory as the source module or in the Python's system-wide cache directory.
```python
# module.py
print("Module has been imported.")

# main_script.py
import module
```
If you run `python main_script.py`, Python creates a `__pycache__` directory (if not already present) and a `.pyc` file for `module.py`.


# operators
## `*` asterisk operator
In Python, the `*` (asterisk) operator is used for sequence unpacking, allowing you to extract elements from iterable objects such as lists, tuples, and strings.

1. unpacking: When used in a function call or in an iterable unpacking expression, `*` is used to unpack the elements of an iterable.

```python
# Unpacking in function call
values = [1, 2, 3, 4, 5]
print(*values)  # Equivalent to print(1, 2, 3, 4, 5)

# Unpacking in iterable unpacking expression
first, *rest = [1, 2, 3, 4, 5]
print(first)  # 1
print(rest)   # [2, 3, 4, 5]
```

2. Extended Unpacking (Python 3.5 and later): In a function signature, * is used to indicate that a function can accept a variable number of positional arguments.

```python
def my_function(arg1, arg2, *args):
    print(arg1)
    print(arg2)
    print(args)

my_function(1, 2, 3, 4, 5)
```

3. Repetition (Multiplication): Outside of unpacking contexts, * is used for multiplication.
```python
result = [1, 2] * 3  # Equivalent to [1, 2, 1, 2, 1, 2]
```

4. Keyword-Only Argument Separator (Python 3): In a function signature, * is used to indicate the start of keyword-only arguments.
```python
def my_function(arg1, arg2, *, kwarg1, kwarg2):
    print(arg1)
    print(arg2)
    print(kwarg1)
    print(kwarg2)

my_function(1, 2, kwarg1=3, kwarg2=4)
```



# argparse
## `*args`
`*args` is a special syntax used in the function definition to pass variable-length arguments.
```python
def multiply(a, b, *argv):
   mul = a * b
   for num in argv:
       mul *= num
   return mul
print(multiply(1, 2, 3, 4, 5)) #output: 120
```
## `**kwargs`
`**kwargs` is a special syntax used in the function definition to pass variable-length keyworded arguments.
```python
def tellArguments(**kwargs):
   for key, value in kwargs.items():
       print(key + ": " + value)
tellArguments(arg1 = "argument 1", arg2 = "argument 2", arg3 = "argument 3")
#output:
# arg1: argument 1
# arg2: argument 2
# arg3: argument 3
```

# OOP
## inheritance
### How do you access parent members in the child class?

1. By using Parent class name: You can use the name of the parent class to access the attributes as shown in the example below:

```python
class Parent(object):  
   # Constructor
   def __init__(self, name):
       self.name = name    
 
class Child(Parent): 
   # Constructor
   def __init__(self, name, age):
       Parent.name = name
       self.age = age
 
   def display(self):
       print(Parent.name, self.age)
 
# Driver Code
obj = Child("Interviewbit", 6)
obj.display()
```

2. By using super(): The parent class members can be accessed in child class using the super keyword.

```python
class Parent(object):
   # Constructor
   def __init__(self, name):
       self.name = name    
 
class Child(Parent):
   # Constructor
   def __init__(self, name, age):         
       ''' 
       In Python 3.x, we can also use super().__init__(name)
       ''' 
       super(Child, self).__init__(name)
       self.age = age
 
   def display(self):
      # Note that Parent.name cant be used 
      # here since super() is used in the constructor
      print(self.name, self.age)
  
# Driver Code
obj = Child("Interviewbit", 6)
obj.display()
```

### How will you check if a class is a child of another class?
This is done by using a method called `issubclass()` provided by python. The method tells us if any class is a child of another class by returning true or false accordingly.

```python
class Parent(object):
   pass   
 
class Child(Parent):
   pass   
 
# Driver Code
print(issubclass(Child, Parent))    #True
print(issubclass(Parent, Child))    #False
```

We can check if an object is an instance of a class by making use of `isinstance()` method:

```python
obj1 = Child()
obj2 = Parent()
print(isinstance(obj2, Child))    #False 
print(isinstance(obj2, Parent))   #True 
```