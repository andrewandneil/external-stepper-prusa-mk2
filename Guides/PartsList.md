# Parts You'll Need

### REQUIRED:
  - 1x printer with a functional Mini Rambo.
  - 1x PCB (find the gerber files for production [here](https://github.com/andrewandneil/external-stepper-prusa-mk2/releases/latest)).
  - 1x 2x8 2.54mm Pitch IDC cable.
  - 1x 2x8 2.54mm Pitch IDC PCB through-hole socket.
  - 2x stepper drivers (on breakout boards) of your choice ([see here for a list of working drivers](#your-stepper-driver-options)).
  - 2x Molex SL 1x4 2.54mm Pitch Male Vertical connectors.
    - [For example this from Digikey](https://www.digikey.co.uk/en/products/detail/molex/0705430003/114923).
    - Can be difficult to find these. You can of course suppliment them with standard 1x4 2.54mm pitch male headers if you wish.
  - 1x 2x3 2.54mm Pitch Male header.
  - 4x 1x8 2.54mm Pitch Female headers.
  - 2x 10K 0805 Resistors.
  - 1x wire-to-board terminal block, 5mm pitch with 2 terminals. (you could of course solder the power wires directly to the board if you'd like. Personally I would still use the terminals).
    - Something like:
      - [This from Farnell UK](https://uk.farnell.com/phoenix-contact/mkdsn-1-5-2-5-08-ht-bk/tb-wire-to-brd-2pos-16awg-blk/dp/3241413).
      - [This from Digikey](https://www.digikey.co.uk/en/products/detail/phoenix-contact/1729128/260615?utm_adgroup=General&utm_source=google&utm_medium=cpc&utm_campaign=PMax:%20Smart%20Shopping_Product_Zombie%20SKUs&utm_term=&productid=260615&gclid=EAIaIQobChMIssap6vvQ_AIVE7rtCh29Aw1REAQYBCABEgKNa_D_BwE).
      - Or [this on Amazon US](https://www.amazon.com/KeeYees-60pcs-Terminal-Connector-Arduino/dp/B07H5G7GC6/ref=sr_1_6?content-id=amzn1.sym.ea945d40-8e84-42be-ad5c-249b9bca6a40%3Aamzn1.sym.ea945d40-8e84-42be-ad5c-249b9bca6a40&crid=83SSXJ9RMVZE&keywords=Terminal+Blocks&pd_rd_r=26ee9c77-86ff-4422-a09c-97c0d5ea3cb3&pd_rd_w=kJu0E&pd_rd_wg=VTSuz&pf_rd_p=ea945d40-8e84-42be-ad5c-249b9bca6a40&pf_rd_r=K55BBQQSG0D345R0BP72&pid=N3qS6tE&qid=1674040094&refinements=p_n_feature_nine_browse-bin%3A18644601011&s=industrial&sprefix=terminal%2Bblock%2Caps%2C145&sr=1-6), only the 2 pin terminal type is required.
  - 2x 100uF 25V Radial capacitors, 6.3mm diameter and 2.50mm pitch.
    - Something like: 
      - [This from Farnell UK](https://uk.farnell.com/panasonic/eca1ehg101/cap-100-f-25v-20/dp/9692827).
      - Or [This from Digikey](https://www.digikey.co.uk/en/products/detail/rubycon/25ZL100MEFC6-3X11/3563144).

### Optional:
  - If you want to use an external power supply to power your drivers:
    - **DISCLAIMER: IF YOU CHOOSE THIS ROUTE YOU WILL BE MESSING WITH MAINS VOLTAGE. WETHER YOU BE IN A 110V or 240V COUNTRY THESE VOLTAGES CAN, AND WILL, KILL YOU IF NOT DONE PROPERLY. EITHER GET A QUALIFIED ELECTRICIAN TO HELP YOU OR JUST USE THE PRINTER'S SUPPLY!**
    - Honestly, here is where I am not going to help you with a specific part. 
    - You'll want either a 12V or 24V PSU (I recommend you just go for 24V if you're doing external anyway). 
    - You'll need to know how much current your steppers+drivers are going to use and do a simple `P=I*V` calculation to figure out your wattage. And remember to always OVER estimate your wattage and have headroom!!
    - **Please DO NOT buy a cheap Chinese PSU. Buy something decent if you're doing this, something like a Meanwell**.
  - If you wish to install a fan[^1][^2]:
    - 1x Pin Header, Square Pin, Signal, Wire-to-Board, 2.54 mm, 1 Rows, 3 Contacts, Through Hole Straight.
      - Something like:
        - [This from Farnell UK](https://uk.farnell.com/molex/22-27-2031/connector-header-3pos-1row-2-54mm/dp/9731156).
        - Or [This from Digikey](https://www.digikey.co.uk/en/products/detail/molex/0022232031/26669).
    - 1x Fan.
      - Something like a 40x10mm fan would do nicely for most drivers (a Noctua A4x10 ([Amazon US](https://www.amazon.com/Noctua-Cooling-Blades-Bearing-NF-A4x10/dp/B009NQLT0M/ref=sr_1_3?crid=33FNCQDU3NYH0&keywords=noctua+40mm&qid=1674041726&sprefix=noctua+40m%2Caps%2C141&sr=8-3), [Amazon UK](https://www.amazon.co.uk/Noctua-NF-A4x10-Premium-Quiet-40x10mm/dp/B009NQLT0M/ref=sr_1_3?crid=BEIZPO650BP9&keywords=a4x10&qid=1674041751&sprefix=a4x10%2Caps%2C71&sr=8-3)) is perhaps your best option for 12V).

### Tools and Other:
  - Solder.
  - Soldering Iron.
  - Kapton Tape.
  - ~~If adding my 3D Printed case:~~ !(hasn't been finalised yet)!
    - ~~3D Printed case; [found here](https://www.printables.com/social/239130-utterotter/).~~
    - ~~x4 M3x10 Bolts.~~
    - ~~x4 M3 Nuts.~~
    - ~~x2 M3x18 Bolts.~~
  - Various HEX keys for disassembly of the printer.
  - Zip ties to replace cut zip ties during disassembly.
  - Some 20AWG or better guage wire for power delivery.
    - If you choose (and you should) to crimp the ends of these wires:
      - Crimper tool.
      - Crimps.

## Your Stepper Driver Options
Please note these are ones I have tested and worked with my Prusa i3 MK2.5S+.

This board can't magically add sensorless homing to your printer. Any driver that supports this mode will, and can work, but the endstop sensors of the printer are still required.

All drivers must be in their respective standalone modes (i.e. SPI/UART disabled). If you're not sure how to do that for your specific choice of driver Google is your friend.

Make sure your drivers have some form of heatsink included. If not I recommend you buy a fairly large heatsink for the driver.

### IMPORTANT: don't just buy the chip. You need the chip on a breakout board!
   - `Trinamic TMC2208`
     - Must have UART disbaled. (if you're not sure what that is or how to disbale it most `TMC2208` breakout boards have UART disabled by default).
     - One of the easiest and cheapest ways of getting quiet stepper drivers. 
     - Will run moderately hotter than the more modern `TMC2209`.
   - `Trinamic TMC2209`
     - Perhaps the best all round option.
     - Runs the quietest and coolest out of the four options listed here.
     - Sensorless homing does go to waste, along with other driver to board communication functions.
   - `Trinamic TMC2130`
     - Chris Riley has a great [YouTube video](https://www.youtube.com/watch?v=Jh8iwqc1TP0) on how to use the `TMC2130`s in standalone mode. Give it a watch
     - Runs in stealthChop or spreadCycle depending on jumper setup.
   - `Trinamic TMC2100`
     - Perhaps the least relevant option today.
     - Setup is very similar to `TMC2130`.
     - In my test it was the loudest of the four.
     - Runs in stealthChop or spreadCycle depending on jumper setup.

I am sure there are other drivers that are compatible with this setup. Please see [advanced tuning](/Guides/AdvancedTuning.md) if you wish to figure out if your chosen stepper driver is compatible.

[^1]: The fan will run at the voltage you are using for the power input into the board. So if you're running an external 12V power supply or tapping into the power from the printer you will need a 12V fan, or if you're using an external 24V power supply you will need a 24V fan.
[^2]: Fan is not strictly nessecary as if you have large enough heatsinks on your drivers, and don't run the motors at insane current levels, the drivers are perfectly capable of being passively cooled.
