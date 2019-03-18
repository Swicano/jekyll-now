---
layout: post
title: Temperature Scanner Replacement Project Pt. 1
---

Some labmates of mine are in a tricky situation: for their project on melt electrospinning they use thermocouples to measure the temperature inside and around a molten pool of polymer a mere 10 cm away from a collector at -40 kilovolts (the *melt* and *electro-* parts of melt electrospinning, respectively). As well, this all needs to be done from the other side of a containment box for safety reasons. The real problem is that sometimes, just sometimes, all those kilovolts dont stay 10 cm away, they find the thermocouple leads and travel all the way to the temperature scanner. The result is much less catastrophic than one would expect, but still permanent death for that channel of the temperature scanner. Luckily our scanner had 10 channels to start with!


<figure>
  <img src="{{site.baseurl}}/images/T_breakout/Omega_dp1001.jpg" alt="Omega DP1001" width="200"/>
  <figcaption> *The old Omega temperature scanner with 3 channels left.* </figcaption>
</figure>


Once the scanner lost a couple channels, we started looking into repair/replacement. The price of a replacement with similar functionality (read up to 10 thermocouples and display the temperature) was over $300, and if we wanted to add any features such as datalogging, the price climbs north of $500 fairly quickly. All that just to get us back to square one, without solving the problem of shocks to the system killing it. I had already been using a separate temperature monitoring setup using Adafruit Feathers and FeatherWings and Max31850 breakouts, so I suggested we could cobble together our own system that had all the features we wanted for a similar price out of those. 

We made a list of the features the old scanner had and some new ones we'd like:

* Cheaper than a new Omega scanner
* Standalone operation, like old scanner
* 10 Thermocouple channels, like old scanner
* Display current temperature
* Datalogging to file (SD card), *new* 
* Replaceable parts, *new* 
* be 30 kV shock proof, *new*


That last one might be a bit hard to come by, so if that doesn't work out, having replaceable channels or individual parts should still be a large improvement. That way if a channel gets fried, we can replace just that channel, instead of the whole scanner.

We decided on using an [Adalogger M0](https://www.adafruit.com/product/2796), since it is very affordable and includes a microSD writer for logging, and options for a battery in case 




![_config.yml]({{ site.baseurl }}/images/T_breakout/Omega_dp1001.jpg)
