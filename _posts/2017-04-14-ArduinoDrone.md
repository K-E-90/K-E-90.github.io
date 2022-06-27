---
title: Drone Motor Test
date: 2017-04-14 12:00:00 +0200
categories: [DIY]
tags: [Drone, Arduino, Raspberry Pi]
---

Working on a first version of my personal drone project. I had the powertrain completed and wanted to test this. I didn't have the desired autopilot hardware, but wanted to test the motors anyway. I did have an Arduino Uno and a Raspberry Pi 3B at that time. Both of these contain pulse-width modulation (PWM) pins, required for the electronic speed controller (ESC) that controls the motor.

On the Arduino I wrote a sample script to adjust the PWM signals to the ESCs. The video is the result of this program.

On the Raspberry Pi I did the same thing, however, the Pi didn't have the required amount of PWM pins. A workaround was to generate a software PWM signal (not with dedicated PWM generator hardware). This worked, but as the Raspberry Pi runs an Operating System, the signal stuttered from time to time. This made me switch to the Arduino until I got the desired autopilot.

<iframe width="640" height="360" src="https://www.youtube.com/embed/Ln1-pIh-zh4" frameborder="0" allowfullscreen></iframe>




