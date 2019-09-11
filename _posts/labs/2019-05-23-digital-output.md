---
layout: post
title:  "Digital Output"
date: 2019-05-23 06:00:00 -0630
week: 2
number: 2
tags: lab
published: false
---

## Materials

* laptop
* internet access
* [Adafruit HUZZAH32](https://www.adafruit.com/product/3591)
* [USB cable - USB A to Micro-B - 3 foot long](https://www.adafruit.com/product/592) (or similar)
* 1x Breadboard
* 1x Resistor (220, 270, or 330 Ohms)
* 1x LED


## blink.py (internal LED)

```python
'''
blink.py (internal led)
'''

import machine
import time

led = machine.Pin(13, machine.Pin.OUT)

while True:
    led.value(1)
    time.sleep(0.5)
    led.value(0)
    time.sleep(0.5)

```

1. Open a Terminal, run Jupyter Notebook: `jupyter notebook`
2. Click `New`, Select `Text File`
3. Click on `Untitled.txt` and change it to `blink.py`
4. Copy and paste the code above into `blink.py`, save the file


### Save blink.py to ESP32

1. Use `ampy` to send files to the ESP32: `ampy -p /dev/tty.SLAB_USBtoUART put blink.py`
2. Confirm that `blink.py` is now on ESP32: `ampy -p /dev/tty.SLAB_USBtoUART get blink.py` (the code should be identical)


### Run blink.py

1. Connect to the ESP32: `screen /dev/tty.SLAB_USBtoUART 115200`
2. Run `blink.py`: `import blink.py` (you should see the internal LED blink)
3. Ctrl-C to exit `blink.py`
4. Ctrl-D to reboot ESP32
5. Exit `screen`: Ctrl-A Ctrl-\


## blink.py (external LED)

### Hookup Pattern

![]({{site.url}}/assets/fritzing/blink_external_led.png)

1. Connect ESP32 GND to a blue bus on the side of your breadboard
2. From pin 27, connect the following in series: a Resistor to an LED to GND (blue bus)


## update blink.py (for external LED)

1. On your laptop open `blink.py` in Jupyter Notebook and change the pin number from `13` to `27`: `jupyter notebook blink.py`
2. Delete the previous version of `blink.py` from the ESP32: `ampy -p /dev/tty.SLAB_USBtoUART rm blink.py`
3. Write the new version of `blink.py` to the ESP32: `ampy -p /dev/tty.SLAB_USBtoUART put blink.py`
4. Connect to ESP32 via `screen`: `screen /dev/tty.SLAB_USBtoUART 115200`
5. Run `blink.py`: `import blink.py`
6. Ctrl-C to stop `blink.py`
7. Exit `screen`: Ctrl-A Ctrl-\


## blink_if.py (external LED + if statement)

Another way to blink an LED is to use [Boolean logic](https://en.wikipedia.org/wiki/Boolean_algebra). In the example below we check to see if the `led.value` is `0` (or off). If the LED is off we turn it back on (`led.value(1)`), otherwise, we turn the led off (`led.value(0)`). We repeatedly check `led.value()` by wrapping this `if` statement in a `while` loop, which will run forever.

```python
'''
blink w/ if statement
'''

import machine
import time

led = machine.Pin(27, machine.Pin.OUT)

while True:
  if led.value() == 0:
    led.value(1)
  else:
    led.value(0)
  time.sleep(0.5)
```

### Send blink_if.py to ESP32

1. Use `ampy` to send files to the ESP32: `ampy -p /dev/tty.SLAB_USBtoUART put blink_if.py`
2. Confirm that `blink_if.py` is now on ESP32: `ampy -p /dev/tty.SLAB_USBtoUART get blink_if.py` (the code should be identical)


### Run blink_if.py

1. Connect to the ESP32: `screen /dev/tty.SLAB_USBtoUART 115200`ß
2. Run `blink_if.py`: `import blink_if.py`
3. See the LED blink
4. Ctrl-C to exit `blink_if.py`
5. Ctrl-D to reboot ESP32
6. Exit `screen`: Ctrl-A Ctrl-\
