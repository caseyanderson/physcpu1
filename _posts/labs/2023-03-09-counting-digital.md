---
layout: post
title:  "Counting Digital Interactions (Presses)"
date: 2023-03-09 06:00:00 -0830
week: 8
number: 5
categories: labs

---

## Materials

* laptop
* internet access
* [Adafruit HUZZAH32](https://www.adafruit.com/product/3591)
* [USB cable - USB A to Micro-B - 3 foot long](https://www.adafruit.com/product/592) (or similar)
* 1x Breadboard
* 1x SPST button


## Hookup Pattern

![]({{site.url}}/assets/imgs/fritzing/button.png)


## button_press_once.py

Here we use a more complex `if` structure to identify a button press: we check to see `if` the button is currently pressed **and** `if` the current value of the button is different than the previous value (`prev_val`). Send the following example to your `ESP32`.

### Code

```python
'''
button_once.py
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

Take a moment to **run and use** `button_press_once.py` while asking the following question: can I reliably press the button and get only one Button pressed! message? Try it!


## button_count.py

Now that we can reliably count a button press without repeat triggers we can rewrite `button_once.py` to count each button press. Send the following to your `ESP32`.

### Code

```python
'''
button_count.py
'''

from machine import Pin
from time import sleep_ms

button = Pin(12, Pin.IN, Pin.PULL_UP)
prev_val = button.value()
count = 0

while True:
    if not button.value() and button.value() is not prev_val:
        count+=1
        msg = ' '.join(['Button pressed', str(count), 'times!'])
        print(msg)
    prev_val = button.value()
    sleep_ms(20)

```

Take a moment to **run and use** `button_count.py` while asking the following, more interesting, question: can I reliably count four button presses? Try it!

![]({{site.url}}/assets/imgs/button_counter_working.png)


## button_count_limit.py

```python
'''
button_count_limit.py
'''

from machine import Pin
from time import sleep_ms

button = Pin(12, Pin.IN, Pin.PULL_UP)
prev_val = button.value()
limit = 5
count = 0

while True:
    if not button.value() and button.value() != prev_val:
        count += 1
        msg = ' '.join(['Button pressed', str(count), 'times!'])
        print(msg)
        if count == limit:
            print('limit reached!')
            count = 0
    prev_val = button.value()
    sleep_ms(20)

```