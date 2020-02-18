# background
The HP-18 is an amateur home-built pure glider, with the following specifications;

<img src="./resources/1529px-Wiki_HP-18_3view.gif" alt="3-View" width="800"/>

<img src="./resources/hp18-1.jpg" alt="HP-18" width="800"/>

Crew: One pilot</br>
Length: 23 ft 2.4 in (7.07 m)</br>
Wingspan: 49 ft 2 in (15.00 m)</br>
Wing area: 113 ft2 (10.5 m2)</br>
Aspect ratio: 21.4</br>
Empty weight: 470 lb (213 kg)</br>
Gross weight: 970 lb (446 kg)</br>

# plan
So, here's a plan... (not entirely certain yet, but I'm liking this more and more)

# first
First, get the HP-18 airworthy.. 
* get a brake master cylinder and rig it.
* cleanup the wing corrosion 
* [install blue fly pressure sensors](https://blueflyvario.blogspot.com/2017/) I have experiance with this system, it works well. 
* Finish the "un-panel" 
   * Wire power to tablet mount
   * Find a tablet
   * Setup XC-Soar
   * Configure preasure gauges
* Conditional Inspection

Then fly it once or twice.  Now for the real work!

# burn the boats

<img src="./resources/25kw-motor.jpg" alt="HP-18 Layout"/>

I already have a 25kw peak motor / controller designed for up to 100v.

## modifications

<img src="./resources/hp-18-nose-motor.jpg" alt="HP-18 Layout"/>
<img src="./resources/hp-18-profile-motor.jpg" alt="HP-18 Layout"/>

I'm going to chop off the nose (includes the nose tow hook). I may find a place to mount the hook later, but for now... gone. 

The best place for the battery modules is inside the wing ahead of the spar. Hollow the wing cavity using a hot knife and build a cradle to support it.  Positioning the battery well inside the wing would do better for flight loading, but nearer the root is easiest logistically and lowers the rolling moment of inertia. 

To mount the wings, I'll need a jack for the 250 lbs!  

## batteries

Here are the specs on the Tesla Model 3 battery module 23S46P (scoured the web, not offical)

* 82.8v nom
* 11.7 kwh
* 191 lbs
* 67.5" x 11.5" x 3.5" 
* $2250+shipping each

The Tesla modules come with a built in BMS, but I will need some way to charge it.  The batteries will be hooked in parallel, so I can charge them individually.  At this current draw (250A) these batteries will get thermal stress, so I will either have to cool or de-rate.  6k is 70A, that's very low thermal stress.  We'll see!

## BMS

The Model 3 battery modules incorporate a "BMS", it's really just a board with some well known/documented chips that very accurately measure voltage and control ballancing resistors;

Linear LTC6804 or (later models) Linear LTC681x

They communicate over a well documented(by Linear) bus called isoSPI.

[Follow this blog for more details](https://cabrioev.blogspot.com/)

It is important to note that the 6804 will self-balance all 12-cells passively.  But with 23 cells total you need two 6804's.  Something has to actively tell each 6804 that it needs to engage the MOSFET balancing gates so each sub-pack doesn't "drift" high/low.

The LTC6820 is a transceiver for the isoSPI bus.  There dev kits and at least one [dev module on ebay here](https://www.ebay.com/itm/Maleetronic-isoSPI-Module/254173328261?hash=item3b2de93385:g:xpIAAOSwJrpclM92)

The Arduino library used to control the [LTC6804 is here](https://www.analog.com/en/search.html?q=LTSketchbook)

What is needed is a "state of charge controller" with a 6820 isoSPI transciever to transmit each battery's status and actively control the sub-packs and be the master-enable on charging / drain.

Given this is a well known protocol and the interfaces are all well known; either an open source or commercial supplier should be available shortly (if not already).

## weight ballance and performance
So all in, empty should go something like (570 + 400 + 30) = 1000 lbs.  Typical weight with me will be 1160. As the weight is in the wings, CG and flight loads are minimally impacted. Stall speed would be 10-15% higher.  For now I'll use a fixed two-blade prop, longest length that the gear will allow (54-60" seems about right).  Eventually I may design a folding system with the nose I cut off.

## details

<img src="./resources/HP-18-Layout.png" alt="HP-18 Layout"/>

To summarize the conversion;

* nose
  * chop off the nose
  * fabricate motor mounts
  * mount motor
  * find a prop
  * build a nose cone
* hv systems
  * mount the controller
  * mount battery fuses
  * mount master on/off switch
  * mount DC-DC converter
  * wire charge connector to fuses
  * wire the controller to master
  * wire master to fuses
  * wire battery to fuses
  * wire DC-DC convert to master 
  * wire DC-DC convert low voltage output to existing electrical system
  * carve wing cavity for batteries
* build a battery system monitor, with bluetooth that can connect to XCSoar to output;
  * battery Voltage
  * current
  * state of charge
  * charge remaining
  * left/right battery temps
  * motor temp
  * controller temp
  * master alarm
* throttle
  * build a throttle
  * build a throttle position sensor that outputs Servo PWM for controller
  * wire throttle sensor to motor control
* open issues
  * How to charge/monitor these batteries?
  * How to monitor system health in-flight?

# phase 3

Flexible solar panels can be found that produce 210w/m^2.  If you could cover the entire 10.5m^2 That's 2.2kw, not likely, but 1.8kw is.  So for every hour you soar you get back 18 minutes of cruise. The easiest way to think of it is that the panels add a net-effective 30mph "boost" to cruise.  More hours soaring, more total range.

# missions
23.4kwh of battery is a TON!  A cross country mission profile could look like... 
* full power for 2 minutes take-off
* cruise-climb to 8,000' at 400 fpm on 15kw for 20 minutes
* With 20 kwh remaining, cruise for 2.5 hrs at 6kw

Figure 90kts cruise, total distance 300nm.  

But this configuration lends itself to a new kind of mission as well...  Take off, cruise heading wherever the conditions are best locally that day, soar as you go.  End of the day power up and head home.  In theory, you could use 3.5hrs of power over 4-8hrs of power/gliding, using streets, one could several hundreds of miles in a day, find a charger and head home the next day.

# competition
This opens a whole new kind of avition competition... How far can you get in a day in an electric aircraft?  You'd have to optimize for atmospheric thermal efficiency (like a soaring competition), solar recharge rate (don't fly under the clouds) and charge management.  It would be very interesting to see where this could go.  
