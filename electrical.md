# Electrical System from ground-up

So what would an electrical system look like if you wanted to start over?  

1. Should be on a PCB, not wired by hand
1. Should directly and correctly support dual battery/essential bus
1. Should integrate with the main flight computer via serial communication (CAN-bus or RS-485) 
1. Built-in over/under voltage
1. Doesn't need to switch everything, just what needs switching; lights.  Everything else is always on.
1. Must fuse every line
1. Turns itself off if you leave it on
1. Is failure resistent, simple failures don't shut everything down

# Controller

This lighting system uses a central controller.  This controller is engages for powering on, monitoring current loads, temperatures and energizing lighting circuits and de-energizing the master bus at shut-down.

The controller will receive GPS information from the flight control system via serial bus (CAN or RS-485).  This will include height above ground and time of day.  This information will be used to manage the light system.  The controller can also receive explicit requests to turn on/off any switched  circuit (Strobe, Landing, Taxi & Aux).  It will broadcast current usage, temperature and switch status for other systems to monitor or dislay.

# Button

There's only one physical input to the enire electrical power system.

This is a dual pole momentary switch, the first pole energizes an essential-bus master latch relay.  Because this specific relay is the most critcal to energy delivery to the essential bus, it uses a latching relay so once the circuit is energized it does not require energy to stay energized.  The non-essential bus relay is then energized off the essential bus using either a solid state or normal electro mechanical relay.

The second pole of the power switch is connected to the power management controller.  Hold the power button down for 10 seconds, then releasing, signals shutdown.  This instructs the power management controller to de-energize the essential latching relay to "off".  The power management controller will turn off the relay after a period of 5 minutes of engine off regardless.

# Lights

Based on how lights are used, they dont't require a switch per set of lights... Their use is predictable.  For example;

- Nav - Always on
- Strobe - Default on, unless selected off
- Taxi - On at night
- Landing - On at night bellow 1000', optionally can operates as Taxi as well 

The master power controller will use the altitude information sent from the flight control computer to determine the above logic.  It will also 
