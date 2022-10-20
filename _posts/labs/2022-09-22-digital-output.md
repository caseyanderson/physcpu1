---
layout: post
title:  "Digital Output"
date: 2022-09-22 06:00:00 -0630
week: 2
number: 2
categories: labs
---

## Materials

* laptop
* internet access
* [Adafruit HUZZAH32](https://www.adafruit.com/product/3591)
* [USB cable - USB A to Micro-B - 3 foot long](https://www.adafruit.com/product/592) (or similar)
* 1x Breadboard
* 1x Resistor (220, 270, or 330 Ohms)
* 1x LED


## basic LED circuit

### Hookup Pattern

![]({{site.url}}/assets/imgs/fritzing/esp32-basic-led-circuit.png)

1. Connect ESP32 `GND` to a blue bus on the side of your breadboard
2. Connect ESP32 `3V` to a red bus on the side of your breadboard
3. Use a 220R (or similar) to run the `3V` signal to the inside of your breadboard
4. Connect that wire to the longer of the two (this is +) LED pins, the shorter pin goes to and adjacent row
5. Connect the shorter LED pin to `GND`


## blink.py (internal LED)

```python
'''
blink.py (internal led)
'''

from machine import Pin
from time import sleep

led = Pin(13, Pin.OUT)

while True:
    led.value(1)
    sleep(0.5)
    led.value(0)
    sleep(0.5)

```


## blink.py (external LED)

### Hookup Pattern

![]({{site.url}}/assets/imgs/fritzing/esp32-external-led.png)

1. Connect ESP32 `GND` to a blue bus on the side of your breadboard
2. From pin 13, connect the following in series: an `LED` to `220R` to `GND`
