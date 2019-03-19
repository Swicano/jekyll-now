---
layout: post
title: Temperature Scanner Replacement Project Pt. 1
---


Some labmates of mine are in a tricky situation: for their project on melt electrospinning they use thermocouples to measure the temperature inside and around a molten pool of polymer a mere 10 cm away from a collector at -40 kilovolts (the *melt* and *electro-* parts of melt electrospinning, respectively). As well, this all needs to be done from the other side of a containment box for safety reasons. The real problem is that sometimes, just sometimes, all those kilovolts dont stay 10 cm away, they find the thermocouple leads and travel all the way to the temperature scanner. The result is much less catastrophic than one would expect, but still permanent death for that channel of the temperature scanner. Luckily our scanner had 10 channels to start with!


<p align="center">
  <img src="{{site.baseurl}}/images/T_breakout/Omega_dp1001.jpg" alt="Omega DP1001" align="center" width="500"/>
  <p align="center">_The old Omega temperature scanner with 3 channels left._ <p align="center">
</p>


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

### Design

The temperature sensor we decided on was the [MAX31856 breakout](https://www.adafruit.com/product/3263) at $17.50. The setup I previously used is [MAX31850T](https://cdn-shop.adafruit.com/datasheets/MAX31850-MAX31851.pdf) based, which is cheap and uses 1-wire, but isnt available as a breakout board (only the K-type is), and requires extra processing to convert the output to the true temperature. The MAX31856 uses SPI, so we will need at least 10 spare GPIO pins for C/S (or multiplexer), but is available as a breakout board, and can handle almost any kind of thermocouple without additional computation. We picked the off-the-shelf breakout board rather than fully custom solution intially, since it lets us quickly order replacements if we need them. If the shock proofing design works, we could design a breakout that includes both the temperature sensor and the shock proofing circuitry.

Having decided on a temperature sensor, we needed a microprocessor board capable of interfacing with 10 copies of it, and here the 

We decided on using an [Adalogger M0](https://www.adafruit.com/product/2796), since it is very affordable ($20) and has enough spare pins to measure all the temperatures without multiplexing. It already includes a microSD reader/writer for logging, and connections for both USB and battery power in case being plugged into the wall is deemed a risk. 

As for the display, we picked the cheapest display FeatherWing, the [128x32 OLED FeatherWing](https://www.adafruit.com/product/2900), which is very small but can fit 4 lines of writing, more than enough for our needs for now. In the future we can upgrade to any other display that can be run over I2C if we want a bigger screen, or touch functionality, etc, etc.



<p align="center">
  <img src="{{site.baseurl}}/images/T_breakout/T_breakout_Fritzing_bb.png" alt="Fritzing Diagram" />
  <p align="center"> *Preliminary Pin Usage Diagram* <p align="center">
</p>
