---
layout: post
title: Temperature Scanner Replacement Project Pt. 1
---

Some labmates of mine are in a tricky situation: for their project on melt electrospinning they use thermocouples to measure the temperature inside and around a molten pool of polymer a mere 10 cm away from a collector at -40 kilovolts (the *melt* and *electro-* parts of melt electrospinning, respectively). As well, this all needs to be done from the other side of a containment box for safety reasons. The real problem is that sometimes, just sometimes, all those kilovolts dont stay 10 cm away, they find the thermocouple leads and travel all the way to the temperature scanner. The result is much less catastrophic than one would expect, but still permanent death for that channel of the temperature scanner. Luckily our scanner had 10 channels to start with!

![_config.yml]({{ site.baseurl }}/images/T_breakout/Omega_dp1001.jpg)

Once the scanner lost a couple channels, we started looking into repair/replacement. The price of a replacement with similar functionality (read up to 10 thermocouples and display the temperature) was over $300, and if we wanted to add any features such as datalogging, the price climbs north of $500 fairly quickly. All that just to get us back to square one, without solving the problem of shocks to the system killing it. I had already been using a separate temperature monitoring setup using Adafruit Feathers and FeatherWings and Max31850 breakouts, so I suggested we could cobble together our own system that had all the features we wanted for a similar price. 

We made a list of the features we would like to have:

* 10 channels to read thermocouples, either simultaneously or sequentially
* datalogging capability, preferably in a way that it 

