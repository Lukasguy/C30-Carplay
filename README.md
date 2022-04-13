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

The MMM is located in the glovebox of the car. This is the actual navigation module which will send navigation VGA data to the RTI screen module. But because I'll use a Raspberry Pi for all the processing, this will not be needed anymore, so I can use this space to place all the modules in.

## Steering wheel controls

## Wiring everthing together

## Audio without extra wiring

The bluetooth audio connection from the phone to the car is preferred. This way I don't have to route any extra wires or select a different audio profile for the phone or the raspbery pi. 

When the phone is connected to carplay, the audio will also switch to carplay and has to be manually switched back to the bluetooth of the car each time the phone connects. Luckily this can be solved with a shortcut automation. 

This webpage was used as an inspiration to create the automation: 
https://jasonmurray.org/posts/2021/audiooutputshortcut/

It explains how to create a shortcut but the process for an automation is similar. Just create a new automation and pick "Carplay" -> "When carplay connects". Then assign this with: "Set Playback Destination" from the scripting menu. For the car's bluetooth to show up, you have to be connected to it, so this must be done in the car when connected. 
