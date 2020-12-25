# Overview

Reverse engineering of the MicroAir T2000SFL Mode-C Transponder from the display header.  Everything in this is for my own purposes, if you decide to disassemble your device and repeate any of this, it is at your own risk.  You could easily damage it.

# Modes / Functions

## Squak Code
The display uses a "Active" transponder code and user input below.  The active and input swap with a flip-flop key

## Modes
- Standby
- On (Mode-A)
- Alt (Mode-C)

## Other

Id - Ident

# Wiring

The display header has four wires

1 - Red +5v
2 - Black Ground (chasis)
3 - Green Tx
4 - White Rx

# Signals

Signals where first run through a DSO, voltages where 0-5v.  It apears to hover at hi more than lo, so I suspect it's hi-idle, low-on.

Pin 3/4 are UARTS they appear to have the following configuration.  I tried many permutations of baud, stop, parity and idle, this gave the best result;

Baud Rate: 38400
Bits&Parity: 8,None
Stop Bits: 1

When you use this configuration, you will get an output which roughly matches this
``0x24,0x4D,0xA1,0x30,0x30,0x30,0x30,0x30,0x53,0x49,0x30,0x34,0x33,0x80,0x3D,0x35,0x0D,``


# Message Content

## Preamble
``80 80 80`` Appear to be a pre-amble
The next 4 bytes ``80 80 80 80`` are only present in Standby mode, and are not present in full mode

The content does not start until you recieve a 0xFF. 

* NOTE ALL BYTE OFFSETS ARE RELATIVE TO message start, 0xFF

## Squak Code

Starting at position 4-8 are the transmitting code as ascii numbers 0x30 through 0x39

## Mode

The mode is encoded in the 6th position and it is the asci leters;

S - Standby
A - Mode-A
C - Mode-C

## Ident

Ident is encoded at the 7th position, it stays on for 10 seconds

I - Non-Ident
S - Identing

## Check Sum

The final two bytes appear to be a checksum.  The exact algorithm I'm trying to work out.  It appears to be a no-carry over sum by digits.

The final byte is a newline, which helps it to display well on a terminal

