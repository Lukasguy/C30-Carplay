# C30-Carplay
Add Apple carplay to built in C30 navigation. 

Based on the following project:
https://github.com/laurynas/volvo_crankshaft

## Modifying the RTI screen

The RTI screen has been modified in the same way as in the volvo_crankshaft project above. I decided not to glue in the LCD to the plastic cover, but to design and 3d print mounts which are glued to the edges of the back of the LCD. These can be used to screw the display onto the frame the same way as the original, and another plus is that the display can be easily alligned perfectly. 

The displays controller board has been mounted on the back of the display with the back taped off the prevent shorts on the metal of the LCD. 

I've soldered 4 wires which run to the original data connector & power connectors of the RTI module:
* Power which is connected to the ACC ignition switched 12V connector
* Ground which is connected to the ground of the power connector
* power button pin which is connected to pin 1 of the origin data connector
* source button pin which is connected to pin 5 (need to check this) of the original connector

Pin 10 of the data connector has been connected to the ACC 12V switched signal of the power connector. This will tell the custom MMM box the status of the ignition. 

## Replacing the MMM with a custom box

The original volvo_crankshaft project this is based on keeps everything in the RTI screen cutout. But because I want to add carplay I will need some more space. Carplay works via OpenAuto pro and uses a dongle. I've also decided to use a switch to turn the raspberry pi on and off. This has been supplied to me by mausberry circuits and will take a bit of extra space. All these components will not fit in the small space of the RTI module cutout, so I'll need to place them somewhere else. 

The MMM is located in the glovebox of the car. This is the actual navigation module which sends navigation VGA data to the RTI screen module. But because I'll use a Raspberry Pi for all the processing, this will not be needed anymore, so I can use this space to place all the modules in.

Modules contained in this box:
* Raspberry Pi: Used to run carplay and show image on the screen using HDMI output (I'm using a Raspberry Pi 4)
* Arduino Pro Micro: Used to send serial data to open/close the RTI screen, turn the screen on/off and toggle the LCD input source. Is also connected to the LIN bus using MCP2004A chip to read steering wheel buttons which are then converted into keyboard key pressed to control the Raspberry Pi
* Carlinkit dongle: Contains the code for Apple Carplay. Needed by OpenAuto Pro
* Audio outputs: Officialy required by OpenAuto Pro but is not actually needed. But I've included it in case it is ever needed
* Bluetooth Dongle: Required for OpenAuto Pro and wireless carplay
* Mausberry Circuits Car switch. Used to power the Pi and other devices. Will switch everything on/off with the ignition

I dremmeled the origin MMM module a bit to remove the power and data connector board section. I've reused these and solderd the required connections on the pins. This way the original data and power connectors can be reused. 

The ACC signal is not supplied to the MMM, but it is supplied to the RTI module. This is why I connected the ACC signal to pin 10 of the data cable. This way the original cable is reused to carry these signals to the MMM (and the other way around). 

## Steering wheel controls

## Wiring everthing together

## Audio without extra wiring

The bluetooth audio connection from the phone to the car is preferred. This way I don't have to route any extra wires or select a different audio profile for the phone or the raspbery pi. 

When the phone is connected to carplay, the audio will also switch to carplay and has to be manually switched back to the bluetooth of the car each time the phone connects. Luckily this can be solved with a shortcut automation. 

This webpage was used as an inspiration to create the automation: 
https://jasonmurray.org/posts/2021/audiooutputshortcut/

It explains how to create a shortcut but the process for an automation is similar. Just create a new automation and pick "Carplay" -> "When carplay connects". Then assign this with: "Set Playback Destination" from the scripting menu. For the car's bluetooth to show up, you have to be connected to it, so this must be done in the car when connected. 
