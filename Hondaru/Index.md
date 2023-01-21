# Honda Swapped Subaru Impreza
My 2000 Subaru Impeza RS Coupe that I swapped with a Honda K24A2.

 - [YouTube video playlist](https://www.youtube.com/watch?v=Z-DdCNjM8aU&list=PLFQKxsMzgSbg17kyCzaNmexq7qo9Ydp6C)


## Introduction
After being out of the car scene for a while, I opted to jump back in with this swap. It was also the first thing I posted on YouTube about. Ahhh, memories...

 It uses an off-the-shelf adapter plate to adapt the Honda engine to the Subaru trans, thus maintaining the classic Subaru AWD. See the parts list below for all that.

After driving the car around for a year I ended up taking it to the dyno and [blowing it up](https://www.youtube.com/watch?v=2WlubEBycJc), making 466hp at the same time. Very cool.

## Parts list
Here's most of the stuff I used on the Hondaru build.

### Engine
 - Stock K24A2
 - Stock Subaru 5 Speed Transmission
 - Haltech Elite 2500 ECU
 - Subaru Gears Honda K Series Adapter Plate [Link](https://www.subarugears.com/product/honda-k-series/)
 - Clutch Masters FX400 Clutch [Link](https://clutchmasters.com/i-30505729-subaru-xv-crosstrek-2013-2015-2-0l-15013-hdc6.html)
 -  FIC 1200CC Fuel Injectors [Link](https://fuelinjectorclinic.com/Honda/K(01-11)-D17-S2K(06-09)/IS116-1200H) [Backup](./parts/Injectors.pdf)
    - These ended up being too small for even 12psi of boost, so I later upgraded to 2150s from FIC as well.They were very understanding and ended up giving me good deal on them.
 - Fuel Rail [Link](https://www.ebay.com/itm/323608063092)

```csharp
new("Fuel Rail", BuildItemCategory.Engine, "https://www.ebay.com/itm/323608063092", "hondaru/FuelRail.pdf"),
new("Fuel Pressure Regulator", BuildItemCategory.Engine, "https://www.ebay.com/itm/254749363596", "hondaru/Fpr.pdf"), 
new("Exhaust Manifold", BuildItemCategory.Engine, "https://www.ebay.com/itm/350792031715", "hondaru/ExhaustManifold.pdf"),
new("Upper Coolant Housing", BuildItemCategory.Engine, "https://www.ebay.com/itm/114238768136", "hondaru/UpperCoolant.pdf"),
new("Swivel Thermostat Housing", BuildItemCategory.Engine, "https://www.ebay.com/itm/113520236147", "hondaru/ThermostatHousing.pdf"),

new("GT3582 Turbocharger", BuildItemCategory.Turbo, "https://www.ebay.com/itm/313405020842", "hondaru/Turbo.pdf"),
new("Blow Off Valve", BuildItemCategory.Turbo, "https://www.ebay.com/itm/323976370478", "hondaru/Bov.pdf"),
new("Air Water Intercooler Exchanger", BuildItemCategory.Turbo, "https://www.ebay.com/itm/284284503552", "hondaru/AWICExchanger.pdf"),
new("Air Water Intercooler", BuildItemCategory.Turbo, "https://www.ebay.com/itm/183903814619", "hondaru/AWIC.pdf"),
new("Wastegate", BuildItemCategory.Turbo, "https://www.ebay.com/itm/151739405815", "hondaru/Wastegate.pdf"),
new("Turbo Oil Feed (turbo kit didn't have right one...)", BuildItemCategory.Turbo, "https://www.ebay.com/itm/264004884925", "hondaru/OilFeed.pdf"),

new("ISC Suspension N1 Street Sport Coilovers", BuildItemCategory.Body, "https://www.rallysportdirect.com/part/coilovers/s001-s-isc-suspension-n1-street-sport-coilovers", "hondaru/Coilovers.pdf"),
new("Firehawk Indy 500 Tires", BuildItemCategory.Body)

```