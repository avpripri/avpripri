# Aviation Primary Principals

_Disrupting small vehicle air travel; making it safer, easier, and more affordable_

This project sets to make an order-of-magnitude improvement in small aircraft safety.  A first principal human re-factoring of the flight experience, positively disrupting general aviation and agnostic of aircraft design. Secondary goals include dramatically lowering the bar for learning and operating small aircraft, including large, mission oriented UAVs. 

![backflip](resources/emersive%20vision.jpg)

## New update...

The backflip proof of technology sub-project is complete and has been flight proven in my glider. I've started working on the second version.  This version works on a much more powerful, capable redundant core board, called Pressure, Attitude, Sensors, and Switching (PASS).  The overall design took some inspiration from the human brain, set up in a left/right configuration to facilitate redundancy.  Down the center is a 100A, 10-channel (10A/ch) dual-bus solid-state MOSFET/PolyFuse electrical system, each side/half also has 17 channels(34 total) of installer-configurable sensor I/O for engine/aircraft sensors.  Dual pitot and static pressure sensors and dual AHRS are also hard wired on the board.  Each half/side has a small 32-bit microcontroller that communicates with each other and connected peripherals via dual/dedicated CAN-bus controller.  Each microprocessor communicates to its own dedicated embedded display system, which is where the real "smarts" of the whole thing live. 

The first-draft board was fabricated and tested, many issue where found and resolved.  The next developer rev of the board is in fabrication as of 1/8.  I added 4 100a current sensors, this gives each bus current sensing on the battery supply/draw and the souce (alternator) current supply.  I've also added built in CAN-bus termintor jumpers and re-aligned the GPIO so they support the maximum analog input chanels.  There are 20 total, but up to 6 ares used internally, 2 are hard-wired to the bus-volt sensing.  The 4 current sensors are pinned to the DB-25 connector, so they can be used externally, if not allocated internally.

I have started working on the core systems which will make up this huge project.  It's called "BackFlip".  It has two projects

## Backflip 

![backflip](https://github.com/avpripri/avpripri/blob/master/backflip.jpg)

[BackFlip PFD](https://github.com/avpripri/BackFlip) - A better primary flight display

[BackFlip IMU](https://github.com/avpripri/RTIMULib2) - An Android-ized re-port of the RTIMULib2 for STM32 powered quad controllers 

## Yesterday and Today

Aviation has a varied safety history.  Through rigorous controls, learning, and testing large aircraft have become very very safe.  Too few of these hard-lessons-learned have trickled down to small aircraft. Furthermore, a malaise, "good enough" attitude is the norm.  But if you dig deeper are 1000x more accidents per hour "good"?  Factors like, training, cost, and complexity have been to blame.  Yet it's these light aircraft where all pilots are made and still the safety of any light aircraft is pitiful.

Here is the summary of the 27th 2017-2018 Nall Report;

_Other or unknown 10.4% - 101 Total_ - So, if we're honest there's not much anyone can do about these, at some level, aviation has risks, we should acknowledge we can't resolve all problems, but maybe some of these "unknown" accidents might not have happened if the airplane hadn't been in the wrong place at the wrong time. 

_Mechanical  15.7% - 152 Total_ - Many mechanical accidents are avoidable with purposely build and tested 100% redundancy at all levels.

_Pilot-related  73.8% - 714 Total_ - This is entirely unacceptable and avoidable.  If you take away nothing from the Nall report, every pilot should recognize they're the weakest and most important link in aviation safety.  This project attempts to fix that.

The Nall report has been trending safer for decades... many in the industry site Electronic cockpits and ballistic parachutes, while I agree they are good, I do not think they are enough.  There's no excuse for fuel starvation or CFIT 100+ years after kitty hawk.

## First Principal

To push through incremental and become disruptive, we have to disassemble the core aviation "Whys".  Why are people flying, why are people learning to fly.

From these tenants, we rebuild, ground-up, from new assumptions and new decisions without old paradigms and solutions.  

## Priorities

These priorities attempt to directly address that general aviation is not at all generally accessible; 

_Safety_ - This project is founded on the principle that an order of magnitude improvement in overall light aircraft aviation safety is achievable.  That's 97 accidents where we have 967 today.  But to do that it requires a "first principle" approach.  Strip down the aircraft, what it does how it functions, and what the pilot's role is in and out of the cockpit. 

_Easy_ - Any ten-year-old can fly a plane on a nice day, it's not at all hard... It's very hard to fly a plane safely in all conditions at all times.  This project proposes an "active-active" stability enhancement and envelope-protection flight control system.  This system relaxes and virtually disappears in "safe" flight regimes and seamlessly becomes more aggressive in high-risk environments.   The flight system will also feature "designed-in" skills-building flight exercises to "flattening" the learning curve and enhance "hands-on" in-flight learning and enabling pilots to gain skills most effectively at their own pace in an objective, safe environment.

_Affordable_ - Pilots that can't afford to fly often aren't flying at their potential.  Many of the other goals of this project have secondary impacts on the bottom line... IE an easier-to-fly and the safer plane needs cheaper insurance.  The direct operating cost of electric aircraft is in single dollars per hour vs. hundred(s) for gasoline.  If it was $10/hr or $100 a day to rent an aircraft, I think we'd see entirely different use cases, even Uber-like commuter scenarios, and metropolitan transport/commuter cases.

## A story of a different kind of flying experience...

It's hard to imagine what a different kind of flying experience is like, so a story helps to frame the idea.

You come out to the airfield to see your beautiful airplane again.  You give it one cursory walk around only looking for any gross damage then hop in.  That's your entire pre-flight.  Push on both brakes for a moment and the displays come alive as diagnostics begin.  It will run a complete check on all electrical, then oil-levels, tire pressure, control system, brakes, fuel quantity, and using strain gauges in the wheels, weight, and balance.

With diagnostics complete, the system asks.

"Weight is 1237 pounds, 224 pounds under gross, balance is 23% aft of forward limit, you have no less than 2hrs, and 23 minutes of fuel onboard.  Winds are eight knots at two-three-zero, temperature 23 Celcius dew point 20, sky clear bellow one-zero-thousand, pressure reports three-zero-zero-three and set. "

"What is your mission today?"

You pull your headset on and look around the cockpit. It's very clean, just two very large displays, vents, a stick, and a throttle.  The core of the display bears a resemblance to the glass panel EFIS you might have seen in the first generation, but there are subtle differences.  It's hard to put your finger on it, but it looks less mechanical.  There are no pixilated nameless tapes for dozens of inputs you couldn't absorb before anyway.  It's just what you care about right now.

You take the smooth simplicity of the displays in as you press the "Push to Listen" (PTL) button and state, "Northeast practice area, 60 minutes"

The display fades to a situation view and zooms to where you are on the ramp, and paints a magenta line to the active runway from your location.  At the same time, the second window in your primary display pops up with a 3D rendering of your path from your location with the same magenta line, and in the corner a "red-ish" area where the taxiway intersects another runway 13-31 hints at a high conflict intersection. The feeling is more automobile navigation in tone and context than your typical airport diagram slapped on a sectional chart. Seamlessly it highlights and flashes momentarily the common traffic advisory frequency is set to 122.8 and prompts;

"The active runway is 24, the most direct routing is alpha straight ahead and to your left"

Easing the throttle forward, the strobes turn on and a few moments later the prop starts to spin at a whisper than a whir as the wheels ease forward and turn towards Alpha taxiway.  En-route you hear the generator start-up, the flight controls go to full stops and you notice the brakes actuate under a heavier propeller load.  The monitor confirms it's the pre-flight checks are being performed while you taxi. As you approach the intersecting runway,

"Approaching high conflict area, alpha, and runway one-three three-one"

The gentle reminder to look around and check, and clear, so you proceed.  All calms as you turn down the long taxiway and the plane announces, "All systems are operating normally. There is no observed traffic on TCAS.  Winds are 5 knots at 220, 20 degrees off the left with a cross-wind component of 2 knots, density altitude is 812 feet, the sky is clear.  Our direction of flight is a right turn north-east 030 VFR departing runway 24 from Alpha"

With a clear approach, you once again ease the throttle forward as the display turns the mission phase prominently as "Ready for take-off" in green, as you slide into position on the runway, the annunciator says;

"Ready for take-off, in case of emergency on the runway, apply brakes and come to a stop.  If air born and room to land, land on the runway, below 600 land in the field to the left.  Above 600 a turnaround is possible."

You ease the throttle to full and the prop and generator roar to full power straining against the brakes with the command to "Hold Brakes" blinking yellow for eight seconds, long enough for one last system check, then "Release" goes green.  The brakes release and you are pulled forward hurtling down the runway.

"Airspeed 30...40..45... all good"

You speed up briskly down the runway and ease back as the airplane finally announces "rotate" and the nose of the plane rises above the horizon... wheels off.

"Wheels off 12:32... all good... 50 feet, straight-ahead"

The field to the left is nice and wide open a good spot to land if one had to.  The monitor shows it painted in faint translucent green in the airport map and the words The tall trees and hill to the right are in red and "Warning - Terrain" is displayed nearby.

"all good two hundred feet, straight-ahead"

"all good four hundred feet, straight ahead."

"all good six hundred feet, turn-back available."

The terrain warning clears

"Turn right to a zero-four-zero heading."

You can't tell if you turned or the plane started, but either way, your heading is turning clockwise in a gentle bank to the right.

"five-hundred feet to level at two-thousand-five-hundred."

The wings level at 040 a moment later the nose pitches down

"Level two-thousand-five-hundred"

You look around and enjoy the view as you head out to the practice area, you can feel the plane giving gentle feedback.  You know you are in command, but it's doing the leveling. If you try to turn it, the resistance is imperceptible, like feathers but it's trying to bring the plane back to the magenta line it's obediently following. As you vacate the airport area, the departure frequency is tuned into the backchannel and low-volume monitoring is turned on.

"Arriving at the northeast practice area, what maneuvers do you want to practice?"

"Stalls"

"OK, we'll need to clear the area first, start by doing a pair of 90 degree turns in either direction"

You pull the stick left and the plane just follows along, it's letting you do your maneuvers.  As you level out it says...

"Ok, begin your stall by powering back, then apply progressive aft stick to stay level"

You pull the throttle back and the propellers whirr gets a little lighter, you pull the elevator aft further.

.. as the speed starts to bleed off you look over and the flaps are deploying automatically as the airspeed decreases.  The plane interrupts with, "Recovery is immediate full power and pitch the nose over gently".  

The nose pops and the tail buffets as you hit the aft limit of the elevator travel.

"Recover"

But you're not very comfortable with stalls yet and you just freeze.  The airplane waits a moment and just before the nose cuts over...

"Release controls!" is commanded abruptly in a harsh demanding voice.

The airplane applies a rudder to stop the yaw rotation that's just barely started and coordinates the power and enough elevator to recover.  As the normal flight is restored, the flaps retract and the plane is stabilized. The plane announces, "Normal flight restored, you may resume flight inputs. What is the next maneuver you'd like to perform?"

You say... "I'm done, let's head home"

"Unicom frequency is already tuned in, you're 15 miles to the northeast, winds are 220 at 5, the pressure is three-zero-zero-three and set, the most appropriate runway is 24" 

You comply, but then... you fade off and something dims it's not good.

The airplane realizes you're not responsive and your pulse is erratic.  It asks you twice to state your landing attempt, but you're out cold.

The airplane states over the radio "N12345, declaring an emergency with an incapacitated pilot please have medical personnel ready and clear runway 24 for emergency landing" 

The airplane lands itself slows down and announces again...

"N12345, emergency declared taxing from runway 24 via Alpha autonomously please clear all runways and taxiways and have emergency personnel available"

The plane taxies to the ramp it started from, shuts down, and waits as the ambulance pulls into the spot.  The doors open and they rescue you from what could have been fatal in several ways.

## The pilot

FAR 91.3(a)
 The pilot in command of an aircraft is directly responsible for and is the final authority as to, the operation of that aircraft.

Given this responsibility, the aircraft systems must always provide the pilot with everything he needs to achieve this objective.

The pilot's role is to express the intent of each mission.  The system is empowered to execute on that intent as much as possible with the direct supervision of the pilot.  

## The aircraft

Every flight-critical system is mechanically and electrically redundant with automated/instantaneous failure modes.  This includes, but is not limited to;
- engine
- motor
- fuel
- flight system
- navigation
- display

## The brains; Flight Management System (FMS)

At the center is "the brains" or the flight management system.  This isn't artificial intelligence or a better autopilot.  It's an expert system programmed with common sense rules about flying.  Factoring in all critical aspects like;

- Systems
- Weather
- Attitude
- Fuel
- Flight Rules (airspace, minimums, clearances)
- Navigation
- Communication

It is taking in all of the above factors (and more) to assess risk which gives or takes away control from the pilot to ensure safety.

# Concerns

_Machines don't make machines safer, look at the 737 Max_  Flawed redundancy which doubles the failure modes are fatal.  IE, multi-engines that can't climb on one engine.  Any redundant system must be tested for partial and total failure modes.  No partial failure mode should cause additional failures or total loss of any one system.

_The more you take the pilot out of the loop, flying won't be fun_  If you have plenty of altitude in good weather, the flight control system will allow most abrupt maneuvers inside the safe flight envelope.  But as you get lower, slower, or into weather... you'll find progressively less and less control and more and more feedback as you deviate from the flight plan.

_What if the flight control system goes haywire and starts flying nuts?_  The flight control system will be the most redundant system with designed-in failure recovery and it will be very heavily tested.  The likelihood of this happening should be low, but it can and will happen.  The pilot still has direct physical control, you can still land the aircraft.  

_If everything is electric, what if that fails too?_  The electric system is designed for failure as well, but everything can fail. The electric motor controller will have its own independent and backed-up power supply from the high voltage and should continue to operate the electric motor.  If that should also be faulty, the airplane can still glide to a forced landing.

# Proof of concept vehicle

The project is going to convert a light homebuilt experimental aircraft for use as a test-bed for the overall concepts expressed on this page.  

![Conceptual Architecture](https://docs.google.com/drawings/d/e/2PACX-1vRf7XpgTQ-mGMANlDBKdWsu2V8Kd2P-1pKBFdryPZWSIR5R45uyv3sI4wjZxiTYhQlgd-wIdy3-WySN/pub?w=960&h=720)

## Phase 1

Acquire an airframe and develop the hardware. This includes 100% redundant;
- Power plant
- Fuel system
- Electrical system
- Flight control system

## Phase 2

Testing
- Built-in
- Ground
- Air

## Phase 3 

Expand and learn - Get this system out for others to build into their homebuilt projects and begin flying more safely.  Explore how this system can be used as a teaching platform for safer flying in general.
