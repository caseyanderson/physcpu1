---
layout: post
title:  "Analog Input/Digital Output"
date: 2019-01-13 06:00:00 -0730
week: 4
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
* 1x Potentiometer (or Voltage Divider Sensor)
* 1x LED (w/ 1x Resistor [220, 270, 330])
### analogIn_PWMOut.py


```python
# analog in to pwm out

import machine
from time import sleep_ms

ledPin = machine.Pin(15)
potPin = machine.Pin(34)

pot = machine.ADC(potPin)
pot.atten(machine.ADC.ATTN_11DB)
pot.width(machine.ADC.WIDTH_10BIT)

pwm = machine.PWM(ledPin)
pwm.freq(100)

while True:
    sensor_val = pot.read()
    print(sensor_val)
    pwm.duty(sensor_val)

    sleep_ms(20)
```
