# Shmoocon 2018 Badge Mod
Was your badge flashed at the 2018 Shmoocon party by [@macpod](https://twitter.com/macpoddotnet)/[@superfr0](https://twitter.com/search?q=superfr0)? As requested by a few folks, here is the code we flashed. Also provided is a pulled copy of the original firmware. 

## Entering bootloader mode:
In order to program/dump/etc the ESP8266 chip present in the badge, the chip must be placed into bootloader mode. This is accomplished by turning the badge off, grounding the pads of the unpopulated smt button pads (try using a piece of tin foil), then with the pins grounded turning the unit back on.

## Original firmware dump command
To dump the original device [esptool](https://github.com/espressif/esptool) was used:
esptool.py --baud 115200 --port /dev/ttyUSB0 read_flash 0 4194304 original_badge_flash.bin

## Setting up the Arduino IDE for new programs
1. Install the current upstream Arduino IDE at the 1.8 level or later. The current version is at the Arduino website.
2. Start Arduino and open Preferences window.
3. Enter http://arduino.esp8266.com/stable/package_esp8266com_index.json into Additional Board Manager URLs field. You can add multiple URLs, separating them with commas.
4. Open Boards Manager from Tools > Board menu and install esp8266 platform (and don't forget to select your ESP8266 board from Tools > Board menu after installation).

5. Open Manage Libraries from Sketch->Include Library
6. Search for and install the "Adafruit Neopixel" library 

## Board configuration:
* Board: "WeMos D1 R2 & mini"
* Flash Size "4M (1M SPIFFS)"
* Debug port: "Disabled"
* Debug Level: "None"
* iwIP Variant: "v2 Prebuilt (MSS=536)
* CPU Frequency "80Mhz"
* Upload Speed: "921600"

## Other comments
The WS2811 ics are daisy chained and are connected to pin 14. The sketch more or less is https://github.com/adafruit/Adafruit_NeoPixel/blob/master/examples/strandtest/strandtest.ino

Enjoy!
