---
layout: post
title:  "Analog vs Digital"
date: 2019-01-12 06:00:00 -0700
week: 3
number: 1
tags: lab
---

## Materials

* laptop
* internet access
* [Adafruit HUZZAH32](https://www.adafruit.com/product/3591)
* [USB cable - USB A to Micro-B - 3 foot long](https://www.adafruit.com/product/592) (or similar)
* 1x Breadboard
* 1x Potentiometer
* 1x LED (w/ Resistor [220, 270, 330])
* 1x LDR (w/ Resistor [10K])


## GPIO

![]({{site.url}}/assets/feather_gpio.jpg)

The HUZZAH32 has a variety of pins which perform a unique function. For example, last week we looked at `3V` and `GND`, pins which give us access to the power and ground on the HUZZAH32 respectively. In other words, these pins can only be used for those purposes.

The photo above highlights a number of pins that do not have a single function and are instead referred to as `General Purpose Input/Output` (or `GPIO`) pins. Note: it is normal to have to consult a datasheet in order to identify pin functionality.

Top row
* 13: GPIO 13, also connected to the on-board LED
* 12: GPIO 12
* 27: GPIO 27
* 33: GPIO 33
* 15: GPIO 15
* 32: GPIO 32
* 14: GPIO 14

Bottom row
* A0: analog output DAC2 or GPIO 26
* A1: analog output DAC1 or GPIO 25
* A2: GPIO 34+
* A3: GPIO 39+
* A4: GPIO 36+
* A5: GPIO 4
* 21: GPIO 21

Note: + denotes input only

## Analog vs Digital
