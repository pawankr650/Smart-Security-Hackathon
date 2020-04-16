# RASPBERRY PI


## GPIO Zero

### Overview
**GPIO Zero** is a Python API used to programme the RPi . It is easy to use and very *friendly* for beginners to start with . It's code is simpler to read & as short as possible .   
The GPIO Zero library takes the class method approach to control, as opposed to the function method approach of **RPi.GPIO** and other, similar libraries . Pins become Python objects, which must be set up before use.


### Importing GPIO Zero
There are various inbuilt function in GPIOZero(library) like LED, Button, PWMLED etc..
we can use these functions in either of the following format:
 1.    first is to import explicitly so that function can be directly used in script.
       for example:

* `from gpiozero import Button ` and Button can be used directly.  **or**
 2.    import whole GPIO Zero library.But here all references to items within GPIO Zero must be prefixed:
 * `led = gpiozero.LED()`




### PIN NUMBERING OF RASPBERRY PI
![image](https://gpiozero.readthedocs.io/en/stable/_images/pin_layout.svg)

[WiringPi pin number/BCM GPIO](http://wiringpi.com/wp-content/uploads/2013/03/gpio1.png)

PIN numbering can be done in various ways. some of them are as follows:
1.    If you wish to use physical (BOARD) numbering you can specify the pin number  as “BOARD(number)”
2.    Wiring pi pin numbers : we can use WPI(wpinumber)
3.    you can specify pin as header:number (here header for raspberry pi B+ is J8 and  number is physical pin)

__Note:__ the numbering of the GPIO pins is not in numerical order; GPIO pins 0 and 1 are present on the board (physical pins 27 and 28) but are reserved for advanced use (see below).Any pin marked “GPIO” in the diagram below can be used as a pin number. For example, if an LED was attached to “GPIO17” you would specify the pin number as 17 rather than 11

### Voltage
1. 5V pin : pin(BOARD) 2 & 4
2. 3V3 pin : pin(BOARD) 1 & 17
3. GROUND pin : pin(BOARD) 6 ,9, 14, 20, 25, 30, 34, 39

### Outputs
A GPIO pin designated as an output pin can be set to high (3V3) or low (0V).

## Different function in __GPIO ZERO__ LIBRARY:  

## _INPUT DEVICES_ ##


### BUTTON  
It is a tiny library to make reading buttons very simple.
```
gpiozero.Button(pin) or Button(pin)
```
Here are some functions related to Button:  
**Let button = Button(pin)**
* `button.when_pressed`  
        It runs the function when the device changes state from inactive to active
* `button.when_released`  
        It runs the function when the device changes state from active to inactive
* `button.when_held`  
        It runs the function when device remains active.
* `button.value`  
        If button is currently pressed return **1**  
        otherwise **0**
* `button.is_pressed`  
        If button is currently pressed return **True**  
        otherwise **False**  
        (unlike value it's always a boolean)
* `button.hold_time`  
        The length of time(seconds) to wait after the device is activated
* `button.hold_repeat`  
        If True when_held will be executed repeatedly.
* `button.held_time`  
        The length of time device has been held for
* `wait_for_press(timeout=value)` (None is default value)  
        Pause the script until the device is activated, or the timeout is reached.
* `wait_for_release(timeout=value)` (None is default value)  
        Pause the script until the device is deactivated, or the timeout is reached.

Here is a code to understand better:

```python
'''this is a simple code for blinking of led with the help of  gpiozero library'''

from gpiozero import Button   #this imports the Button class from the gpio lirary. 

button = Button(2)      # 'button' is variable name can be anything and this becomes the object.

while True:
    if button.is_pressed:       # this calls the is_pressed() function 
         print("button is pressed")
    else:
         print("button is not pressed")
    
```   


## _OUTPUT DEVICES_ ##  

### LED
This library uses __BCM__ method of numbering as default. So there is no need to tell which to use. Also any output pin is called **`LED`** .This is because it is defined as LED class . <br />
```
gpiozero.LED(pin)  or  LED(pin)
``` 
Here are some function for LED:   
**let led = LED(pin)**   
* **`led.blink(on_time = 1, off_time = 1,n=None)`**  (values given are default)   
   * it's parameter are:  
     * on_time(float) : number of seconds on   
     * off_time(float) : number of seconds off  
* `led.off()` 
        turn the device off.
* **`led.on()`**  
        turn the device on.
* **`led.toogle()`**  
        Reverse the state of the device. If it’s on, turn it off; if it’s off, turn it on.
* **`led.islit`**  
        if active returns **True**  
        otherwise **False**
* **`led.pin`**  
         The pin through which device is connected.
* **`led.value`**  
         if active returns **1**  
         otherwise **0**

Here is a code to understand better:

```python
'''this is a simple code for blinking of led with the help of  gpiozero library'''

from gpiozero import LED   #this imports the LED class from the gpio lirary.
from time import sleep 

led = LED(18)       # 'led' is variable name can be anything and this becomes the object.

while True:
    led.on()       # this calls the on() function of LED class for object led.
    sleep(1)
    led.off()      # this calls the off() function.
    sleep(1) 
    
``` 
### PWMLED

As known PWM is technique for getting analog results from digital means . So this class can be used for variable output .  
```
gpiozero.PWMLED(pin)  or PWMLED(pin)
```
Here are some functions :  
**let led = PWMLED(pin)** 
* **`(on,off,pin,is_lit)`** works same as **LED** function.  
* ` led.blink(on_time=1, off_time=1, fade_in_time=0, fade_out_time=0, n=None)`  (values given are default)  
  * `It's parameter:`  
    * **on_time, off_time, n**  are same as in LED  
    * fade_in_time (float) – Number of seconds to spend fading in. Defaults to 0.  
    * fade_out_time (float) – Number of seconds to spend fading out. Defaults to 0.  
        
* **` led.value = val `**    
        Through this brightness of the led can be set .  It should be noted the value must lie between '0' & '1' .  

* **` led.pulse(fade_in_time=1, fade_out_time=1, n=None)`**   
        This is similar to blinking with brightness fading in and out .

Here is a code to understand better:

```python
'''this is a simple code for blinking of led with the help of  gpiozero library'''

from gpiozero import PWMLED   #this imports the PWMLED class from the gpio lirary.
from time import sleep 

led = PWMLED(18)       

while True:
    led.value = 0        # off
    sleep(1) 
    led.value = 0.5      # half brightness
    sleep(1)
    led.value = 1        # full brightness
    sleep(1)
    
``` 
### RGBLED
It represent full color LED component(composed of red,green and blue LED)  
```
gpiozero.RGBLED(red,green,blue)  or  RGBLED(red,green,blue)
```
* Parameters:  
  * red(int) : The GPIO pin that control the red component of RGB LED.  
  * green(int) : The GPIO pin that controls the green component of the RGB LED.
  * blue (int) – The GPIO pin that controls the blue component of the RGB LED.  

Here are some Functions related to RGBLED:  
LET led = RGBLED(pin)  
* **_on, off, toggle, is_lit, blink_** works same as PWMLED.
* `led.color`  
      Represent the color of LED as a tuple of(red,green,blue).


### BUZZER
In this Function you will learn how to use a buzzer (or piezo speaker) with Raspberry Pi. Buzzers can be found in alarm devices, computers, timers and confirmation of user input such as a mouse click or keystroke.

```
gpiozero.Buzzer(pin)  or  Buzzer(pin)
```
Some function related to Buzzer are:  
**Let bz = Buzzer(pin)**  
* **`(off, on, toggle, pin)`** works same as in LED or PWMLED.
* `bz.beep(on_time=1,off_time=1,n=None)`  (values given are default values)   
        on_time(float) : Number of seconds on.  
        off_time(float) : Number of seconds off.  
        n(int)  :  Number of times to blink.  










