# External Stepper Drivers for Prusa MK2 based printers
Adds the ability to use external TMC stepper drivers on the Prusa MK2/S/2.5 (any printer that uses the Mini Rambo)

## Purpose
Since the Mini Rambo that powers the original line of Prusas was released, stepper driver technology has come a long way. Now days, the `A4982`s that are hard soldered onto the board are loader and less accurate than more modern offerings from Trinamic.

The mission with this is to take the solder pads on the back of the Mini Rambo, to a board where there is a socket for standard, off the shelf stepper driver boards. 

Upon seeing a certain other design on the internet that did the same thing, but was closed source, I decided to create my own design from scratch, and make it open source! You will find all KiCAD PCB Design files, along with the F3D files and STEP files for the case I have created. 

## Functionality
Tested mostly with the `TMC2208` drivers, however, `TMC2209`s, `TMC2130`s and `TMC2100`s (may require to be in their 'standalone' mode) have all been tested and confirmed to work with this board and the printer. However, do note the graphic towards the bottom left of the PCB for the correct positioning of the jumpers for your stepper drivers.

Compatible with any printer using the Mini Rambo main board, including but not limited to `Prusa i3 MK2`, `Prusa i3 MK2S`, `Prusa i3 MK2.5` and `Prusa i3 MK2.5S`.

## Using
This WILL require modifying your mainboard. However, the modification is not permant and can be reversed at any time. Only requires soldering to 8 points on the back of the main board. You will also need to get power for the board from somewhere. To do this you have 2 options:
  1. Tap into the 12V supplied from the printer's power supply and run a cable to the socket on the board.
  2. Run either a 12V or 24V external power supply and utilise that. 

The 24V option is your prefered option if you are wanting the drivers to operate as cool and quite as possible, however, it does add the complexity of a second power supply to your printer. Up to you of course.
#### Setting Stepper Current
My `TMC2208`s have been set to a Vref voltage of 1V[^1].

## What's Included?
In the repository you will find the KiCAD files if you wish to modify, adapt or improve the board and ~~a 3D printable case for the board, along with a STEP file if you wish to modify, adapat or improve it.~~ (yet to be added).
Please see the [releases](https://github.com/andrewandneil/external-stepper-prusa-mk2/releases) section to find the current Gerber files for the fabrication of the PCB.

## Pictures
To be added

## Cases

### My Case
As of the moment yet to be finalised

### Other People's Cases
In the offchance that someone either, modifies, redesigns, or creates from sctach a new case or related accessory, I'll do my best to add them here.
If you're one of amazing community that might create a case, get in touch with me and I'll link it here, along with any credit due.

## Parts List
Please see [here](/Guides/PartsList.md)

## Assembly Guide
Please see [here](/Guides/AssemblyGuide.md)

## What else
Notice how nowhere in this guide I mentioned the X and Y axis until now? Well, for good reason. If you wanted to you could build a board for the E and Z axis and use it in parallel to a X and Y board (or just use the E and Z board if you're weird like that I suppose). The Z motor plug will need to be split into 2 new plugs (one for ZL and ZR). The board labels the two sockets with X and Y identifiers, but this is more so you can trace which plug goes where. Obvisouly just connect either the X or Y plugs to the E or Z solder pads on the Rambo if you're planning on doing this.
However, logically with the X and Y axis doing the most moving and at the highest speeds, your best bet to make it mostly quiet is just making one for the X and Y.

## Future Plans
I have no clue if I will ever get around to implementing these plans but you might as well know about them (if I don't do them and you're reading this in the future please feel free to 'borrow' these ideas 😉):
  - Creating a board that allows X, Y, E and Z axis drivers.
  - Creating a 3D printable case for the board.
  - Test the board with even more drivers.
  - Create an easy to follow and detailed guide for assembly.

## Currently Known Issues
##### Will do my best to update if other issues are found
  - Z and E motors will 'squeal' if using TMC drivers on X and Y axis. I believe this to be something to do with microstepping. Only happens if the motors are powered and at a certain rotational degree. *Your quick fix here is to ignore it or make a board for the E and Z axis*

## Disclamer
I have tested this board extensively and have yet to run into issues, however, if you choose to do this mod, you do so at your own risk. I, nor any other party involved, offer any kind of warranty with this product. I have done my best to include all relevant information in this GitHub page, to allow you to come to a decision as to wether or not you would like to partake in this mod. This is not a product. You must source and assemble the board yourself. I will do my best to support any issues you may have if I can.

[^1]: My reference voltage and therefore stepper current is just a suggestion not a defintive do it. Do your own research and experimentation to suit your steppers and drivers.
