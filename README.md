# TAM-Series1-2013-Marlin
Marlin 1.0.0 customized for Type A Machines Series 1 - 2013 Plywood edition

Marlin 1.0.0 firmware configured for Type A Machines Series 1 - 2013 Plywood edition. Couldn't find an official Marlin 1.0 release for my older machine from Type A, so I grabbed the firmware for one of their newer machines and reconfigured (hopefully) all of the relevant parameters for my machine. Mostly just in Configuration.h.

I inferred the particulars of the steppers and belts on my machine through trial and error, so use at your own risk.

Useful resources for tuning params:

http://reprap.org/wiki/Triffid_Hunter%27s_Calibration_Guide

http://www.thingiverse.com/thing:13441

http://www.thingiverse.com/thing:5573 & http://www.thingiverse.com/thing:264782/

http://support.typeamachines.com/hc/en-us/articles/200364725-Gcode-Supported-By-Marlin-and-Series-1

---


In particular, my tuned settings for stepper steps/mm:
```c
// #define DEFAULT_AXIS_STEPS_PER_UNIT   {150.15, 150.15, 1012.658, 192.91} //Series 1.3 Direct Drive extruder 400 step motor and Mk7 gear. 1/16th on Y, and E. 1/8th on X and Z.
// #define DEFAULT_AXIS_STEPS_PER_UNIT   {150.15/2, 150.15, 3200/4, 202} //Series 1. Production Rev A (B??). 400 step NEMA17's and V1 drive gear.
//
// 2015-11-18
// steps scaled based on X & Y measurements of 140mm calibration print http://www.thingiverse.com/thing:13441
// M92 X75.1851 Y149.9198
#define DEFAULT_AXIS_STEPS_PER_UNIT   {75.1851, 149.9198, 1012.658, 192.91}
```

Good to know w/ Marlin v1:
```c
//=============================Additional Features===========================
//===========================================================================

// EEPROM
// the microcontroller can store settings in the EEPROM, e.g. max velocity...
// M500 - stores paramters in EEPROM
// M501 - reads parameters from EEPROM (if you need reset them after you changed them temporarily).
// M502 - reverts to the default "factory settings".  You still need to store them in EEPROM afterwards if you want to.
// So, to change the Z STEPS_PER_UNIT from 800 to 1012
//   M501 - to check params
//   M92 Z1012 - set new Z value to FLASH, note, not saved to eeprom yet
//   M500 - save
//   M501 - double check
//
//define this to enable eeprom support
#define EEPROM_SETTINGS
```
