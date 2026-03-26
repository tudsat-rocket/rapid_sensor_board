# Rapid Sensor Board
this module is meant to be a general-purpose amplifier which is going to be used for all analogue sensors which will be in the rocket, those include the WIKA pressure sensors as well as the fancy-fins strain gauges.

## Description
The main function of the module is to amplify signals with low voltage levels that are too small to be useful for our ADCs. Therefore the board has two sides with solder pads, one to connect to the IO board and one to connect to a sensor. The layout is designed in a way, that the sensor side is compatible with the WIKA TPR-Flex PCBs.

## Features
* Selectable gain (1-1000) -> the selection of RG1 will determine the gain (G = 1 + 49,4kOhm/RG)
* selectable offset -> output offset can either be 0V or Vcc/2
* Breakaway mounting holes
## Connections
### To IO-Board:
Connects the amplifier module with the IO-Board with the following pins:
* u+  ->  positive supply voltage (3-36V)
* u-  ->  gnd as "neg" supply voltage (only use in single supply mode) | reference for the output signal.
* o+  ->  amplified signal, references gnd (u-)
* ref  ->  selected reference signal (0V or Vcc/2) can be used to get additional information (e.g. detect noise on supply line(?))

### To sensor:
Connects the amplifier module with the Sensor with the following pins:
* u+  -> positive supply voltage (filtered supply voltage)
* u-  -> neg. supply voltage (gnd)
* s+  -> positive signal
* s-  -> negative signal

## User guideline:
The Gain resistor (RG1) must be chosen in a way that the expected maximum amplified voltage is lower than 4.85V (5V - 0.15V) and the expected minimum amplified voltage is higher than 0.1V if a smaller (or negative) output voltage is expected the solder jumper for the reference voltage needs to be connected to 3 to set an output shift.
Only if the connected sensor is expected to output a signal which exclusively results in an output signal that is in the above given values, can the reference solder jumper be set to 1.

The above-given adjustments are necessary as the IO module is only able to read values between 0V and 5V. A higher Input voltage can be used if the connected sensor needs a supply voltage which exceeds 5V. The amplified signal then still needs to be smaller than the given 4.85V.
