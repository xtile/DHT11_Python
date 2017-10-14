# DHT11 Python library

This simple class can be used for reading temperature and humidity values from DHT11 sensor on Orange PI Zero 

# Usage

1. Instantiate the `DHT11` class with the pin number as constructor parameter.
2. Call `read()` method, which will return `DHT11Result` object with actual values and error code.

For example:

```python
from pyA20.gpio import gpio
from pyA20.gpio import port


import dht11
import time
import datetime

# initialize GPIO
PIN2 = port.PA6
gpio.init()




# read data using pin PA6 (PWM)
instance = dht11.DHT11(pin=PIN2)

while True:
    result = instance.read()
    print("Last input: " + str(datetime.datetime.now()))

    if result.is_valid():
        print("Last valid input: " + str(datetime.datetime.now()))
        print("Temperature: %d C" % result.temperature)
        print("Humidity: %d %%" % result.humidity)

    time.sleep(1)
```

For working example, see `dht11_example.py` (you probably need to adjust pin for your configuration)


# License

This project is licensed under the terms of the MIT license.
