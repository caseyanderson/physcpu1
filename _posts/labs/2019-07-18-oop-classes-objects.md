---
layout: post
title:  "Object-Oriented Programming: Classes & Objects"
date: 2019-07-18 06:00:00 -0600
week: 10
number: 1
tags: lab
published: false
---

Object-Oriented Programming, often abbreviated as OOP, is a [programming paradigm](https://en.wikipedia.org/wiki/Programming_paradigm) that emphasizes reusable patterns of code. OOP patterns are comprised of `classes` and `objects`:

* A `Class` defines a set of properties that will characterize any `object` instantiated from it (i.e. a recipe)
* An `Object` is an instance of a `class` (i.e. the food one produces by following the recipe)

A `class` describing a person, for example, might contain the following information: name, age, height, hair color, eye color, weight, etc.. In other words, any resulting person object will have these features.

A `class` can also describe behaviors or actions. All person `objects`, for example, may include the following behaviors: talking, standing, walking, running, sitting, breathing, etc..


## Classes

All `classes` are defined by name (where the first letter is capitalized) and preceeded by the keyword `class`. Follow along:

*For Example*
```python
class Person:
    pass
```

* Note: in the above `pass` is a placeholder used only while prototyping.

One can now create an instance of `Person()` with the following:

1. `test = Person()`
2. `type(test)`

Step 2. should produce this in the output: `__main__.Person`, which confirms that `test` is of type `Person()`


## The Initialization Method

`Methods` are a special kind of `function` defined within a `class`. While most `class methods` are designed by the programmer all `classes` share one method in common: the `initialization method` (or `__init__() method`). The `__init__() method` is used to `initialize` data and is conventionally the first method in a `class`. The first argument of the `__init__()` method **has** to be `self`, which allows an instance of `class` to refer to itself.

Run the following and then follow the numbered steps below to see the `__init__() method` in action:

*For Example*
```python
class Person:

    def __init__(self):
        print("here is a person")
```

1. `test = Person()`

Step 1 prints the message "here is a person" as soon as the `__init__() method` is run. Note that we only have to create an `instance` of the `class` to run the `__init__() method`, as it is automatically `initialized` (i.e. run) upon `instantiation` of an `object`.


## Instance Variables

Every person has a name, right? If we are creating an instance of the class `Person()` it would be logical to also denote the name of that person when an `object` (or person) is `initialized`. We can update our `class` to reflect this more detailed model of a `Person()` like so:

*For Example*
```python
class Person:

    def __init__(self, name):
        self.name = name
        print("A person named " + str(name))
```

1. `person1 = Person("Marcus")`

The `__init__() method` now does two things: it `initializes` an `instance` of `Person()` and prints the name of that person. Note that we now **have** to provide an `instance` of `Person()` with a name otherwise we get an error. The variable `name` is an `instance variable` (sometimes called an `instance attribute`), or a variable whose information one can expect to be different for every instance (or person) initialized by the `Person()` class.

We could create multiple people like so:

*For Example*
1. `person1 = Person("Marie")`
2. `person2 = Person("Steve")`

Let's update our `Person()` class to include the age of each person as an additional `instance variable`:

*For Example*
```python
class Person:

    def __init__(self, name, age):
        self.name = name
        self.age = age
        print("A person named " + str(self.name) + " who is " + str(self.age) + " years old.")
```

1. `person1 = Person("Marie", 20)`
2. `person2 = Person("Steve", 22)`

Once intialized, we can ask Python to tell us the age of either of our people with the following: `person1.age` or `person2.age`


## Instance Methods

A `class` can perform actions with `instance methods`. Previously we printed the name and age of our people with the `__init__() method`, but it might make more sense to write a method called `description()` to print this information only when necessary. Follow along:

*For Example*
```python
class Person:

    def __init__(self, name, age):
        self.name = name
        self.age = age

    def description(self):
        print("{} is {} years old".format(self.name, self.age))
```

1. `person1 = Person("Marie", 20)`
2. `person1.description()`


Let's update the `Person()` class to include an additional `instance method`. If we wanted to represent aging in the `Person()` class, in a very simplistic manner, we could add a `method` that increments the `age` attribute in an `instance` of `Person()`. Let's call this `method` `birthday()` and add it to `Person()`. Follow along:

*For Example*
```python
class Person:

    def __init__(self, name, age):
        self.name = name
        self.age = age

    def description(self):
        print("{} is {} years old".format(self.name, self.age))

    def birthday(self):
        self.age+=1
        print("Today is {}'s birthday! Happy Birthday, {}!".format(self.name, self.name))
```

1. `person1 = Person("Marie", 30)`
2. `person1.description()`
3. `person1.birthday()`
4. `person1.description()`


## main()

Let's say that we want to run a few lines of code that use the `Person()` class all at once, as an executable file, rather than line-by-line (or interactively, as we have been). Doing so requires the use of Python's `main()`, a function that executes automatically when an operating system begins running a (Python) program. Follow along:

*For Example*
```python
class Person:

    def __init__(self, name, age):
        self.name = name
        self.age = age

    def description(self):
        print("{} is {} years old".format(self.name, self.age))

    def birthday(self):
        self.age+=1
        print("Today is {}'s birthday! Happy Birthday, {}".format(self.name, self.name) + "!")

def main():
    person1 = Person("Marie", 30)
    person2 = Person("Steve", 45)

    person1.description()
    person2.description()

    person2.birthday()
    person2.description()

if __name__== "__main__":
    main()
```

1. save the code above in a python file with filename `person.py`
2. (in a terminal) navigate to where you saved `person.py` and make it executable: `sudo chmod +x person.py`
2. (in a terminal) run the file: `python3 person.py`

Note that the code we previously ran manually has been moved into the `function definition` for `main()`. We end our file with a conditional statement (`if __name__== "__main__":`) that runs our customized `main()`.
