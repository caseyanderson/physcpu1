---
title: '2.2 Functions'
date: '23-05-2025 06:05'
taxonomy:
    category:
        - labs
---

## Functions

A function is a reusable block of code referenced by name. Some functions allow programmers to pass changing data, via a parameter, into the function to produce particular results. Generally it is assumed that, no matter the specific behavior, a function will accept some data as input, transform it, and output / `return` it for use elsewhere.

In Python we define, with the prefix `def`, a function, allowing us to both dictate the specific behavior of the function (via code) and give it a name.

```
def nameOfFunction():
    # code that is executed when the function is run

```

## Hello [Name]

Let's take the classic Hello World example to begin with. In order to `print` the `string` "hello world" we make use of the `print()` object (FYI `print`, as well as `type` and `len`, are all built-in python functions).

```
print("hello world")
```

If we wanted to, we could wrap the `print` statement above in a function definition

```
def hello():
    print("hello world")

```

Allowing us to `print` the message by simply typing `print()` (try it!)

At the moment this is not a particularly helpful function other than minimizing the amount of typing a programmer needs to do.

To enhance the function, let's refactor (redesign) it to greet a person by name (i.e. we want it to `print` Hello [NAME], where [NAME] is passed via parameter).

We create a parameter to allow us to pass a name to the function `hello()` below

```
def hello(name):
    print("Hello", name)

````

We can test it with the following: `hello("casey")`, which returns the string "hello casey".

We can refactor this function once more to use the `String` method `join`. Try the following

```
def hello(name):
    msg = " ".join(["Hello", str(name)])
    print(msg)

```

And try running again: `hello("casey")`, `hello(7)`

Finally, lets say we have a list of `students` and wanted to use this function to say Hello to each of them. Let's also say we wanted our `hello` function to change teh data passed into it and output that changed data. Try the following

```
# function definition (or setup)
def hello(name):
    msg = " ".join(["Hello", str(name)])
    return(msg)

# make the list of students
students = ["Casey", "Danielle", "Trea'jure"]

# greet each student by name
for i in people:
    greeting = hello(i)
    print(greeting)


```

## nSidedDice

Suppose we want a function that can simulate a dice roll when run. For example

```
from random import randint

def diceRoll(sides):
    side = randint(1, sides)
    return(side)

diceRoll(6)
```

Here we use a random number generator to output integers between 1 and `sides`. Here we have a metaphorical dice throw.

Perhaps another approach can be found by refactoring with `choice` from `random`. For example

```
from random import choice

def nSidedDice(numSides):
    sides = []
    for i in range(1, numSides + 1):
        sides.append(i)
    result = choice(sides)
    return(result)

```

Randomly choosing from a list of possible sides seems like less of a distant metaphor for a dice roll than using a random number generator only capable of outputting inegers.

Finally, consider the following, in which we add a feature to easily identify whether the dice rolls an even or odd number.

```

# roll a random sided die, print whether it is even or odd

def nSidedDiceEvenOdd(numsides):
    limit = numsides + 1
    sides = []
    for i in range(1, limit):
        sides.append(i)
    result = choice(sides)
    if result % 2 == 0:
        msg = " ".join([str(result), "is even"])
    else:
        msg = " ".join([str(result), "is odd"])
    return(msg)

```

