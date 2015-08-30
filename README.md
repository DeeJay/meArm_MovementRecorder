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

If using the Adafruit board:
```
Arduino    PWMServo  WiiChuck  Nokia
  GND         GND        -      Gnd
   5V    VCC & V+        +
 3.3V                        Vcc+BL*
   A4         SDA        d
   A5         SCL        c
   A2                            DC*
   A1                            CE*
   A0                           RST*
    2                           Clk*
    3                           Din*
                  *=Use resistor - 10k on the data pins, 100ohm on BL
```

The servos attach to the first block of four servo connections on the Adafruit board, brown wire at the bottom, yellow wire at the top.

```
Adafruit    Servo
     0      Base
     1  Shoulder (right)
     2     Elbow (left)
     3   Gripper
```
You can attach to a different block of four by changing the 'begin' callto specify a block 0-3, e.g. to use the second block call arm.begin(1); - to mirror movements to all 4 blocks, call arm.begin(-1);

If not using the Adafruit board:
```
Arduino    WiiChuck     Nokia    Base  Shoulder  Elbow  Gripper
  GND           -        Gnd    Brown     Brown  Brown    Brown
   5V           +                 Red       Red    Red      Red
 3.3V                 Vcc+BL*
   A4           d
   A5           c
   A2                     DC*
   A1                     CE*
   A0                    RST*
    2                    Clk*
    3                    Din*
    6                                                    Yellow
    9                                           Yellow
   10                                    Yellow
   11                          Yellow
         *=Use resistor - 10k on the data pins, 100ohm on BL
```
There are a couple of changes to make in code if not using the Adafruit board, these are commented.

The Nokia connections are expecting 3V3, so from a 5V Arduino we use resistors - 10k on the GPIO pins (DC, CE, RST, Clk, Din) and 100ohm on the backlight BL.

Basic movements
---------------

First stick moves gripper forwards, backwards, left and right  Second stick moves gripper up and down (and left and right again).  Shoulder buttons open and close the gripper.  The home button returns to starting point.

Recording and playback
----------------------

Use the cursor pad to navigate the on-screen menu, and A or B buttons to select a menu choice.  Record steps as points in space the arm will travel between.  Opening and closing the gripper also records a data step.  Select 'Replay all steps' to go through the programmed motions and return to the starting position.
