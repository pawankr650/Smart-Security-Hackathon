# GPIO LIBRARIES and how to choose between them 

This is a friendly documentation that discusses many GPIO libraries .  The RPi has **GPIO** ( **G**eneral **P**urpose **I**nput **O**utput ) pins just like arduino and can be used in *I/O* and many more things . These pins can be programmed like them however unlike arduino in which all the libraries are under one hood in Rpi there are lot of different libraries available in lot of different languages . This is due to the fact that Arduino is just a microcontroller while RPi is a computer . Like one can write a given programme and implement it in all the different computer languages . Similarly , the RPi GPIO pins can be programmed in all of them . But writing all the code from the scratch can be time-consuming and tough job .  

So there are many libraries whose functions and classes we can use to do our job . Now as told there are many such libraries . Here are some popular ones :  

   * [RPi.GPIO](https://sourceforge.net/p/raspberry-gpio-python/wiki/Home/)  
   * [pigpio](https://github.com/pawankumarssnl/rpi/blob/master/rpi/PiGPIO.md)  
   * [GPIOZero](https://github.com/pawankumarssnl/rpi/blob/master/rpi/GPIOZero.md)    
   * [WiringPi](http://wiringpi.com/)    
   * [RPIO](https://pythonhosted.org/RPIO/)   

Both RPi.GPIO and GPIOZero are written in python . If you are a beginner either of them can be good option to start . Both are equally capable .But if you have no idea about RPi have never worked with arduino or microcontrollers then GPIOZero would be better option . GPIOZero is basically a simplified library and therefore very friendly to use .  It is particularly designed in a way so that anyone can use it . Also it is new .
    
If you have some idea then you can use RPi.GPIO as you will feel what's really happening in the circuit . Some details which you may miss in GPIOZero can be understood here .

Now pigpio  is a very versatile library and has many more advanced features which others lack . Also it is implemented in C , Python , Shell and Gambas . Since it has more features hence it is a bit complex . If you are fairly versed and know about RPi and want to do some accurate measures this can be a great option .

### Authors
   * [Pranav](https://github.com/pranavkumar14)  
   * [Pawan](https://github.com/pawankumarssnl)  
