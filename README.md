# actinius-gnssr
This repository will host the code and instructions to to build a low cost GNSS reflectometer based on the actinius-icarus board (Nordic nrf9160 chip)
together with an Adafruit featherwing data logger

# Current Status: under construction ( nothing is working yet) 

## TODO Sofware:
1. ~~Setup communication with the sdcard from the data logger (uses SPI3 protocol)~~
2. Setup the setting of the clock on the datalogger (uses a serial connection on i2c of the feather board). possibly use GPS nmea messages to set the time (every once in a while?)
3. ~~Allow writing of lz4 compressed files to the sdcard (to store nmea messages, and telemetry)~~
4. Add functionality to upload nmea logs to an external server using the on board LTE chip
5. (Bonus add functionality to to a remote over-the air update of the firmware)
6. Read privacy sensitive settings from configuration file (such as upload passwords etc.)

## TODO:Hardware
1. Assemble battery, charger and solar panel, and case



# Building the firmware
Building this firmware requires [installing the Software development Kit from Nordic](https://developer.nordicsemi.com/nRF_Connect_SDK/doc/latest/nrf/getting_started.html). Which is an extended version of the Zephyr development kit
`west build -b actinius_icarus_ns -d build`

# Upload firmware using mcumgr
`mcumgr --conntype="serial" --connstring="dev=/dev/ttyUSB0,baud=115200" image upload app_update.bin`


# checking the uart serial output on linux
There is a [convenience script](debugtools/catserial.sh), which sets the correct serial baud rate etc and spits out the serial output from the Icarus.

The correct settings are:
- baud rate: 115200
- data bits:8
- stop bit: 1
- parity: None
- Flow control: None

