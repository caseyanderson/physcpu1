---
layout: post
title:  "Analog & Digital Signals"
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


## GPIO

![]({{site.url}}/assets/feather_gpio.jpg)

The HUZZAH32 has a variety of pins that perform different functions. For example, last week we looked at `3V` and `GND`, pins which give us access to the power and ground on the HUZZAH32 respectively. In other words these pins can only be used for those purposes.

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

## Electrical Signals

In electronics a signal is a time-varying quantity, where the quantity that is varying over time is voltage or current, which conveys information. Physical Computing involves interfacing two different types of electrical signals together: digital and analog.

## Digital Signals

Note: image sourced from [here](https://learn.sparkfun.com/tutorials/analog-vs-digital/all#digital-signals)

![]({{site.url}}/assets/digital_sig.png)

A digital signal is comprised of a sequence of discrete values. In computation we typically think of these values as binary, or sequences of `1` and `0`, however there are a variety of equivalent ways to refer to this same alternation:

|V+|GND|
|-------|--------|
| HIGH | LOW |
| 1 | 0 |
| True | False |
| On | Off |

For computers (or robots) the world in all its complexity can be represented, or encoded, by sequences of two possible values.

<iframe width="560" height="315" src="https://www.youtube.com/embed/aAwJlD-m_hE" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

To date we have exclusively worked with digital inputs and outputs: a button, is either connected (on) or disconnected (off); an LED is either illuminated (on) or dark (off).


## Analog Signals

Note: image sourced from [here](https://learn.sparkfun.com/tutorials/analog-vs-digital/all#analog-signals)

![]({{site.url}}/assets/analog_sig.png)



## Analog Input
