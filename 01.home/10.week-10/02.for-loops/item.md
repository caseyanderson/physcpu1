---
title: '10.1 for Loops'
date: '14-11-2024 06:00'
taxonomy:
    category:
        - labs

---

## for loops

`for` loops allow one to iterate (repeat) over a collection or sequence. Abstractly all `for` loops share this structure:

```python
for item in collection:
  do something
```

But its often easier to understand them in action.

*For Example*
```python
x = "Mary had a little lamb"
x = x.split(' ')

for i in x:
    print(i, len(i))
```

Above we store a sample sentence at `x` and then split that sentence by space, producing a list of words that we then store at `x` (overwriting the original sentence in the process). Next we enter the `for` loop, which could be read as follows: `for` every word (`i`) in the list (`x`) print the word (`i`) and its length (or number of letters).

### for loops with range()

One can also use a `for` loop to count by iterating across a `range`.

A single value in `range` is interpreted as the `stop` value (the start value defaults to `0` in this case).

*For Example*
```python
for i in range(5):
  print(i)
```

`range(x,y)`, however, allows one to specify the `start` value and the `stop` value.

*For Example*
```python
for i in range(5, 10):
  print(i)
```

Optionally one can specify the `step` value by setting the third parameter.

*For Example*
```python
for i in range(0,15,3):
   print(i)
```

In the above example we increment, or add, by `3` until we reach the number `15` (starting from `0`).

Decrementing, or counting down, is accomplished by setting the `start` value high and `step` to a negative value.

*For Example*
```python
for i in range(1024,-1,-1):
   print(i)
```

Above we start at `1024` and count down, by `-1`, until we reach `-1`.
