---
layout: post
title:  "Voltage Dividers"
date: 2019-01-12 06:00:00 -0710
week: 3
number: 2
tags: lab
---

## Materials

* laptop
* internet access
* [Adafruit HUZZAH32](https://www.adafruit.com/product/3591)
* [USB cable - USB A to Micro-B - 3 foot long](https://www.adafruit.com/product/592) (or similar)
* 1x Breadboard
* 1x LED
* 4x Resistors (2x 220 - 330, 2x 10K)

A voltage divider is any circuit that produces an output that is a fraction of its input. One can make a fixed value voltage divider with two resistors and an LED by wiring up the following:

![]({{site.url}}/assets/voltage_divider.png)

The above diagram represents the most basic way to use two resistors (labeled as `Z1` and `Z2`) to take some voltage (`Vin`) and output a fraction of it (`Vout`). The amount of `Vin` that is output at `Vout` depends on the values of the two resistors. This is the basic wiring pattern for almost any analog sensor, btw.

### Fixed Value Voltage Divider

#### hookup pattern

Wire up 3x:
1. with two equal value resistors
2. with 1 220 and 1 10K
3. with 1 10k and 1 10R (latter provided by CTA)

If you ever need to calculate the value of `R1` and `R2` (fyi: in this case, I am using `Z` and `R` interchangeably, but `Z` refers to impedance and `R` refers to resistance) such that you can get a specific `Vout`, here is the formula:

![]({{site.url}}/assets/voltage_divider_formula2.jpg)

Shortcuts for above

There are a collection of voltage divider-based sensors that can be used interchangeably, from a hardware and software standpoint, for wildly different interactions. In other words, all of the following analog sensors/voltage dividers are usable with analog_read.py:

* Potentiometer/knob: [1-turn](https://www.digikey.com/product-detail/en/3852C-282-103AL/3852C-282-103AL-ND/1088605) or [Continuous Turn](https://www.digikey.com/product-detail/en/6639S-1-103/6639S-1-103-ND/274005)
* [Light-dependent resistor](https://www.sparkfun.com/products/9088)
* [Force sensor](https://www.sparkfun.com/products/9375)
* [Flex Sensor](https://www.sparkfun.com/products/10264)
