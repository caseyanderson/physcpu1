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
* 1x LED (w/ 1x Resistor [220, 270, 330])


## GPIO

![]({{site.url}}/assets/feather_gpio.jpg)

The HUZZAH32 has a variety of pins, each of which perform different functions. For example, last week we looked at `3V` and `GND`, pins which give us access to the power and ground on the HUZZAH32 respectively.

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

In electronics a signal is a time-varying quantity which conveys information. The quantity that is varying over time is typically voltage or current. Physical Computing involves interfacing two types of electrical signals: digital and analog.


## Digital Signals

(Note: image sourced from [here](https://learn.sparkfun.com/tutorials/analog-vs-digital/all#digital-signals))

![]({{site.url}}/assets/digital_sig.png)

A digital signal is comprised of a sequence of discrete values. We typically think of these values as binary, or sequences of `1` and `0`, and associate them with computers. There are, however, a variety of equivalent ways to refer to this same alternation:

|V+|GND|
|-------|--------|
| HIGH | LOW |
| 1 | 0 |
| True | False |
| On | Off |

<iframe width="560" height="315" src="https://www.youtube.com/embed/aAwJlD-m_hE" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

To date we have exclusively worked with digital inputs and outputs: a button (input) is either connected (on) or disconnected (off); an LED (output) is either illuminated (on) or dark (off).


## Analog Signals

(Note: image sourced from [here](https://learn.sparkfun.com/tutorials/analog-vs-digital/all#analog-signals))

![]({{site.url}}/assets/analog_sig.png)

An analog signal is comprised of a signal whose value me be any point within a given range. The photo above, representing the composite video signal from an RCA plug, is one example of an analog signal. Generally people refer to phenomena in the "real world" as analog: light level, temperature, weight, etc.

Note: ESP32 pins which begin with an `A` are analog capable pins.


## Analog Input

### analog_read.py

```python
# analog read

import machine
from time import sleep_ms

adc = machine.ADC(machine.Pin(34))
adc.atten(machine.ADC.ATTN_11DB)

while True:
  print(adc.read())
  sleep_ms(20)

```

1. Open a Terminal, run Jupyter Notebook: `jupyter notebook`
2. Click `New`, Select `Text File`
3. Click on `Untitled.txt` and change it to `analog_read.py`
4. Copy and paste the code above into `analog_read.py`, save the file

### Hookup Pattern

![]({{site.url}}/assets/pot_analog_read.jpg)

1. Connect Pot1 to ESP32 GND
2. Connect Pot2 to ESP32 34
3. Connect Pot3 to ESP32 3V

### Send analog_read.py to ESP32

1. Use `ampy` to send files to the ESP32: `ampy -p /dev/tty.SLAB_USBtoUART put analog_read.py`
2. Confirm that `analog_read.py` is now on ESP32: `ampy -p /dev/tty.SLAB_USBtoUART get analog_read.py` (the code should be identical)


### Run analog_read.py

1. Connect to the ESP32: `screen /dev/tty.SLAB_USBtoUART 115200`
2. Run `analog_read.py`: `import analog_read.py`
3. Turn the pot, see the print statement change
4. Ctrl-C to exit `analog_read.py`
5. Ctrl-D to reboot ESP32
6. Exit `screen`: Ctrl-A Ctrl-\
