# Python - Beginner

## Week 1 Part 1 - The Programming Experience

### Hello World

```python
# the hello world program
print("hello world")
```

## Week 2 Part 1 - Simple Calculations

### Program Statements

```python
# two statements in one line
print("hello "); print("world")

# one statement in three lines
print(              \
    "hello world"   \
    )

# '\' cannot be used inside quotes
print("hello "
    "world")

# triple-quote should only be used for docstrings, not for multi-line comments
docstring = """ hello world """
```

### Simple Numeric Statements

```python
# use floor division to get the largest integer less than or equal to the answer
answer = 14 // 3  # 4
answer = -14 // 3  # -5
```

### User Input from the Console

```python
# we can send the output (prompt) to the screen inside the input statement
user_input = input("hello ")  # world
print(user_input)  # hello world
```

### String, print(), and a Console Example

```python
# use number in print statement with commas
print("hello", 3.14, "world")  # hello 3.14 world

# convert number to string and concatenate
print("hello " + str(3.14) + " world")  # hello 3.14 world

# if you don't want a newline
print("hello ", end='')
print("world")  # hello world
```

### Formatted Output with f-strings

```python
# combine literal strings and variable strings
hello = "hello"
hello_world = f"{hello} world"
print(hello_world)  # hello world

# change the precision of decimal output
pi = 3.1415
output = f"{pi:.3f}"
print(output)  # 3.142
```

### Parameters, Arguments and Function Signatures

```python
# the signature of add() is the add(a, b) along with the docstring
def add(a, b):
    """ Adds two arguments and returns the sum """
    temp = a + b
    return temp
```

### Locals and Functional Return

```python
# convert string to int
answer = int(input())
```

## Week 2 Part 2 - Control Flow

### The if Statement

```python
# use parenthesis to isolate the condition visually
if answer < 0:
    print("hello")
if (answer < 0):
    print("world")

# end a program (not preferred)
import sys

sys.exit()
```

### The else Block

```python
# don't place anything on the same line after a colon
if (answer < 0):
    print("hello")
else:
    print("world")
```

### elif

```python
# do not use progressive indentation
if (answer < 0):
    print("hello")
elif (answer == 0):
    print("world")
else:
    print("hello world")
```

### Relational Expressions

```python
# there is no reason to put a constant True or False into a condition
answer = True
answer = False
```

## Week 3 Part 1 - Program Flow

### What's up with **name** == "**main**"?

```python
# the python interpreter sets a special variable called __name__ to __main__
if __name__ == "__main__":
    print("hello world")
```

### Overview of Structures

```python
# for loop structure
for <iteration_var> in <sequence>:
    print("hello world")

# while loop structure
while <test>:
    print("hello world")
```

### while Loops

```python
# for loop example
for i in range(0, 5):
    print("hello world")  # printed five times

# if answer is False, then not answer is True
answer = False
while not answer:
    print("hello world")  # printed only once
    answer = True
```

### break Out of Iteration Structure

```python
# the break statement can be used to exit from a loop body instantly
while True:
    print("hello world")  # printed only once
    break
```

### continue With Iteration Structure

```python
# as soon as the continue is reached, control will pass back to the top
for i in range(0, 5):
    continue
    print("hello world")  # not printed
```

### Catching Exceptions

```python
# exceptions should be used to catch errors that you are expecting
try:
    user_input = int(input())
except ValueError:
    # is not an integer
else:
    # is an integer
```

### Numeric Types

```python
# cube
answer = 3
answer = answer ** 3  # 27
```

### Variable Assignment in Python

```python
# the variable name is free to point at any object
answer = 3
answer = "hello world"
```

### Converting Between Numeric Data Types

```python
# slicing
answer = "hello 3.14 world"
pi = float(answer[6:10])  # 3.14

# int() and float() will happily ignore leading or trailing spaces
pi = float("    3.14    ")  # 3.14
```

## Week 3 Part 2 - Debugging and Functions

### Functions that do Nothing

```python
# python will complain if we write a function definition with no statements
def useless_function():
    pass
```

## Week 4 Part 1 - Data Containers

### Collection and Sequence Objects

```python
# strings are iterables
my_string = "hello world"
print(id(my_string))  # the "identity" of the object
for char in my_string:
    print(char)

# a list is a collection of object which is ordered and mutable
my_list = [3, 0, 1, 4]
print(type(my_list))  # the type of the object
print(my_list)  # [3, 0, 1, 4]
my_list[0] = 1
print(my_list)  # [1, 0, 1, 4]

# a tuple is similar to a list, but it is immutable
my_tuple = (3, 0, 1, 4)
print(my_tuple)  # (3, 0, 1, 4)
my_tuple[0] = 1  # error

# the items in a set must be unique and hashable and are sorted
my_set = {3, 0, 1, 4}
print(my_set)  # {0, 1, 3, 4}
my_set.add(1)
print(my_set)  # {0, 1, 3, 4}
for item in my_set:
    print(item)
my_set = {[3, 0], [1, 4]}  # error
my_set = {(3, 0), (1, 4)}
print(my_set)  # {(1, 4), (3, 0)}

# a dict organizes data values by association key:value pairs
my_dict = {}  # creates an empty dict object
my_dict["h"] = "ello"
my_dict["w"] = "orld"
print(my_dict)  # {'h': 'ello', 'w': 'orld'}
for key in my_dict:
    print(key, my_dict[key])
```

### Characters and Strings

```python
# the length (size) of a string
my_string = "hello world"
print(len(my_string))  # 11

# ascii representations of characters
print(ord("h"), ord("e"), ord("l"), ord("l"), ord("o"))  # 104 101 108 108 111

# creating characters from ascii or unicode values
print(chr(104), chr(101), chr(108), chr(108), chr(111))  # h e l l o
```

### Substring, Slicing and Mode Concatenation

```python
# pulling a character from a string
my_string = "hello world"
print(my_string[6])  # w

# python does not allow you to change a string value
my_string[0] = "i"  # error

# extracting a substring from a larger string
print(my_string[6:11])  # world
print(my_string[-5:])  # world

# changing a character in a string
my_string = my_string[:5] + "_" + my_string[6:]
print(my_string)  # hello_world
```

## Week 4 Part 2 - Data Containers and Looping

### Lists

```python
# getting a sublist from a larger list
my_list = [3, 0, 1, 4]
print(my_list[1:3])  # [0, 1]

# list concatenation
my_list = my_list + [1, 5, 9, 2]
print(my_list)  # [3, 0, 1, 4, 1, 5, 9, 2]

# the number of elements in a list
print(len(my_list))  # 8

# the del statement
del my_list[0]
print(my_list)  # [0, 1, 4, 1, 5, 9, 2]
del my_list[0:3]
print(my_list)  # [1, 5, 9, 2]
del my_list[:]
print(my_list)  # []

# unpacking lists (and strings)
my_list = [3, 0, 1, 4]
one, two, three, four = my_list
print(f"{one} {two} {three} {four}")  # 3 0 1 4
my_string = "hello"
one, two, three, four, five = my_string
print(f"{one} {two} {three} {four} {five}")  # h e l l o

# last loading of lists
my_list = [3, 0, 1, 4] * 2
print(my_list)  # [3, 0, 1, 4, 3, 0, 1, 4]

# the append() method
my_list = []
my_list.append(3)
my_list.append(0)
my_list.append(1)
my_list.append(4)
print(my_list)  # [3, 0, 1, 4]

# list nesting
my_list.append([3, 0, 1, 4])
print(my_list)  # [3, 0, 1, 4, [3, 0, 1, 4]]
print(my_list[4])  # [3, 0, 1, 4]
print(my_list[4][0])  # 3
```

### The For Loop

```python
# the third number in range is called the iteration step
for i in range(0, 5, 2):
    print("hello world")  # printed three times

# the "don't care" variable
for _ in range(0, 5, 2):
    print("hello world")  # printed three times
```

### Tuples

```python
# instantiating a list using the comprehension notation
my_list = [i for i in range(1, 5)]
print(my_list)  # [1, 2, 3, 4]

# tuples can be defined without parentheses
my_tuple = 3, 0, 1, 4
print(my_tuple)  # (3, 0, 1, 4)

# instantiating a tuple using the comprehension notation
my_tuple = (i for i in range(1, 5))
print(my_tuple)  # <generator object <genexpr> at 0x000002664C519510>
my_tuple = tuple(i for i in range(1, 5))
print(my_tuple)  # (1, 2, 3, 4)
```

## Week 5 Part 1 - Logical Operators, Truth Table and Containment Operator

### Looping Through Lists and Strings

```python
# for loops don't require the range() function
for my_character in "hello world":
    print(f"{my_character} ", end='')  # h e l l o   w o r l d

# since lists can be heterogeneous, we can do this
for item in ["hello", 3.14, "world"]:
    print(f"{item} ", end='')  # hello 3.14 world

# testing the type of a variable
for item in ["hello world", 3.14, []]:
    item_type = type(item)
    if item_type == float:
        print(f"\"{item}\" is a float")  # "3.14" is a float
    elif item_type == str:
        print(f"\"{item}\" is a string")  # "hello world" is a string
    else:
        print(f"\"{item}\" is something else")  # "[]" is something else
```

### Boolean and Containment Operations

```python
# not a == b is interpreted as not (a == b), and a == not b is a syntax error

# tests if string_1 is a substring of string_2
print("hello" in "world")  # false
print("hello" in "hello world")  # true

# used similarly with lists
print("hello" in ["hello", 3.14])  # true
print("3.14" in ["hello", 3.14])  # false
```

### A Nice Example

```python
# you can avoid using logical operators with this shortcut notation
print(10 < len("hello world") < 12)  # true

# string methods
print("hello".isalpha())  # true
print("3014".isdigit())  # true
print("hello3014".isalnum())  # true
print("hello".islower())  # true
print("HELLO".isupper())  # true
print("hello".upper())  # HELLO
print("HELLO".lower())  # hello
```

## Week 6 Part 1 - Dictionaries and Default Parameters

### Dictionaries

```python
# the python dict type looks much like a list of tuples (key, value)
my_dict = {}
my_dict["one"] = 1
my_dict["two"] = 2
my_dict["three"] = 3
my_dict["four"] = 4

# the in operator
print("one" in my_dict)  # True
print("five" in my_dict)  # False
```

### Looping Through Dictionaries

```python
# the key in each dict element is the thing over which we loop
for key in my_dict:
    print(key, end=" ")  # one two three four
for key in my_dict:
    print(my_dict[key], end=" ")  # 1 2 3 4

# don't use dict if you need an ordering
for key in sorted(my_dict):
    print(key, end=" ")  # four one three two

# items() gives you a way to pull out both keys and values in a single loop
for key, value in my_dict.items():
    print(f"{key}={value}", end=" ")  # one=1 two=2 three=3 four=4
```

### Default Parameters

```python
# sometimes we don't want to bother including arguments that rarely change
def say_hi(name, greeting="hi"):
    print(f"{greeting} name")
```

## Week 7 Part 1 - Arrays and Variable Scope

### Arrays

```python
# python has no built-in array type
```

### Globals

```python
# when a function wants to use and modify a global, it must declare the global
def print_pi():
    global PI
    PI = 3.14
    print(PI)  # 3.14


PI = 0
print_pi()
```
