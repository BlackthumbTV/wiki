# Manual Swap Parts List
Below is a quick list of things you need to complete an auto-to-manual transmission swap on a Subaru. This is a work in progress, but should get you started.

- Manual Transmission
- Manual Transmission Mount/Crossmember
- Matching Rear Differential 
  - IE if your trans has a 3.9 FD, you need a 3.9 FD rear diff.
  - Best bet is to pull the diff from the MT donor car. If you can't, look up your trans code on [LegacyPic](https://legacypic.uk/transmission/) to find the FD, and find a matching rear diff.
- Matching Driveshaft
  - The automatic transmission itself is *longer* than the 5 speed, thus its drive shaft is *shorter* than a 5MT drive shaft. 
  - If you're swapping to a 5 speed, you need the *longer* 5MT drive shaft for the *shorter* five speed.
  - 6 speed transmissions are actually longer than the 5 speeds, so the above doesn't apply. 
    - You can use the 4EAT drive shaft with a 6MT.
- Axles (Maybe)
  - If you have a "male" transmission (IE your transmission has axle stubs), then you need "female" axles (IE they pop over the male axle stubs, and are secured with a roll pin).
  - Some transmissions are "female", IE they don't have axle stubs and instead the axle is "male" and pops directly into the trans.
  - So, if you have a "female" trans and "female" axles, you have one of two options
    1. You can just buy "male" axles.
        - You'll need left/right axle seals (below).
    2. You can get "axle stubs" to convert your "female" trans to "male".
        - Axle Stub Shafts (x2): `38415AA110`
        - Axle Circlips (x2): `805329010`
        - Seals
            - Left: `806730041`
            - Right: `806730042`
        - These parts may be able to be sourced from your 4EAT, though I haven't tried this.
  - The opposite is true for a male-male situation.
- Clutch assembly
  - Flywheel, pressure plate, pilot bearing
    - Some transmissions have push-type clutches, such as N/A cars and a range of more modern (2006+?) WRXs.
    - Others have pull-type clutches, such as the 02-05 WRX/STIs (and others).
    - Be sure to get the proper clutch setup based on whatever the trans requires.
  - You'll need the longer MT flywheel bolts as well. The AT flex plate bolts are too short to bolt the flywheel to the crank.
- Clutch/Brake Pedal box assembly
- Master/Slave Cylinder
  - or clutch cable assembly, though you'd probably want to go hydro clutch if possible.
- Manual Starter motor
- Shifter assembly
  - This includes the rear bushing/mount
  - The 6MT shifter assembly is different from the 5MT, as it has the reverse ring that you pull up on to put the car in reverse.

# Wiring
I've mostly manual swapped older Subarus, such as a 2000 Impreza 2.5 RS Coupe and a 1999 Legacy Sedan, so this info mainly pertains to cars of that vintage, but it's probably worth checking if it applies to your swap too.

Lots of car manufacturers use a different ECU for auto vs manual cars, so you'd need to get a "manual ECU" for your swap.

Subaru does not do this, the ECUs are the same for AT vs MT. There's a special pin on the ECU called the `AT/MT Identification` pin. In MT cars, it is permanently grounded which tells the ECU that it's supposed to run in manual mode. In AT cars, there isn't even a pin in the harness for it, so it remains un-grounded and thus in auto mode.

This means that, if you're manual swapping a Subaru, you don't need to get a different ECU. You can just shove some wire into the back of the connector for that pin and ground it out somewhere and the ECU will just run in manual mode. 

What pin that is depends on the make/model of the car you're swapping. Lookup an ECU pinout for your car, and try to find that `AT/MT Identification` pin in it. Ground it out.

Note that if you don't do this, the car will still run but it'll idle all weird and suck to drive. But it'll still run.