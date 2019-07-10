# About

The primary goal of the Phase 1 Airframe development is to focus on prooving out the concepts of the project.  The attributes of a test-bed aircraft is that it be simple yet mechanically robust (space for equipment), seats two for pilot and test engineer, aero-dynamically stable, easy to fly and experimental.

# Candidate airframes;

- Vans RV-9A
![RV9](resources/rv9.jpg)
- Sonex 
![Sonex](resources/sonex.jpg)
- Zenith CH 601
![CH601](resources/ch601.jpg)
- Zenith CH 701
![CH701](resources/ch701.jpg)
- Kitfox
![Kitfox](resources/kitfox.jpg)

We will purchase an actively flying airframe, from the list above, in a known airworthy condition.

# Critical Systems

- Powerplant
- Fuel
- Electrical
- Flight control

# Powerplant

Goals; 
1. Redunancy
1. Safe flight failure mode
1. Simple
1. Meeting mission goals

Proposals;
- Traditional aircraft engine(s)
- Hybrid ICE + Electric motor
- Electric Motors + ICE generator
- All Electric

## Traditional light twin 
Pros - Simple, well known
Cons - Flying single engine is tricky, additional licensing

## Hybrid ICE + Electric Motor
![Corvair](resources/corvair.jpg)
Pros - Cheapest, easy to fly (no special ratings), lightweight, can replace starter/alternator, immediate and simple failure mode
Cons - Propellor and crankshaft are a common failure mode

## Electric Motors + ICE Generator 
![Freepiston Geneator](resources/freepiston_genset.jpg)

Pros - Ultra-reliable, can utilize purpose build "genset" with high efficiency.
Cons - Heavy (motors, props, generator and engine), twin engine requires additional rating

## Co-axial All electric 
Pros - Ultra reliable, simplest possible solution
Cons - Very limitted range (limitted mission), Some propellor/axle common mode failures.

## Summary

If weight and money wasn't a thing... A coaxial dual-electric with removable ICE generator for cross countries likely meets the objectives best.

Since it needs to fly and airplanes fly on money... The hybrid ICE + Electric motor option is a good light/cheap/simple compramise.

# Fuel

Fuel system are best which have the following traits;

- Simple
- Gravity fed

For this reason high-wings are preferred.  If a low wings is however selected, a single 5-15g gravity fed header tank will be used and fed by low-pressure electric pumps to each wing tank.   The fuel pump will be controlled and monitored by fuel management system.  Regardless of configuration all tanks will have a capacitive sensor and a seperate low-level indicator that provide fuel level information to the dedicated fuel management system.

# Electrical

_Dual redundant electrical systems_  There are many great source for redundant electrica systems.  I will defer to those.  They are not hard to build or understand, they do require some additional considerations.

_Switchless_ The entire electrical system will be actuated by PCS-fuse-issolated and solid-state or mechanical relays controlled by the electrical management system.  There will only be one bat switch in the cockpit labelled "Master/Essential/Off".  All other switching will be fuse issolated and actuated by the electrical management system.  This includes;

- Charge source(s) disable for DC-DC converter
- Flight control master
- Avionics master
- Lighting
- Accessories

_High / Low Voltage_ The electric motors will run at high voltage. That system will be recharged by a generator or the ICE engine.  A DC-DC converter will be used to feed the low voltage systems in the cockpit.  This is similar to how electric and hybrid vehicles generator low voltage system power.

# Flight control

The flight control system will initially be "human redundant".  This isn't ideal, but a truelly fail redundant fly-by-wire system is likely out of scope and perhaps recless to test without better background.  When _EVERYTYING_ else failes, I really wouldn't feel comfortable unless I knew I could hand-fly the test aircraft to a field. 
