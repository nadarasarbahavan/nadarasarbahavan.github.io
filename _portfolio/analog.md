---
title: "Fully Analog Wall-follower (Undergrad Coursework-Electronics)"
excerpt: "An analog wall-following robot that navigates a 400mm corridor and curved bends without any micro-controller, using sensor fusion and a fully analog PID control system driving a PWM motor controller."
collection: portfolio
date: 2019-06-01
---

![Project screenshot](/images/solder.png)

The task was to create an analog wall follower: a robot capable of moving along a corridor without colliding with the wall on either side, with navigation done by detecting the walls and without using micro-controllers. The robot guides itself along the walls of a 400mm wide corridor and is able to navigate curved bends, with zero user interference. It detects walls on both sides and uses a Proportional-Integral-Differential (PID) control system to handle itself.

The robot obtains data about its orientation with respect to the adjacent walls from its four sensors and feeds it to a sensor fusion unit, which converts it to a single signal. This signal is processed by the PID and fed into the PWM unit along with a triangle wave generator output. The PWM unit then adjusts the speed of the two active motors via the motor controller so that the robot avoids colliding with the wall and follows it.
**Project report:** ![Download PDF](/files/Group22_Soldering iron.pdf)
