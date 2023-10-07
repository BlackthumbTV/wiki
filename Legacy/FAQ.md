# FAQ
Below are some FAQs I see in the comments, which I mostly use to copy and paste for repeat questions.


### What did you do for tuning?
I use Haltech Elite 2500 standalone ECUs in my builds. The base tune Haltech provides was actually very close. I had to tweak fueling as usual, but ignition timing was good enough for me. One thing to note is that this car runs on E85 as well. Check out [my video about ECU tuning](https://www.youtube.com/watch?v=hRpR1lXKQL8) for more info.

### That big manifold will take forever to build boost
From datalogs of the ECU; the boost builds as fast as I can push the pedal between shifts (~200ms). I didn't change to a smaller pulley for faster boost response, I did so to get a higher peak pressure.

It takes substantially more intake manifold volume than this to see a tangible difference in throttle response. I've tuned an intercooled supercharged Miata, where there entire volume of the front mount air-air intercooler was after the throttle body, meaning it saw vacuum as well as boost. Only then did I notice a difference in time to build boost/vacuum, and it was still plenty drivable.

### That big manifold lowers your peak pressure, which is why you needed a smaller pulley
The engine this supercharger came on has a substantially bigger crank pulley (~7") than the one on this Subaru engine (~5.5"), thus the supercharger was spinning much faster in stock form.

Also, the size of the manifold does not correlate to peak boost pressure, only how long it takes to build said pressure, which is currently as fast as I can stab the throttle according to ECU datalogs.

`(Engine volumetric efficiency) vs (blower displacement * blower RPM)` is what determines peak pressure, from what I understand.

### What about intercooling?
I had considered intercooling, but [Richard Holdener did a video about the ZZP Intercooler](https://www.youtube.com/watch?v=7AhjNay2-bY) and, while it did drop intake temps substantially (~100f), it didn't net very much power at all (~15hp). 

He notes that with higher temps you risk detonation (knock), but this car is running on E85 so I'm not worried.

### What about doing a water/methanol injection system?
Water/methanol injection shouldn't be necessary at these boost levels, especially considering it's already running on E85. Even if boost was higher I'd still be comfortable without intercooling or water/methanol because I can run on a high octane fuel like E85.

### Have you considered better design / longer runners / porting the charger / ceracoting / whatever?
Is it worth it?  There may be a loss of power from the aggressive angles and such, but is it really that much? Probably not. 
I try not to focus on micro-optimization as it takes up so much time for so little reward. 
If I want more power I can just turn up the boost 🤷