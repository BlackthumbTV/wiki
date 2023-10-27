# Airflow Graphing
In [This Video](https://www.youtube.com/watch?v=9-RtJrj18uY) I graphed my mass airflow sensor to tune VVL/VVT, instead of using a dyno like one would typically do. It's important to note that I graphed Airflow vs RPM, as opposed to Airflow vs Time which is what most tuning/datalogging software defaults to. I ended up writing a quick web app to do this as my the Haltech software couldn't be configured to changed to do that (that I know of).


## Graphing Airflow with Speed Density/MAP Sensor
You COULD technically graph you Volumetric Efficiency table, and then correct it using your Lambda readings vs Target AFR.

MAF sensors are very clever devices that almost directly let us measure the amount of air flowing into the engine, usually in grams of air per second.

Speed Density setups don't technically measure the air going into the engine, they take a very educated guess (or assumption, even) at how much air is going in, which can also be represented in grams of air per second. In fact, the Haltech has a datalogging channel specifically for this.

The trouble is, it's normal in an SD setup for there to be some amount of error. In fact, as we tweak these cam values, we're actually inducing error as we're quite literally changing our engines volumetric efficiency. So, whatever error we accumulate, we must apply to our "guessed" or "assumed" airflow from Speed Density.

So, if you can get your speed density airflow in g/s, apply the lambda error (actual AFR vs target AFR), we can maybe make a good stab at what the airflow is. Though it may be less reliable or noisier than what a MAF would provide. Maybe.

It's also worth noting that, with the Haltech, you can wire up a MAF and use it only for datalogging. No need to run the car with it!