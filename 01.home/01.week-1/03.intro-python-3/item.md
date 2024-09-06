---
title: '1.3 Intro Python 3'
date: '16-05-2025 06:10'
taxonomy:
    category:
        - labs
---

## Introduction to Python

[Python](https://www.python.org/) is a general-purpose, interpreted, high-level programming language. The syntax of the language has been optimized to emphasize code readability, as well as brevity.

Note: though there are multiple versions of python we will exclusively use **Python3**


### Variables & Strings

A variable is a container for data

```python3
data = "hello world"
```

A variable is created when we put data in it. Once created we can ask Python for information about the data

```python3
type(data)
```

The above line returns `str`, short for `string`, a datatype representing characters surrounded by quotes.

Note: quotes must be balanced. Below we are missing a closing quote so Python will complain (`SyntaxError: unterminated string literal (detected at line 1)`)

```python3
data = "hello word
```

We can ask Python how long the string stored at `data` with `len()`

```python3
len(data)
```


### Built-in String Methods

Return a part of the string (referred to as "string slicing") with the following

```python
data[:3]
```

One can see what other operations are possible with `data` by typing `data.` and then hitting the TAB key

```python
data.
```

From this list, one can type out any of the functions followed by a `?` and hit ENTER to see a brief description of what it does.

To convert the string to a capitalized version of itself

```python
data.upper()
```

Note that running `.upper()` on `data` does not permanently alter the data stored there

```python
data
```

To **replace** the lowercase version of the string at `data` with a capitalized version

```python
data = data.upper()
```

```python
data
```


### Integers & Floats

There are two basic types of numbers:

* integers
* floating point numbers (floats for short)

Integers are any whole number (positive or negative)

```python
data = 5
type(data)
```

floats are any number with a decimal point

```python
data = 4.0
type(data)
```


### Lists

A compound data type used to group multiple values together. A `list` is written as a series of comma-separated items between square brackets. They do not need to be of uniform datatype

```python
data = ['spam', 'eggs', 100, 1234]
data
```

Individual items in a `list` are referenced by their `index`, or location in the `list`. We can reference individual items by entering the variable and the position (counting from 0)

```python
data[0] # the first item in the list
```

```python
data[3]
```

```python
data[:2] # a list can be sliced just like a string
```

Individual items/elements in a string can be modified (or updated) as follows

```python
data[1] = 2
data
```

One can make Python determine the length (or size) of `list` by calling `len()` on it.

```python
len(data)
```


### Adding Elements to a List

#### insert

add an element to a `list` at index

```python
h = [ 'this', 'is', 'a', 'list' ]
h.insert(3, 'great')
h
```

#### append

add an element to the end of a `list`

```python
h.append('certainly')
h
```

### Removing Elements From a List

There are two basic ways to remove an element from a `list`:

* `pop`
* `remove`


#### pop

remove and return an item from a `list` at index. If no index is specified `pop` removes and returns the last item of a `list`

```python
h = ['this', 'is', 'a', 'great', 'list', 'certainly', 'the', 'best', 'list']
h.pop()
h
```

#### remove

remove the first occurrence of value

```python
h
h.insert(2, 'is') # insert a duplicate word
h # confirm the duplicate
```

```python
h.remove('is')
h
```

## loops

There are two basic types of loops in Python:

* `while`
* `for`

### while

A `while` loop executes a block of code repeatedly until a condition has been met. In Python we use whitespace to denote blocks (multiple lines of related code) with 4 spaces (or 1 tab)

```python
data = 0

while data < 25:
    print(data)
    data+=1

print("done!")
```

Above we initialize a variable (`data`) to 0. Our `while` loop block has two lines:

1. `print` the current value of `data`
2. `increment` (adds 1 to) `data`

These two lines repeat until the current value of `data` is not less than 25


### for

A for loop iterates across a sequence of values, performing a block of code for every item in the sequence. I could rewrite our previous example with a `for` loop like so

```python
for i in range(25):
    print(i)

print("done!")
```


## import

One of the benefits of using Python is its robust "standard library," or built-in tools that available by default whenever one is programming in Python. `len()`, `while`, `for`, and `print()` are some examples.

There are lots of modules and packages that other programmers have written which we can incorporate into our own code by using `import`. For example

```python
import math

math.pi
```

Which enables a programmer to easily generate the first few digitsl of `pi`

We can `import` the entire module/package or we can just get something specific from it

```python
from math import pi

pi
```
