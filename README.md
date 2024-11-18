# freenove-4wd-car
Experimenting implementing PID controller, Kalman Filter and Localization on a robotic hardware car kit.

# Hardware Kits:
  - [Freenove 4WD Car Kit](https://www.amazon.com/dp/B07YBQ73CH?ref=ppx_pop_mob_ap_share)
  - [Sunfounder Super Starter Learning Kit V3.0 for Raspberry Pi](https://www.amazon.com/dp/B06XZ833QW?ref=ppx_pop_mob_ap_share)
  - [DSD Tech HC-05 Bluetooth Serial Pass-through Module Wireless Serial Communicaton with Button for Arduino](https://www.amazon.com/dp/B01G9KSAF6?ref=ppx_pop_mob_ap_share)

![alt text](https://github.com/akaufman3/freenove-4wd-car/blob/main/IMG_4136.jpg?raw=true)

# Project Objectives:

1. Put together the Car kit.
    - Follow the tutorial provided with the hardware kit to put the Car together.
![alt text](https://github.com/akaufman3/freenove-4wd-car/blob/main/IMG_4137.jpg?raw=true)
![alt text](https://github.com/akaufman3/freenove-4wd-car/blob/main/IMG_4143.jpg?raw=true)

2. Load libraries and run pre-built programs to experiment with sensors and actuators.
     - Load required libraries, as described in the tutorial for the hardware kit.
     - Load some pre-built programs and run on the hardware.
     - Write my own rule-based programs or copy and modify existing ones.
     - Move the car forward, backward, turn.
     - Make the car track a line.
     - Identify/avoid an obstacle.
     - Send Serial communication back and forth between car and a device/computer.

Working through some of the pre-built progams I experimented with having the car be able to detect and object at a certain distance:
  - <a href="https://youtube.com/shorts/2b_CvHQLJTQ?si=Czg7olRUOdeLG7KM" target="_blank"><img src="https://github.com/akaufman3/freenove-4wd-car/blob/main/Screenshot%202024-11-18%20at%201.45.33%20PM.png?raw=true" 
alt="IMAGE ALT TEXT HERE" width="250" height="400" border="10" /></a>

I experimented with line tracking. There were some interesting lessons around the interferance of the color of flooring and the distinction between the black tape line and the floor. This can be seen in the below video:
  - <a href="https://youtube.com/shorts/kJCh03ERKyo?si=2h8C8oGevs1FqMWV" target="_blank"><img src="https://github.com/akaufman3/freenove-4wd-car/blob/main/Screenshot%202024-11-18%20at%202.00.07%20PM.png?raw=true" 
alt="IMAGE ALT TEXT HERE" width="250" height="400" border="10" /></a>

There were additionally some interesting lessons around the following:
  - Not enough power defined in the code to move the car forward
  - Favoring driving left
  - Frequency of loop() being very high since I didn't have a delay which caused the car to move and sense at very high frequency, and if the sensor readings are changing the car will move very fast between turning and going straight which was causing the jerky movement
  - Impact of low batteries on oscillation
  - Working towards the objective of keeping the car moving with the black tape as close to the center as possible
  - Thinness of black tape line on readability of sensors
  - Medium sized lines also helped improve the mapping (half width of electrical tape)
  - Object distance detection and reversing the car as necessary



