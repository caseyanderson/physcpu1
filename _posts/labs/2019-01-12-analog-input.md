---
layout: post
title:  "Analog Input"
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
* 1x Potentiometer
* 1x LED (w/ 1x Resistor [220, 270, 330])

## analog_read.py

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

1. Connect Pot1 to ESP32 `GND`
2. Connect Pot2 to ESP32 `34`
3. Connect Pot3 to ESP32 `3V`

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
