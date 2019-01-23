# InnocommSPI
Demo application that sends messages with Arduino using the "Sigfox 3 Click" module with Innocomm SN10-13.  

This code was forked from here : https://github.com/aureleq/InnocommSPI

## Requirements
I checked the operation with Arduino UNO and Leonardo.  
This should work with Arduino UNO and Leonardo but you may need a level-shifter as the UNO board GPIOs output 5V and not 3V3.

If you would like to know about the SPI command, please refer to this link : https://www.nxp.com/docs/en/supporting-information/SIGFOX-SPI-COMMAND-INTERFACE-DESC.xlsx

Please note that the Innocomm SN10-13 used in this application is for RCZ3, so you need to modify the code depending on the module you are using.  

## Setup
Connect the shield to the Arduino pins as follows:

* Pins Arduino UNO:
  * ***** NOTE: Arduino GPIOs supply 5V => Innocomm GPIOs expects a 3V3 so level-shifter may be required *****
  * SCLK: pin 13
  * SDO/MISO: pin 12
  * SDI/MOSI: pin 11
  * CS: pin 8
  * ACK: pin 9

## Usage
3 functions have been defined in loop() to send payloads:
* sendPayload(payload, payloadSize) => send uplink payload only
* sendPayload(payload, payloadSize, downlinkFlag) => send payload and request ack
* sendBit() => send single bit