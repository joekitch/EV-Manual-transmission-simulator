# EV-Manual-transmission-simulator
Making a means to simulate a stick shift manual transmission in an ev conversion, with full use of clutch pedal and H pattern shifter

---

## Disclaimer

This is a very experimental system, and because it's actively messing with how the car controls, it could be dangerous.
I claim no responsibility for any damage to your car, or injuries to yourself if you cause a crash!

---

## Backround

EVs, famously, usually only have one gear, going from 0 to 14 or 18 thousand rpm, with no shifts along the way.

However it's possible to simulate this in order to inject some theater into the ev driving experience

The hyundai ionic 5n implements a system of this form, and is the inspiration for this project. However the 5n simplifies this by using shift paddles to simulate a dual-clutch gearbox

Youtube link;

[![The 5n's implementation](https://img.youtube.com/vi/sagIsYqMiJA/0.jpg)](https://www.youtube.com/watch?v=sagIsYqMiJA)


---

## Working principle

The general setup will involve a continuously running simulation of a manual transmission, with its outputs directly injecting canc commands to influence the throttle commands to the motor controller, as well as changing entire throttle maps as gears change

In terms of inputs, an h-pattern shifter and clutch pedal are necessary. 

---

## Simulating the transmission

Simulink already has a manual transmission simulation model available for usage

https://www.mathworks.com/help/sdl/ug/vehicle-with-manual-transmission.html 

some slight modifications to the model to add additional gears could make it very viable

---

## Shifter and clutch

The H-pattern can be taken from the sim racing world, which has many open hardware solutions, but i'll need to use a very robust design with high reliability

The stock clutch pedal can be used with a potentiometer, but it'll be necessary to design a spring system which can reasonably simulate the resistance of a clutch pedal

---

## Hardware

- an ev ECU which can accept injected can commands and flash new throttle maps as gears change
- Raspberry Pi to continuously run the manual transmission simulation
- canbus module for the pi
- potentiometer to read clutch pedal position
- H pattern shifter with switches in the gates and a reverse lockout, connected to the pi's GPIO

---

## Software

- a simulink model of a manual transmission
- a canbus translation layer running on the pi at all times, which can also input/output from the simulation
- 

---
