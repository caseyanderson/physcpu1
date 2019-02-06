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

`Analog to Digital Conversion` (`ADC`) is the process of converting a varying voltage (`analog`) to a sequence of discrete voltages (`digital`). `MicroPython` provides a convenient interface for this via `ADC`, which can be used on any pin whose number is prepended with an `A` on the `ESP32`.

To create and store an instance of `ADC` on the pin labeled `A2`: `adc = ADC(Pin(34))`.

Take a moment to wire up a potentiometer, or other voltage divider sensor, to pin `34` on the `ESP32` and follow along:

*For Example*
1. Connect to the ESP32: `screen /dev/tty.SLAB_USBtoUART 115200`
2. import `ADC` and `Pin` from `machine`: `from machine import ADC, Pin`
3. create an instance of an `ADC` on pin `A2` (i.e. pin number `34`): `adc = ADC(Pin(34))`
4. set the attenuation (numerical range) for this `ADC` instance: `adc.atten(ADC.ATTN_11DB)`
5. read the voltage at pin `34`: `adc.read()`
6. repeat step 5.
7. repeat step 5. again
8. repeat step 5. one more time

* In step 4. we set the range of our `ADC` instance via `adc.atten()` (short for attenuate). Here `adc.atten(ADC.ATTN_11DB)` sets the input range to `0.0V` to `3.6V`
* In steps 6. - 8. above we ran the same line of code three times and got three different values because the `voltage` is `analog` (varying). Some analog sensors produce voltages that are more varied than others.


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
