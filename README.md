# TCA9555

***

## Introduction

**TCA9555** is a Python module for interfacing the Texas Instruments [TCA9555](https://www.ti.com/lit/ds/symlink/tca9555.pdf) 16-bit I2C-based GPIO expander using a Raspberry Pi.

## Installation

You have to have Python >= 2.7 with the following packages installed:

- [wiringpi](https://github.com/WiringPi/WiringPi-Python)
- [bitstring](https://github.com/scott-griffiths/bitstring)

To install these dependecies, open a terminal and type
```bash

pip install wiringpi bitstring
```
Then, to finally install **TCA9555**, move to the root folder and type
```bash

python setup.py develop
```

which will install in development mode

## Usage

```python

# Import the class
from tca9555 import TCA9555

# Initialize with standard I2C-bus address of TCA9555 a.k.a 0x20
gpio = TCA9555()

# Print startup-config as human-readable
print(gpio.format_config())

# Set all pins 0, 1, 2 as output
gpio.set_output(bits=(0,1,2))

# Write value 5 to bits 0, 1, 2
gpio.int_to_bits(bits=(0,1,2), val=5)

# Read value from bits 0, 1, 2 
print(gpio.int_from_bits(bits=(0,1,2)))  # 5

# Check if bit 0 is high
gpio.is_high(0)

# Set bit 6 and 10
gpio.set_bits(bits=(6, 10))

# Unset bits 6
gpio.unset_bits(bits=6)
```
