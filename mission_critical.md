# Hardware

Many of the systems discussed actually imply a life-critical requirement.  If the flight computer fails for any reason, reboots and stop working... a student pilot could die.  Creating systems to this level of quality is extraordinarily difficult.  A bottom-up approach that attempts brutally simplistic redundancy is an oximoron.  But that is the stated goal. What is the simplest life-critical architecture?

## Sensors

All life-critical sensors are doubled.

## Actuators

All life-critical actuators are doubled

## Signal

All signals generated from life-critical sensors or actuators are triple redundent and vote.

# Software

The software approach for life-critical systems should compliment but not neccissarily mimic the hardware approach.  The software is going to become exceedingly complex... there's a falicy that "fault tolerant" code is safer code.  Unless foundational pieces are put in place to ensure that fault tolerance, this assumes a false sense of security. 

## Failed Appraoches

1. For example... if we mandate error handling and unit tests for every code path... sure, this sounds great, but it's not a cure-all.  Given wildly varied inputs may cause 'other than tested' excecution branches and unintended behaviors that lead to failure.   This approach is simply but inappropriate for this effort. 

1. For example... we mandate every possible input this system could ever encounter is tested.  That's great, but "every possible" is actually infinite (or near infinite) in many cases for flight systems.  Given the impossibility, a "finite" alternative is actualy done and that finite alternative regardless of how complex isn't "all".

## What about... Approaches

1. What if the system couldn't fail... there is no such thing as a failure.  example, the Apollo Guidance Computer (AGC).  It can be in a fault and "programs" can hang/fail, but a hardware watchdog restarts them and resumes "real-time enough".  Now the AGC is a very simple computer by any means (after 1970, it was off the charts for the 60's).  But this approach is interesting and requires further study.

1.  [tbd] - research additional approaches to life-critical.  So far research sucks.


## Operating System

This project likely will mix/match operating system approaches, so I want to outline them for clarity. There are really three kinds of ways software can run on a computing core;

- Dedicated purpose - When the power comes on... your program is loaded from flash or ROM into a well-known location in RAM and the CPU begins execution at the start.  The programmer have full control of any instruction and interupts of your process.

- Real-Time - A small set of programs shares the CPU with a priority.  You can pin some programs to a CPU, you have full control of that CPU and generally interupts, but other programs on other CPUs share memory and interupts as well.  It allows good timing control and some side-processing.

- Multi-Tasking - The programer has not expection of what else may or may not be running nor any expectation of getting any CPU time or when their code will hit the CPU. For any time-critical event (like reading a serial input), these systems force interupts at lower (more real-time) levels.


