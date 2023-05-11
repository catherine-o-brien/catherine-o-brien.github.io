---
layout: post
title: "LED Disco Ball That Responds To Music With Arduino ESP32"
description: "To create an LED disco ball that responds to music, I put an LED strip into clear piping, shaped the piping into a sphere-like shape, and connected the LED strip to an ESP32 and a microphone. Using the data from the microphone, the LED strip lights up in different patterns."
date: 2023-05-11
feature_image: images/musical-led-disco-ball/disco-ball.png
tags: []
---

I have always wanted to create some sort of display that responds to music, and this final project for my Creative Embedded Systems class seemed like the perfect opportunity! I decided to create a disco ball-inspired LED display that responds to music. To do so, I put an LED strip into clear piping, shaped the piping into a sphere-like shape, and connected the LED strip to an ESP32 and a microphone. Using the data from the microphone, the LED strip lights up in different patterns.

<!--more-->

[View this project on my GitHub](https://github.com/catherine-o-brien/module4)

# MY PROJECT

# MATERIALS

* **Arduino ESP-32 TTGO T-display** [like this one](https://www.amazon.com/LILYGO-T-Display-Arduino-Development-CH9102F/dp/B099MPFJ9M)
* **USB-C cord** (make sure that your cord supports data transfer, not just power– [see more about that here](https://www.dignited.com/50330/usb-data-cable-vs-usb-charging-cable/). For this project, you will use this cable both to upload code to your device during development and to power the device once it is finished.)
* **Microphone** (I used the [Arduino Sound Sensor](https://microcontrollerslab.com/ky-038-microphone-sound-sensor-module-arduino-tutorial/))
* **Breadboard** (this isn't actually necessary, but very helpful for prototyping and troubleshooting your project!)
* **5V Battery pack**
* **LED Strip** (I used [this one](https://www.amazon.com/BTF-LIGHTING-Flexible-Individually-Addressable-Non-waterproof/dp/B01CDTEG1O/ref=sr_1_8?crid=3N19D1Q6X1QOS&keywords=programmable%2Bled%2Bstrips&qid=1681838388&sprefix=programmable%2Bled%2Bstri%2Caps%2C146&sr=8-8&th=1))
* **Clear flexible tubing** (encloses the LED strip)
* **Hearty wire and wire cutters** (needs to be strong enough to hold the flexible tubing in the spherical shape– I used wire about 4mm thick, similar to [this one](https://www.amazon.com/TecUnite-Aluminum-Bendable-Skeleton-Thickness/dp/B07CQL7Y5B/ref=sr_1_2_sspa?keywords=4mm%2Bwire&qid=1683783492&sr=8-2-spons&spLa=ZW5jcnlwdGVkUXVhbGlmaWVyPUFNTFhSVjlUQktLSUYmZW5jcnlwdGVkSWQ9QTAyNDY3ODVUVVlCSjRaQkpDRDAmZW5jcnlwdGVkQWRJZD1BMDU2NjI2MzIwMFFKNVpLS1JTRlImd2lkZ2V0TmFtZT1zcF9hdGYmYWN0aW9uPWNsaWNrUmVkaXJlY3QmZG9Ob3RMb2dDbGljaz10cnVl&th=1)) 
* **Xacto knife**
* **Arduino IDE** [download here](https://support.arduino.cc/hc/en-us/articles/360019833020-Download-and-install-Arduino-IDE)


# STEPS

## 1. Setting up the hardware

My first step for this project was connecting my various forms of hardware and ensuring that they worked. My LED strip had female wire connections for ground, power, and data, and it also had two loose, unstripped wires that could serve as connections for ground and power. I used a wire to connect the data connection to the ESP32, but I opted not to use the ESP32 to power the LED strip because of the strain that that amount of power would put on such a small device. Instead, I stripped the loose ground and power wires and soldered them to the ground and power wires of an external battery pack. I used heat shrink to protect the soldering. 

![Close-up of the LED strip seen from within plastic tube](images/musical-led-disco-ball/led.png "Close-up of the LED strip")

Once I had successfully connected the LED strip, I connected the microphone. The ESP32's power source was plenty to power this small microphone, so I connected the ground, power, and analog data outputs to the ESP32 directly. I used the analog output from the microphone even though I ultimately converted it to a digital format (either the LED strip is "on" or "off") because I wanted to be able to define where the line was between "on" and "off" myself, and I was able to do that by using the analog output. 

![Close-up of the Arduino Sound Sensor, a small red device with a circular black microphone](images/musical-led-disco-ball/microphone.png "Arduino Sound Sensor")

To power the ESP32, I used the USB-C cable plugged into my laptop. I opted not to use a battery pack here because although it restricts the mobility of the project, using the battery pack for both the ESP32 and the LEDs would run the battery pack out of power too quickly. 

![The ESP32 connected via wires to the microphone. The wires that connect the LED strip to the battery pack and to the ESP32 are visible, but the LED strip itself is not.](images/musical-led-disco-ball/hardware.png "My hardware setup")

## 2. Writing the code

My code reads output from the microphone describing the change in volume over 200 milliseconds, decides if that change in volume is significant enough to suggest that it was triggered by a beat in the music. If the code interprets the change in volume as a beat, it invites the disco ball to flash off, creating a visual representation of the beat. Simultaneously, it also rotates through many different colors, in order to make the flashing of the disco ball more visually interesting. 

Check out my code at a more in-depth level on my [GitHub!](https://github.com/catherine-o-brien/module4)

![A screenshot of the Arduino IDE, showing my code for calculating the maximum and minimum volumes and for flashing the LED strip.](images/musical-led-disco-ball/code-sample.png "Sample of my code showing how I calculate the maximum and minimum volumes and how I flash the LED strip accordingly.")

## 3. Creating the enclosure

Once I had completed the software and hardware, I created my enclosure out of clear flexible tubing and wire. I used an Xacto knife to cut holes in the tubing into which I could insert wire to create joints to hold the shape together. 

![Close-up of a metal wire twisted through and around two clear tubes with LED strips inside of them.](images/musical-led-disco-ball/enclosure-joints.png "Close-up of an enclosure joint.")

By using these joints, I created a spherical shape that mirrored the shape of a real disco ball. I also added a hook on top of the disco ball so that it can be hung from a ceiling. 

![The disco ball hung up, flashing red. It is attached to a wooden coat hook mounted to a wall.](images/musical-led-disco-ball/hung-up.png "The disco ball, hung up.")

The hardware here is hidden behind the small plastic dish, which both protects them from damage and from view! This was a part of my enclosure that I added at the end, mostly for aesthetic purposes. 

## 4. Final product

Finally, once my enclosure was finished, I took a video of my final product, which you can see below! The disco ball successfully lights up according to the beats in the music, and I couldn't be happier with my results!

<iframe width="560" height="315" src="https://www.youtube.com/embed/Va2wmVxZMc4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

Just for fun, here's another video from when I was testing out different music– in this one, I'm clapping, because the beats in this music weren't distinctive enough for my device to pick them up!

<iframe width="560" height="315" src="https://www.youtube.com/embed/0KHQs4_STWY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

# CREDITS

This project was completed for Module 4 of Mark Santolucito’s Creative Embedded Systems course at Barnard College. See more about the assignment and his work on his website [here](http://www.marksantolucito.com/COMS3930/spring2023/mod4)!