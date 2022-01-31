# C30-Carplay
Add Apple carplay to built in C30 navigation


# Solving the audio problem

The bluetooth audio connection from the phone to the car is preferred. This way I don't have to route any extra wires or select a different audio profile for the phone or the raspbery pi. 

When the phone is connected to carplay, the audio will also switch to it and has to be manually switched each time the phone connects. Luckily this can be solved with a shortcut automation. 

This webpage was used as an inspiration to create the automation: 
https://jasonmurray.org/posts/2021/audiooutputshortcut/

It explains how to create a shortcut but the process for an automation is similar. Just create a new automation and pick "Carplay" -> "When carplay connects". Then assign this with: "Set Playback Destination" from the scripting menu. For the car's bluetooth to show up, you have to be connected to it, so this must be done in the car when connected. 
