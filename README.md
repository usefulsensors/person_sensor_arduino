# Using a Person Sensor on an Arduino

Example code that shows how to interface an Arduino to [Useful 
Sensor's](https://usefulsensors.com) 
[Person Sensor](https://usfl.ink/ps) board over I2C.

## Introduction

The Person Sensor is a small hardware module that's intended to make it easy to
find out when people are near a device, where they are, and who they are. It has
an image sensor and a microcontroller with pretrained ML models that use
computer vision to spot faces. 

There's a [detailed developer guide](https://usfl.ink/ps_dev)
available, but this project has sample code that shows you specifically how to 
get the sensor up and running with the Arduino IDE. It has been tested with the
Arduino Nano BLE Sense board, but uses standard APIs and should hopefully be
compatible with other platforms.

## Building

Open the `person_sensor_arduino.ino` file in the Arduino IDE, and press upload
to build and flash the example onto your board.

## Wiring Information

You'll need to consult your board's documentation to find out what the pins or
connectors used for the I2C interface are. Ideally you should find a board or
breakout that supports a standard connector like Qwiic or Grove, so you can
attach a cable from the sensor's Qwiic port.

## Running Face Detection

Once you have the sensor wired in, and the sketch flashed, you should start to
see information about the faces it spots, or error messages. If you hold the
sensor so that it's pointing at your own face you should see output like this in
the Serial Monitor:
```
********
1 faces found
Face #0: 99 confidence, (68, 71), 136x193, facing      
```
This shows that the sensor has found one face, with a 136 by 193 bounding box,
with the top-left corner at 68, 71, and the head is pointing directly towards
the sensor.

## Troubleshooting

The first thing to check is that the sensor is receiving power through the
`VDD` and `GND` wires. The simplest way to test this is to hold the sensor
upright (so the I2C connector is at the top) and point it at your face. You
should see a green LED light up. If you don't see any response from the LED then
it's likely the sensor isn't receiving power, so check those wires are set up
correctly.
