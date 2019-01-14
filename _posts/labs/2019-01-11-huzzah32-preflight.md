---
layout: post
title:  "Adafruit HUZZAH32 Pre-flight"
date:   2019-01-10 06:00:00 -0700
week: 2
number: 1
tags: lab
---

## Materials
* laptop
* internet access
* [Adafruit HUZZAH32](https://www.adafruit.com/product/3591)
* [USB cable - USB A to Micro-B - 3 foot long](https://www.adafruit.com/product/592) (or similar)


## Install USB to Serial driver

1. Go [here](https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers)
2. Scroll down to **Download for Macintosh OSX**, click on **Download VCP (832 KB)** to download
3. Restart CPU


## Install Command line tools for ESP32

1. Open a Terminal
2. `pip3 install esptool`
3. `pip3 install adafruit-ampy`


## Install software for ESP32

1. Go [here](https://micropython.org/download/#esp32)
2. Download and install the "Standard firmware"
