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

# Buttons...

_Power_ This is a dual pole momentary switch, the first pole energizes a the essential-bus master latch relay.  This is the traditional master relay.   
