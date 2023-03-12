# First Run
I went with the Open Inverter logic board for my Tesla LDU. Getting it working was a chore, and I ran into a few blockers, all of which were my fault.

## Settings
I spun my motor up using 24v to start with, just for testing. I started with the default parameters from the Open Inverter parameter site. aHere's the settings I had to change to get it to run on 24v.

1. `udcmin`, `udcsw`, and `udcnom` must all be set to zero.
  - I left `udcnom` at the default value, which set boost to something like 22000. The motor ended up drawing many hundred of amps, which was not ideal. 
2. `boost` must be raised up a bit. Default was `1850`, I changed it to `6000` and the motor was drawing a good 22a while spinning up.
3. Configure your `potmin` properly.

## Board Issues
I had one problem with the board I got from the Open Inverter shop. There was a very small solder ball between two of the pins on the microcontroller that I ended up having to reflow.

I also had some issues that were my own fault, which all came down to my solder flux being quite conductive and causing erronious readings. I ended up giving the boarrd an alcohol bath and scrubbing everything with a tooth brush which resolved the issues.