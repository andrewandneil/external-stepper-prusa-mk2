# Assembly Guide

## Step 1
As with any guide you will need to check you have all the required [parts](/Guides/PartsList.md).
Here is a quick overview to double check you have everything for the PCB side:
  - 1x PCB
  - 1x IDC Connector
  - 2x 0805 Resistors
  - 2x Capacitors
  - 1x Terminal Block
  - 1x 2x3 Male Pin Headers

Optionally:
  - 1x Fan Header
  - 4x Female Pin Headers

<img src="/Photos/Photos%20for%20Guide/01_PartsLaidOut.png" width="400">

## Step 2
Now you'll need to solder everything to the board. I'm not going to baby step you through this step, as you should already know how to do this.

A general rule of thumb for soldering components to a PCB is to start with the shortest components first and work your way up.

Here you can also choose to add the 1x8 female pin headers or just solder the chips directly to the board. (I recommend using the pin headers).

<img src="/Photos/Photos%20for%20Guide/02_SolderedBoard.png" width="400">

You will also need to set your jumper configurations now. If you look at the bottom left of the PCB (also shown in image below) you should see a diagram for how you will need to do it. Make sure you configure these correctly for your driver! Incorrect configuration will likely cause wildly incorrect axis movements.

<img src="/Photos/Photos%20for%20Guide/02_JumperConfigs.png" width="400">

Make sure your jumpers are configured for your chips as below:

**`TMC2208` or `TMC2209`:**

<img src="/Photos/Photos%20for%20Guide/02_TMC22089.svg" width="400">

**`TMC2130` or `TMC2100` spreadCycle:**

<img src="/Photos/Photos%20for%20Guide/02_spreadCycle.svg" width="400">

**`TMC2130` or `TMC2100` stealthChop:**

<img src="/Photos/Photos%20for%20Guide/02_stealthChop.svg" width="400">

## Step 3
Now you need to take your 8 pin IDC cable and cut off one end. Hopefully, you'll have a cable where the 2 ends point different directions. You'll most likely want the direction that allows the cable to come directly away from your PCB rather than needing to over it:

<img src="/Photos/Photos%20for%20Guide/03_IDCCut.png" width="400">
<img src="/Photos/Photos%20for%20Guide/03_IDCwithPCB.png" width="400">

## Step 4

## Step 5
**This step is very important! Pay close attention and double check what you're doing or it could result in damage to either your Mini Rambo or stepper drivers!**

Now you need to take your IDC cable and solder it to the points shown below. If I were you I would cut the individual cables to length as you go to get a nice clean and uniform look. See the image in [Step 6](#step-6) for a better look.

**YOU MUST DOUBLE CHECK THAT YOU HAVE THE CORRECT PIN ON RAMBO TO THE CORRECT PIN ON THE PCB**
  * You can check this by using a multimeter and ensuring that the label on the back of the PCB corresonds to the correct test point on the back of the Mini Rambo.
  * The labels for the pins can be found on the back of the PCB next to the corresponding pin on the IDC connector.

###### If you're doing this mod for the Z and E axis it goes without saying that you should replace X and Y with E and Z.

| Test Point Label on the Mini Rambo | Corresponding Label on PCB |
|------------------------------------|----------------------------|
| XDIR | XDIR |
| XSTEP | XS |
| XEN | XEN |
| YDIR | YDIR |
| YSTEP | YS |
| YEN | YEN |

<img src="/Photos/Photos%20for%20Guide/05_PointsOnRambo.png" width="400">
<img src="/Photos/Photos%20for%20Guide/05_PCBPoints.png" width="400">

## Step 6
Last two points to solder to the Rambo is the GND and VCC Pins.

These two points are rather simple and just need to be soldered as below.

<img src="/Photos/Photos%20for%20Guide/06_GNDVCCRambo.png" width="400">

With that all completed the back of your Mini Rambo should look something like this:
<img src="/Photos/Photos%20for%20Guide/06_CableOnRambo.png" width="400">

## Step 7
Nice! You've finished the hard part! Give yourself a pat on the back. Now we need to do the fun bit, wiring!

This is where the guide will split into two for a bit, [Step 7-1](#step-7-1) is for the people using the printer's power supply and [Step 7-2](#step-7-2) is for those of you using external power supplies.

### Step 7-1
#### For people using the printer's power supply

You will now need to tap into the 12V power rails for the Mini Rambo. As a general rule use the `PWR IN` power lines and not the `BED IN` power lines to avoid potential issues.

There are multiple ways of doing this: 
  - You can solder the wires directly to the back of the `PWR IN` terminal on the back of the Mini Rambo. 
    - I wouldn't recommend this as it's more difficult and you're more likely to damage somehting in the process.
  - You can add additonal wires to the crimp connector on the Mini Rambo side of the power supply.
    - This is the option I choose as it required the least wire and least disassembly.
  - Or you can tap into the terminals on the printer's power supply, i.e. direct from the source.
    - **THIS METHOD REQUIRES MESSING WITH AN AREA DESINGED FOR MAINS VOLTAGE. WETHER YOU BE IN A 110V or 240V COUNTRY THESE VOLTAGES CAN, AND WILL, KILL YOU IF NOT DONE PROPERLY. EVEN IF THE POWER CABLE IS REMOVED THE CAPACITORS CAN STILL HOLD A DEADLY CHARGE. EITHER GET A QUALIFIED ELECTRICIAN TO HELP YOU OR CHOOSE ONE OF THE OTHER TWO OPTIONS**
    - With that being said, it's perhaps one of most secure options, however, requires disassembly of the printer's power supply shroud.

Whichever option you choose, it's always a good idea to check for shorts before continuing.

What I did was take my wires and wrap them around the wires already inside the crimp terminals on the Rambo. I then placed the crimp+wire combination back inside the terminal and clamped it down. I know it doesn't sound the best but nothing has gone wrong yet and the connection is very solid.

I am sure if you've gotten this far in the mod you know what you're doing at least somewhat. Make your own decisions with the information provided.

What my connector looks like:
<img src="/Photos/Photos%20for%20Guide/07_PowerCable.png" width="400">

Now go onto [Step 8](#step-8).

### Step 7-2
#### For people using an external 12V or 24V power supply
**I WOULD LIKE TO STESS AGAIN THAT IF YOU CHOOSE THIS ROUTE YOU WILL BE MESSING WITH MAINS VOLTAGE. WHETHER YOU BE IN A 110V or 240V COUNTRY THESE VOLTAGES CAN, AND WILL, KILL YOU IF NOT DONE PROPERLY. EITHER GET A QUALIFIED ELECTRICIAN TO HELP YOU OR JUST USE THE PRINTER'S SUPPLY!**

(I know, I know, this is the 3rd time I've mentioned it, but trust me I know from experience you do not want 240V coursing through your veins! ☺️)

This step depends heavily on your choice of power supply. However, it is likely that:
  - You will need to wire Live, Neutral and Earth to their respective terminals.
  - You will need a wire from GND on the PSU to the `-` on the PCB.
  - You will need a wire from 12/24V on the PSU to the `+` on the PCB.
  - You will need to ensure that if your PSU comes with a voltage switch that you set it to your local voltage.
  - And I **STRONGLY** recommend some form of 3D printed cover to go over the terminals when you're done. Exposed mains voltage is no joke.

Also, do not connect the external PSU to the Rambo in any way! Only connect it to the `+` and `-` on the breakout board.

Now go onto [Step 8](#step-8).

## Step 8
Now it's time for reassembly. 

>__Warning__
>
>I strongly recommend you double check you have wired everything correctly between the Mini Rambo and the breakout board using a multimeter, whilst you still have it out the case.
>
>Check the polarity one last time (as shown in [Step 5](#step-5)). Once you've confirmed everything is good, you can continue.

Take your Mini Rambo and place it back into the Mini Rambo's housing. Place the housing back onto the printer and plug all the wires back in. However, leave the X and Y (or the E and Z, depending) stepper motor cables unplugged from the Mini Rambo. We will need to plug these into your breakout board in order for the drivers to, well, drive them.

<img src="/Photos/Photos%20for%20Guide/08_RamboBackOnPrinter.png" width="400">

## Step 9
Now you're going to want to plug all the connectors into the board.

You may already know where everything goes but here's a reminder:
  1. `Board Input` IDC Connector. This is where you plug in the IDC cable that you soldered to the back of the Mini Rambo
  2. `X Motor` Molex SL. This is where the plug for the X axis stepper goes into.
  3. `Y Motor` Molex SL. This is where the plug for the Y axis stepper goes into.
  4. `X Driver` x2 1x8 Female Headers. This is where you plug in the stepper driver for your X axis.
  5. `Y Driver` x2 1x8 Female Headers. This is where you plug in the stepper driver for your Y axis.
  6. 2x3 Male Header. This is where you will need to set your jumper configurations. See [Step 2](#step-2) if you havent configured them already.
  7. `Fan` 1x3 (if installed). This is where you can optionally plug in a fan.
  8. `12/24V GND` 2 port Terminal. This is where you should have placed your power wires from [Step 9](#step-9). If you're using my case you will need to remove them for the next step.

<img src="/Photos/Photos%20for%20Guide/09_Connectors.png" width="400">

## Step 10

### This part of the guide is written for my version of the case. Suppliment this step if using a 3rd party case, your own design, or no case at all.
It's time for a case. 

If using my case make sure you have on hand:
  - 1x Case.
  - 2x Arm Pieces.
  - 4x M3x10 Bolts. (2 of these bolts can be salvaged from the Mini Rambo's mounts as we replace them with longer bolts)
  - 4x M3 Nuts.
  - 2x M3x?? Bolts.

##### Please note this case is likely to change as I improve the design. The concept should remain the same, but do not be alarmed if your case looks different to the one in the photos

  1. Take the two 'arm' pieces of the case and push fit them into the part designed to house the board.
<img src="/Photos/Photos%20for%20Guide/10_ArmInsertion.png" width="400">

  2. Now install the breakout board into the case (note: you may need to remove the power cables temporarily from the board if installed. Place them back in when the PCB is inside the case).
<img src="/Photos/Photos%20for%20Guide/10_PCBInstall.png" width="400">

  3. Place the 4 M3 nuts into the hexagon shapped holes on the back of the case.
<img src="/Photos/Photos%20for%20Guide/10_NutsInstall.png" width="400">

  4. Now install the 4 M3x10 screws, and tighten them into the nuts.
<img src="/Photos/Photos%20for%20Guide/10_M3x10Bolts.png" width="400">

  5. Take the bottom two screws and nuts out of the Rambo (if not done already) and push the hexagon protrusions into the cavity left by removing the nuts.
<img src="/Photos/Photos%20for%20Guide/10_RamboBoltRemoval.png" width="400">
<img src="/Photos/Photos%20for%20Guide/10_ProtrusionsInstall.png" width="400">

  6. Add the removed nuts to the holes behind the protrusions.
<img src="/Photos/Photos%20for%20Guide/10_NutsBackToRambo.png" width="400">

  7. Now simiply add your M3x?? screws through the Mini Rambo into the installed nuts.
<img src="/Photos/Photos%20for%20Guide/10_LongM3BoltsRambo.png" width="400">

Congratulations you now have the case installed.

