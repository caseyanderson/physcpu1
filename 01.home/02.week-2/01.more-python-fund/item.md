---
title: '2.1 More Python Fundamentals'
date: '23-05-2024 06:00'
taxonomy:
    category:
        - labs
---

## Operators

Operators are symbols that perform operations on variables and values. There are several types of operators in Python but for our purposes we will focus on the following:

* Arithmetic Operators
* Assignment Operators
* Comparison Operators

### Arithmetic Operators

Arithmetic Operators perform mathematical operations on values and variables.

```
a = 10
b = 5

print('Sum: ', a + b)
print('Subtraction: ', a - b)
print('Multiplication: ', a * b)
print('Division: ', a / b)
```

### Assignment Operators

Assignment operators are used to assign values to variables.

```
a = 10
b = 5

print(a, b)

a += b # a = a + b
print(a)

a -= b # a = a - b
print(a)
```

### Comparison Operators

Comparison operators compare values / variables and return a True or False (i.e. boolean) result.

```
a = 5
b = 2

print('a == b is', a == b)
print('a != b is', a != b)
print('a > b is', a > b)
print('a < b is', a < b)
print('a >= b is', a >= b)
print('a <= b is', a <= b)

```

## Conditional Statements

### if

Abstract Structure

```
if condition:
    # code to perform if condition is True
```

* if the condition returns `True` perform the code in the block
* if the condition returns `False` skip the code in the block

For example

```
data = 50

if data == 50:
    print("data is fifty")

```

vs

```
data = 50

if data > 50:
    print("a large number")

```

### if...else

A programmer can explicitly define code to run if the `condition` is not `True` rather than simply doing nothing.

```
if condition:
    # code runs if condition is True
else:
    # code runs if condition is False

```

For example

```
data = 50

if data > 0:
    print('Positive!')
else:
    print('Negative!')

```

### if...elif...else

Choose between two alternatives

```
if condition1:
    # code runs if condition 1 is True
elif condition2:
    # code runs if condition 2 is True
else:
    # code runs if condition 1 and 2 are False

```

For example

```
number = 0

if number > 0:
    print("Positive number")

elif number == 0:
    print('Zero')
else:
    print('Negative number')

```
