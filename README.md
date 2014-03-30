megamidi
========

Megamidi is a midi controller firmware for the arduino mega2560 based on http://www.instructables.com/id/Arcade-Button-MIDI-Controller by fraganator using the dualmocoLufa firmware http://morecatlab.akiba.coocan.jp/lab/index.php/aruino/midi-firmware-for-arduino-uno-moco/?lang=en

I have added substantial features to the original code: 
- The ability to use rotary encoders, each encoder uses 2 pins
- Cleaned up the Potentiometer code to give the full range of 7bits without losing resolution
- added addressable RGB LED code (WS2812B, will need external power)
- added code to allow the user to change led colour via midi commands
- added code to save and restore led colour information to and from onboard eeprom


It's currently setup to to use 32 buttons and 4 potentiometers, sending out note on/off messages for the buttons and CCs for the pots/encoders, the mega2560 has 54 individual digital IO pins and needs 1 for the LEDs so that's 53 buttons or 26 encoders or any mixture of the 2 + 16 pots or faders.  I haven't worked out how many leds you can address with the mega2560 eeprom but the code can in theory cope with somewhere around 50 leds but that can be improved upon as the orignal code was written on a leonardo which has smaller onboard eeprom space.

Any unused analog inputs need to be tied to gnd, as a quick fix, all unused analog inputs are set to outputs and pulled to ground, look for NUM_UNUSED and UNUSED_ANALOG_PINS defines, and adjust accordingly.

The code is rough and ready but quite usable, I will clean up as I go along.

You will need: 
- 1x arduino mega2560 r3
- the latest arduino Midi Library (v4)
- dualMocoLUFA firmware flashed onto the mega2560 r3, download the source from here http://morecatlab.akiba.coocan.jp/lab/index.php/aruino/midi-firmware-for-arduino-uno-moco/?lang=en
- Arduino 1.5.5-r2 software
- If you use the LED code you will need the adafruit neoPixel library and most likely an external power supply

As with any other arduino code, open the .ino in the arduino IDE, compile it and upload it to your mega2560, then burn the dualMocoLUFA firmware to the atmega16u2 on the arduino mega board.
