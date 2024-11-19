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
    - Practicing having the car move backwards and forwards
    - [code](https://github.com/akaufman3/freenove-4wd-car/blob/main/move-car-forward-backward)
    - <a href="https://youtube.com/shorts/d4gTm3qUuXs?si=OyTW5ZBuKPcH_Fp0" target="_blank"><img src="https://github.com/akaufman3/freenove-4wd-car/blob/main/Screenshot%202024-11-18%20at%202.41.01%20PM.png?raw=true" alt="IMAGE ALT TEXT HERE" width="250" height="400" border="10" /></a>
       
3. Challenge 1: Sense the environment in some way (light, temperature, sound, water level in your plant, etc.) and respond somehow
    - Working through some of the pre-built progams I experimented with having the car be able to detect and object at a certain distance:
    - <a href="https://youtube.com/shorts/2b_CvHQLJTQ?si=Czg7olRUOdeLG7KM" target="_blank"><img src="https://github.com/akaufman3/freenove-4wd-car/blob/main/Screenshot%202024-11-18%20at%201.45.33%20PM.png?raw=true" 
alt="IMAGE ALT TEXT HERE" width="250" height="400" border="10" /></a>

4. Challenge 2: Affect the environment in some way of your choice (move an object, make a robot drive or fly in a controlled way, turn an appliance on/off, etc…)
Note: The environment must be affected by a type of actuator that can be controlled by software.
   - Adapted boiler plate code to allow the car to detect objects at varying distances and adjust direction or rotate 180deg to attempt to move around the object
   - [code](https://github.com/akaufman3/freenove-4wd-car/blob/main/detect-and-rotate)
   - <a href="https://youtube.com/shorts/Qj_mQ-wwjQY?si=MxwAiCIdN4ToMBLe" target="_blank"><img src="https://github.com/akaufman3/freenove-4wd-car/blob/main/Screenshot%202024-11-18%20at%203.29.21%20PM.png?raw=true" alt="IMAGE ALT TEXT HERE" width="250" height="400" border="10" /></a>

5. Challenge 3 - AI – PID Controller
    - Implement a PID controller to keep the car at a certain target distance from an object, e.g., your hand. The car should speed up or slow down depending on the distance from the object.
    - I managed to get at least the forward movement working for PID implementation. It was pretty hard but a nice challenge. Getting the alpha error to correlate with a speed and tuning that so the car stopped nicely, accelerated smoothly is tricky. I would have liked to spend more time getting it to drive in reverse. I had to take the 5/4 stop/start out because my code wouldnt loop. At first I just tested for obstacle being too close to the car (car stopped) and far (car could drive forward).
      - [code](https://github.com/akaufman3/freenove-4wd-car/blob/main/pid-controller)
      - [code](https://github.com/akaufman3/freenove-4wd-car/blob/main/car-class)
      - <a href="https://youtube.com/shorts/pEK_mu42l4E?si=EtS3flFuS7bZu5Yq" target="_blank"><img src="https://github.com/akaufman3/freenove-4wd-car/blob/main/Screenshot%202024-11-18%20at%203.54.24%20PM.png?raw=true" alt="IMAGE ALT TEXT HERE" width="250" height="400" border="10" /></a>
    - Then I tried to do an out of range stop. So for this video you can see the car drives forward when the obstacle is within a certain threshold but stops if the obstacle is close or really far out of range.
      - ![alt text](https://github.com/akaufman3/freenove-4wd-car/blob/main/Screen%20Shot%202023-05-01%20at%203.50.29%20AM.png?raw=true)
      - <a href="https://www.youtube.com/shorts/q08wobXeXOo" target="_blank"><img src="https://github.com/akaufman3/freenove-4wd-car/blob/main/Screenshot%202024-11-18%20at%204.02.15%20PM.png?raw=true" alt="IMAGE ALT TEXT HERE" width="250" height="400" border="10" /></a>

6. I also experimented with line tracking. There were some interesting lessons around the interferance of the color of flooring and the distinction between the black tape line and the floor. This can be seen in the below video:
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
