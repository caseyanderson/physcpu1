---
layout: post
title:  "Prototyping with Button Input"
date: 2020-06-26 06:00:00 -0600
week: 10
number: 1
tags: lab
---

## Basic button.py

```python
'''
button.py
'''

from machine import Pin
from time import sleep_ms

button = Pin(12, Pin.IN, Pin.PULL_UP)

while True:
    if not button.value():
        print('Button pressed!')
    sleep_ms(20)

```

When one presses the button one invariably triggers more than one print statement. How hard is it to try to press the button only once? Take a moment to try now.

rewrite..

```python
'''
button_count.py
'''

from machine import Pin
from time import sleep_ms

button = Pin(12, Pin.IN, Pin.PULL_UP)

counter = 0

while True:
    if not button.value():
        counter+=1
        msg = ' '.join(['counter is', str(counter)])
        print(msg)
    sleep_ms(20)

```

```python
'''
button_press_once.py
'''

from machine import Pin
from time import sleep_ms

button = Pin(12, Pin.IN, Pin.PULL_UP)
prev_val = button.value()

while True:
    if not button.value() and button.value() is not prev_val:
        print('Button pressed once!')
    prev_val = button.value()
    sleep_ms(20)
```

```python
'''
button_press_count.py
'''

from machine import Pin
from time import sleep_ms

button = Pin(12, Pin.IN, Pin.PULL_UP)
prev_val = button.value()
counter = 0

while True:
    if not button.value() and button.value() is not prev_val:
        counter+=1
        msg = ' '.join(['Button pressed', str(counter), 'times!'])
        print(msg)
    prev_val = button.value()
    sleep_ms(20)
```

```python
'''
button_press_counter_limit.py
'''

from machine import Pin
from time import sleep_ms

button = Pin(12, Pin.IN, Pin.PULL_UP)
prev_val = button.value()
limit = 5
counter = 0

while True:
    if not button.value() and button.value() != prev_val:
        counter += 1
        msg = ' '.join(['Button pressed', str(counter), 'times!'])
        print(msg)
        if counter == limit:
            print('limit reached!')
#            counter = 0
            break
    prev_val = button.value()
    sleep_ms(20)
```

```python
'''
button_press_counter_cases_limit.py
'''

from machine import Pin
from time import sleep_ms

button = Pin(12, Pin.IN, Pin.PULL_UP)
prev_val = button.value()
limit = 5
counter = 0
action = 0

while True:
    if not button.value() and button.value() != prev_val:
        counter += 1
        if counter == limit:
            print('limit reached, resetting!')
            counter = 0
            action = 0
        else:
            action = counter
    if action == 1:
        print('interaction 1 is happening now!')
    elif action == 2:
        print('interaction 2 is happening now')
    elif action == 3:
        print('interaction 3 is happening now')
    elif action == 4:
        print('interaction 4 is happening now')
    prev_val = button.value()
    sleep_ms(20)
```
