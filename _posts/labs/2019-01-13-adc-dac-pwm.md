---
layout: post
title:  "ADC, DAC, & PWM"
date: 2019-01-13 06:00:00 -0700
week: 4
number: 1
tags: lab
published: false
---

## Materials

* laptop
* internet access
* [Adafruit HUZZAH32](https://www.adafruit.com/product/3591)
* [USB cable - USB A to Micro-B - 3 foot long](https://www.adafruit.com/product/592) (or similar)
* 1x Breadboard
* 1x Potentiometer (or Voltage Divider Sensor)
* 1x LED (w/ 1x Resistor [220, 270, 330])


## Analog to Digital Conversion (ADC)

reference analog input from previous week, show line with adc


## Digital to Analog Conversion (DAC)

reference

## Pulse Width Modulation

### Hookup Pattern

![]({{site.url}}/assets/blink_rszd.jpg)

1. Connect ESP32 `GND` to a blue bus on the side of your breadboard
2. From pin `27`, connect the following in series: a `resistor` to an `LED` to `GND` (blue bus)


![]({{site.url}}/assets/PWM_wikipedia.png)

`Pulse Width Modulation` (or `PWM`) allows one to use a digital output to simulate an analog or varying voltage. This is accomplished by toggling a digital pin on and off very quickly, which

```python
import machine
pin = machine.Pin(27)
pwm12 = machine.PWM(pin)
```

There are two parameters associated with


### fade.py

```python

from time import sleep
from machine import Pin, PWM

pwm = PWM(Pin(15))
pwm.freq(60)

while True:
    for i in range(1024):
        pwm.duty(i)
        sleep(0.001)
    for i in range(1023, -1, -1):
        pwm.duty(i)
        sleep(0.001)
```
