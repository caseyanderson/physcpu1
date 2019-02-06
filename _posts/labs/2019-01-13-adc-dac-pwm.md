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

`Analog to Digital Conversion` (`ADC`) is the process of converting a varying `voltage` (`analog`) to a sequence of discrete `voltages` (`digital`). `MicroPython` provides a convenient interface for this via `ADC`, which can be used on any pin whose number is prepended with an `A` on the `ESP32`. In this class we will typically use `ADC` with `analog` sensor input so it's okay to associate this process with (`analog`) inputs generally (for now).

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
* In steps 6. - 8. we ran the same line of code three times and got three different values because the `voltage` is `analog` (varying). Some `analog` sensors produce `voltages` that are more varied than others.


## Digital to Analog Conversion (DAC) / Pulse Width Modulation (PWM)

![]({{site.url}}/assets/PWM_wikipedia.png)

Digital to Analog Conversion (DAC) is the opposite of `ADC`: a `DAC` converts a sequence of discrete `voltages` into a varying `voltage`. In order to approximate an analog voltage with a digital pin on the `ESP32` one typically uses `Pulse Width Modulation` (`PWM`). This is accomplished by toggling a digital pin on and off very quickly.

The image above is an example of `PWM` output. Note that it approximates an analog voltage but, if we look closely, we can still observe the discrete steps of the original digital signal.

### Hookup Pattern

![]({{site.url}}/assets/blink_rszd.jpg)

1. Connect ESP32 `GND` to a blue bus on the side of your breadboard
2. From pin `27`, connect the following in series: a `resistor` to an `LED` to `GND` (blue bus)

In the following sequence we instantiate a `PWM` instance and associate it with an `ESP32` pin. Log in to your `ESP32` via `screen` and follow along:

*For Example*
1. import `Pin` and `PWM` from `machine`: `from machine import Pin, PWM`
2. store `PWM` pin number to the variable `pin`: `pin = Pin(27)`
3. create a `PWM` object and store it at `pwm12`: `pwm12 = PWM(pin)`

There are two parameters associated with `PWM`: `frequency` and `duty cycle`:
* the `frequency` controls the speed at which the pin is toggled `ON` and `OFF`
* the `duty cycle` is how long the pin is `HIGH` compared with the length of a single period (`LOW` plus `HIGH` time). Maximum `duty cycle` is when the pin is `HIGH` (`On`) all of the time, and minimum is when it is `LOW` (`OFF`) all of the time.

Follow along to experiment with changing these settings:

*For Example*
1. 


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
