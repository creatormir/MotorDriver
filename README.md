# MotorDriver
library Motor Driver for ESP32, arduino and other. It has a smooth start and stop. Without interruptions.

# Library for control h-brige DC motor driver
Library for VNH3SP30, VNH2SP30, VNH3ASP30, VNH5019A-E and other driver. 
The library supports a smooth change in speed. Does not use interruption.
If you are using ESP32/8266 remember to negotiate levels with the driver. There are drivers that support 3.3 V, there are only 5 V.
This library can also work with a homemade driver.

## Getting Started

To install this library use the **Arduino library manager** or use the **Clone or download > Download ZIP** button on the repository home page and then install the library in your Arduino environment using **Sketch > Include Library > Add .ZIP Library...**

Note the EN pin state. HIGH or LOW.

## Example
```
#include <MotorDriver.h>

#define DEF_PIN_DRIVERH_INA 19 // IN A.
#define DEF_PIN_DRIVERH_INB 18 // IN B.
#define DEF_PIN_DRIVERH_ENAB 17 // ON/OFF
#define DEF_PIN_DRIVERH_PWM 21 // for PWM

MotorDriver motor1;

motor1.begin(DEF_PIN_DRIVERH_INA, DEF_PIN_DRIVERH_INB, DEF_PIN_DRIVERH_PWM, DEF_PIN_DRIVERH_ENAB); // initial

// set direction: DIRECTION_A or DIRECTION_B
motor1.setDirection(DIRECTION_A); // DIRECTION_A/DIRECTION_B

// motor1.setSpeed(speedTo, durationChange, speedFrom);
// speedTo = Final speed
// durationChange = Duration(milliseconds) of reaching the final speed. Default zero, that is instant change.
// speedFrom = initial speed. Default current speed.

motor1.setSpeed(150); // Sharp change of speed
motor1.setSpeed(255); // Sharp change of speed
motor1.setSpeed(SPEED_MAX); // Sharp change of speed

motor1.setSpeed(150, 3000, 0); // Smooth acceleration from zero in 3 seconds.
motor1.setSpeed(255, 500, 30); // Smooth acceleration from 30 in 2.3 seconds.

motor1.setSpeed(240);
motor1.setSpeed(50, 1500); // Smooth deceleration from current(240) speed


// stop(duration) // equivalent motor1.setSpeed( duration );
// duration Smooth deceleration. default 0
```
