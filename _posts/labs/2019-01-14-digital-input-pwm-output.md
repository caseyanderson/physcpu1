---
layout: post
title:  "Digital Input / PWM Output(s)"
date: 2019-01-14 06:00:00 -0700
week: 5
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
* 1x TIP120 (or N-channel MOSFET)
* 1x diode (1N4001)
* 1x 10K resistor
* 1x external power supply
* 1x SPST button


## Transistors

*Note: props to [this](http://bildr.org/2011/03/high-power-control-with-arduino-and-tip120/) fantastic article*

Transistors are three pin components capable of amplifying or switching signals. In Physical Computing we typically use them to control high voltage devices (like motors, lights, or solenoids) by quickly toggling a pin between `HIGH` and `LOW` (i.e. `PWM`).

While there are a variety of different types of transistors, we will focus on the `TIP120`, a pinout for which can be found below:

![]({{site.url}}/assets/tip120_pinout.jpg)

1. Base -> Control
2. Collector -> Input
3. Emitter -> Output

More specifically, transistors are based on the following phenomena: a small current flowing between the base (`B`) and emitter (`E`) causes a larger current to flow between the collector (`C`) and emitter (`E`).

![]({{site.url}}/assets/adafruit_transistor.png)


## TIP120 + PWM

### Schematic

![]({{site.url}}/assets/tip120_motor_light_sol_schematic.jpg)

### Hookup Pattern

![]({{site.url}}/assets/fritzing/mosfet_pwm_motor.png)

1. blah blah

cutoff vs saturation

## button_motor.py

### Hookup Pattern

![]({{site.url}}/assets/fritzing/button_motor.png)

1. add a button to blah
