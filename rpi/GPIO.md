# RASPBERRY PI

## GPIO Zero

###Overview
      

### Importing GPIO Zero
There are various inbuilt function in GPIOZero(library) like LED, Button, PWMLED etc..
we can use these functions in either of the following format:
 1.    first is to import explicitly so that function can be directly used in script.
       for example:
 *   from _gpiozero_ import _Button_  and Button can be used directly.  **or**
 2.    import whole GPIO Zero library.But here all references to items within GPIO Zero must be prefixed:
 *    led = _gpiozero.LED()_

### PIN NUMBERING OF RASPBERRY PI
![image](https://gpiozero.readthedocs.io/en/stable/_images/pin_layout.svg)

[WiringPi pin number/BCM GPIO](http://wiringpi.com/wp-content/uploads/2013/03/gpio1.png)

PIN numbering can be done in various ways. some of them are as follows:
1.    If you wish to use physical (BOARD) numbering you can specify the pin number  as “BOARD(number)”
2.    Wiring pi pin numbers : we can use WPI(wpinumber)
3.    you can specify pin as header:number (here header for raspberry pi B+ is J8 and  number is physical pin)

Note: the numbering of the GPIO pins is not in numerical order; GPIO pins 0 and 1 are present on the board (physical pins 27 and 28) but are reserved for advanced use (see below).Any pin marked “GPIO” in the diagram below can be used as a pin number. For example, if an LED was attached to “GPIO17” you would specify the pin number as 17 rather than 11

### voltage
1. 5V pin : pin(BOARD) 2 & 4
2. 3V3 pin : pin(BOARD) 1 & 17
3. GROUND pin : pin(BOARD) 6 ,9, 14, 20, 25, 30, 34, 39

### Outputs
A GPIO pin designated as an output pin can be set to high (3V3) or low (0V).

# Different function in _GPIO ZERO_ LIBRARY:


### LED
