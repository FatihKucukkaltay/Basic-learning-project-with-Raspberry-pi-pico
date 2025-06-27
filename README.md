
# 🚦 Traffic Light System with Buzzer – Raspberry Pi Pico Project

This is a basic beginner-level Raspberry Pi Pico project using MicroPython.  
It simulates a traffic light system using red, yellow, and green LEDs, and plays a buzzer sound every time a light changes – just like in a racing start!

## 🎯 What You’ll Learn

- How to control LEDs with GPIO pins
- How to use a passive buzzer with PWM
- Basic timing and delays using `sleep()`
- Combining lights and sound to simulate real systems

## 🧰 Components Used

- Raspberry Pi Pico
- Red LED (x1)
- Yellow LED (x1)
- Green LED (x1)
- 220Ω resistors (x3)
- Passive buzzer (x1)
- Jumper wires
- Breadboard

Full code here :
 
from machine import Pin, PWM
from time import sleep

 LED Pins
red = Pin(15, Pin.OUT)
yellow = Pin(14, Pin.OUT)
green = Pin(13, Pin.OUT)

 Buzzer PWM singnal
buzzer = PWM(Pin(12))

def beep(duration=0.3, frequency=1000):
    buzzer.freq(frequency)
    buzzer.duty_u16(30000)  # Ses seviyesi
    sleep(duration)
    buzzer.duty_u16(0)

while True:
    # Red Light and voice
    red.on()
    yellow.off()
    green.off()
    beep()
    sleep(5)

    # Yellow Light and voice
    red.off()
    yellow.on()
    green.off()
    beep()
    sleep(2)

    # Green Light and voice
    red.off()
    yellow.off()
    green.on()
    beep()
    sleep(5)

