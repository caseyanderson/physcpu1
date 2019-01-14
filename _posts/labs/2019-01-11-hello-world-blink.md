---
layout: post
title:  "Hello World (blink.py)"
date: 2019-01-11 06:00:00 -0710
week: 2
number: 2
tags: lab
---

## Materials

* laptop
* internet access
* [Adafruit HUZZAH32](https://www.adafruit.com/product/3591)
* [USB cable - USB A to Micro-B - 3 foot long](https://www.adafruit.com/product/592) (or similar)
* 1x Breadboard
* 1x Resistor (220, 270, or 330 Ohms)
* 1x LED


## blink.py (internal LED)

```python
import machine
import time

led = machine.Pin(13, machine.Pin.OUT)

while True:
  if led.value() == 0:
    led.value(1)
  else:
    led.value(0)
  time.sleep(0.5)
```

1. Click and select the code above, copy it to your clipboard
2. Open a Terminal
3. Create and open a python file: `sudo nano blink.py`
4. Paste the code into your Terminal
5. Ctrl-O to save, Ctrl-X to exit


### Write blink.py to ESP32

1. Use `ampy` to send files to the ESP32: `ampy -p /dev/tty.SLAB_USBtoUART put blink.py`
7. Confirm that `blink.py` is now on ESP32: `ampy -p /dev/tty.SLAB_USBtoUART get blink.py` (the code should be identical)


### run blink.py

1. Connect to the ESP32: `screen /dev/tty.SLAB_USBtoUART 115200`
2. Run `blink.py`: `import blink.py` (you should see the internal LED blink)
3. Ctrl-C to exit blink.py
4. Ctrl-D to reboot ESP32
5. Exit `screen`: Ctrl-A Ctrl-\


## blink.py (external LED)

1. Confirm that you have a functional LED by wiring it inline **with a resistor** between `3V3` and `GND`
2. After confirming that your LED works, move the wire that was previously attached at `3V3` to `GPIO` pin 27
3. On your laptop open `blink.py` in Jupyter Notebook and change the pin number from `13` to `27`: `jupyter notebook blink.py`
4. Delete the previous version of `blink.py` from the ESP32: `ampy -p /dev/tty.SLAB_USBtoUART rm blink.py`
5. Write the new version of `blink.py` to the ESP32: `ampy -p /dev/tty.SLAB_USBtoUART put blink.py`
6. Disconnect from ampy: Ctrl-A Ctrl-\
7. Connect to ESP32 via `screen`: `screen /dev/tty.SLAB_USBtoUART 115200`
8. Run `blink.py`: `import blink.py`
9. Ctrl-C to stop `blink.py`
10. Exit `screen`: Ctrl-A Ctrl-\
