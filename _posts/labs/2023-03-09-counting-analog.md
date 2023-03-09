---
layout: post
title:  "Counting Analog Interactions (Waves)"
date: 2023-03-09 06:00:00 -0900
week: 8
number: 6
categories: labs

---

## Materials

* laptop
* internet access
* [Adafruit HUZZAH32](https://www.adafruit.com/product/3591)
* [USB cable - USB A to Micro-B - 3 foot long](https://www.adafruit.com/product/592) (or similar)
* 1x Breadboard
* 1x Light Dependent Resistor


## Hookup Pattern

![]({{site.url}}/assets/imgs/fritzing/ldr_voltage_divider.png)


## wave.py

intro text here

### Code

```python
'''
wave.py
'''

from machine import ADC, Pin
from time import sleep_ms
from math import fabs

ldrPin = Pin(34, Pin.IN)

ldr = ADC(ldrPin)
ldr.atten(ADC.ATTN_11DB)
ldr.width(ADC.WIDTH_10BIT) # 0 - 1023

prev_val = ldr.read()

threshold = 80 # update this!

while True:
    current_val = ldr.read()
    diff = fabs(current_val - prev_val)
    
#    data = " ".join(["curr:", str(current_val), "prev:", str(prev_val), "diff:", str(diff)])
#    print(data)
    if diff >= threshold:
        print("a wave!")
    elif diff <= 10:
        print("no wave!")
    prev_val = current_val
    sleep_ms(20)

```


## wave_count.py

more intro text

### Code

```python
'''
wave_count.py
'''

from machine import ADC, Pin
from time import sleep_ms
from math import fabs

ldrPin = Pin(34, Pin.IN)

ldr = ADC(ldrPin)
ldr.atten(ADC.ATTN_11DB)
ldr.width(ADC.WIDTH_10BIT) # 0 - 1023

prev_val = ldr.read()

threshold = 80 # update this!
count = 0

while True:
    current_val = ldr.read()
    diff = fabs(current_val - prev_val)
    if diff >= threshold:
        print("a wave!")
        count+=1
    wave_count = " ".join(["count:", str(count)])
    print(wave_count)
    prev_val = current_val
    sleep_ms(20)

```


## wave_count_sleep.py

```python
'''
wave_count_sleep.py
'''

from machine import ADC, Pin
from time import sleep_ms
from math import fabs

ldrPin = Pin(34, Pin.IN)

ldr = ADC(ldrPin)
ldr.atten(ADC.ATTN_11DB)
ldr.width(ADC.WIDTH_10BIT) # 0 - 1023

prev_val = ldr.read()

threshold = 80 # update this!
count = 0
prev_count = 0

while True:
    current_val = ldr.read()
    diff = fabs(current_val - prev_val)
    
#    data = " ".join(["curr:", str(current_val), "prev:", str(prev_val), "diff:", str(diff)])
#    print(data)
    if diff >= threshold:
        print("a wave!")
        count+=1
        if count != prev_count:
            sleep_ms(500)
#             sleep_ms(1000)
    wave_count = " ".join(["count:", str(count)])
    print(wave_count)
    prev_val = current_val
    prev_count = count
    sleep_ms(20)

```
