meArm_MovementRecorder
======================

Record and playback movements on the Phenoptix meArm robotic arm, using MeArm.Brains controller with a Wii Classic gamepad and an LCD screen from an old Nokia phone.

Hardware requirements
---------------------

* MeArm.Brains controller http://blog.mearm.io/wp-content/uploads/2015/01/BrainsDiagram.pdf
* meArm open source robotic arm http://www.phenoptix.com/products/mearm-pocket-sized-robot-arm
* Wii Classic controller http://en.wikipedia.org/wiki/Classic_Controller
* Nokia 5110 LCD display https://www.sparkfun.com/products/10168

 
Software requirements
---------------------

* meArm_Adafruit library from https://github.com/RorschachUK/meArm_Adafruit
* (Or optionally meArm library from https://github.com/yorkhackspace/meArm instead)
* ClassicController library from https://github.com/wayneandlayne/Video-Game-Shield
* Adafruit Nokia library from https://github.com/adafruit/Adafruit-PCD8544-Nokia-5110-LCD-library
* Adafruit GFX library from https://github.com/adafruit/Adafruit-GFX-Library
* QueueList library from http://playground.arduino.cc/Code/QueueList
* (Optional) Adafruit PWM Servo library from https://github.com/adafruit/Adafruit-PWM-Servo-Driver-Library

Wiring
------




Using the MeArm.Brains board:

| ProMicro Pin | Function | Base | Left | Right | Claw | Wii | Nokia |
| :--- | :--- | --- | --- | --- | --- | --- | --- |
| 0 | Tx | | | | | | |
| 1 | Rx| | | | | | |
| 2 | SDA | | | | SDA | | |
| 3 | SCL | | | | SCL | | | 
| 4 | A6 | | | | | DC | |
| 5 | pwm | | | Servo | | | |
| 6 | A7 pwm | | | Servo | | | |
| Pin | | | | | | | |
| Pin | | | | | | | |
| Pin | | | | | | | |



Table from GH example -

| Left-Aligned  | Center Aligned  | Right Aligned |
| :------------ |:---------------:| -----:|
| col 3 is      | some wordy text | $1600 |
| col 2 is      | centered        |   $12 |
| zebra stripes | are neat        |    $1 |


Basic movements
---------------

First stick moves gripper forwards, backwards, left and right  Second stick moves gripper up and down (and left and right again).  Shoulder buttons open and close the gripper.  The home button returns to starting point.

Recording and playback
----------------------

Use the cursor pad to navigate the on-screen menu, and A or B buttons to select a menu choice.  Record steps as points in space the arm will travel between.  Opening and closing the gripper also records a data step.  Select 'Replay all steps' to go through the programmed motions and return to the starting position.
