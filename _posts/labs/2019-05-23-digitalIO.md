---
layout: post
title:  "Digital Input / Digital Output"
date: 2019-05-23 06:00:00 -0700
week: 2
number: 3
tags: lab
---

## Materials

* laptop
* internet access
* [Adafruit HUZZAH32](https://www.adafruit.com/product/3591)
* [USB cable - USB A to Micro-B - 3 foot long](https://www.adafruit.com/product/592) (or similar)
* 1x Breadboard
* 1x Resistor (220, 270, or 330 Ohms)
* 1x LED
* 1x SPST button


## Digital Input

### button.py

```python
'''
button.py
'''

import machine
import time

button = machine.Pin(12, machine.Pin.IN, machine.Pin.PULL_UP)

while True:
    if not button.value():
        print('Button pressed!')
    time.sleep_ms(20)

```

1. Open a Terminal, run Jupyter Notebook: `jupyter notebook`
2. Click `New`, Select `Text File`
3. Click on `Untitled.txt` and change it to `button.py`
4. Copy and paste the code above into `button.py`, save the file


### Hookup Pattern

![]({{site.url}}/assets/fritzing/button.png)

1. Connect 1 button pin to ESP32 Pin 12
2. Connect another button pin to ESP32 GND


### Send button.py to ESP32

1. Use `ampy` to send files to the ESP32: `ampy -p /dev/tty.SLAB_USBtoUART put button.py`
2. Confirm that `button.py` is now on ESP32: `ampy -p /dev/tty.SLAB_USBtoUART get button.py` (the code should be identical)


### Run button.py

1. Connect to the ESP32: `screen /dev/tty.SLAB_USBtoUART 115200`
2. Run `button.py`: `import button.py`
3. Press the button, see the print statement change
4. Ctrl-C to exit `button.py`
5. Ctrl-D to reboot ESP32
6. Exit `screen`: Ctrl-A Ctrl-\


## Digital Input / Digital Output

### button_led.py

```python
'''
button_led.py
'''

import machine
import time

button = machine.Pin(12, machine.Pin.IN, machine.Pin.PULL_UP)
led = machine.Pin(27, machine.Pin.OUT)

while True:
    if not button.value():
        led.value(1)
    else:
        led.value(0)
    time.sleep_ms(20)
```

1. Open a Terminal, run Jupyter Notebook: `jupyter notebook`
2. Click `New`, Select `Text File`
3. Click on `Untitled.txt` and change it to `button_led.py`
4. Copy and paste the code above into `blink_led.py`, save the file

### Hookup Pattern

![]({{site.url}}/assets/fritzing/button_led.png)

1. Connect 1 button pin to ESP32 Pin `12`
2. Connect ESP32 `GND` to a blue bus on the side of your breadboard
3. Connect another button pin to the same blue bus on the side of your breadboard
4. From pin `27`, connect the following in series: a Resistor to an LED to GND (blue bus)


### Send button_led.py to ESP32

1. Use `ampy` to send files to the ESP32: `ampy -p /dev/tty.SLAB_USBtoUART put button_led.py`
2. Confirm that `button_led.py` is now on ESP32: `ampy -p /dev/tty.SLAB_USBtoUART get button_led.py` (the code should be identical)


### Run button_led.py

1. Connect to the ESP32: `screen /dev/tty.SLAB_USBtoUART 115200`
2. Run `button_led.py`: `import button_led.py`
3. Press the button, see the LED light up
4. Ctrl-C to exit `blink_led.py`
5. Ctrl-D to reboot ESP32
6. Exit `screen`: Ctrl-A Ctrl-\
