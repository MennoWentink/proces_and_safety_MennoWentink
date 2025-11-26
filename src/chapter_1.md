# Chapter 1

In this assignment I simulate my journey going to school

```plantuml
@startuml state diagram going to school

start
:leave home and get in my car and drive to train station;
:parked the car. Walking to the station;
:Aarrived at the station;
:train ride;
:Train arrived. Walking to school;
:arrived at school;
stop

to do:
One Sequence diagram depicting the communication between the tasks
One Sequence diagram showing the calling of the function by the task.
@enduml
```

The train ride is programmed in a function this will be called from the main program, but needed a different state diagram.

```plantuml
@startuml state diagram train towards enschede

start
:op het station?;
:train leaves station;
:train arrives at station;
stop

@enduml
```

```plantuml
@startuml
title Travel from Home to School

actor PLC
participant MAIN
participant GVL
participant TrainFB as FB_TrainAtoB

PLC -> MAIN: PLC startup
MAIN -> GVL: Step = 0

' Auto part
MAIN -> GVL: StartDrive = true
MAIN -> MAIN: Drive timer running
MAIN -> GVL: StartDrive = false
MAIN -> GVL: Step = 1

' Walk to station
MAIN -> GVL: StartWalk1 = true
MAIN -> MAIN: Walk1 timer running
MAIN -> GVL: StartWalk1 = false
MAIN -> GVL: Step = 2

' Train ride
MAIN -> TrainFB: Start = true
TrainFB -> TrainFB: Train timer running
TrainFB -> MAIN: Arrived = true
MAIN -> GVL: Step = 3

' Walk to school
MAIN -> GVL: StartWalk2 = true
MAIN -> MAIN: Walk2 timer running
MAIN -> GVL: StartWalk2 = false
MAIN -> GVL: Step = 4

MAIN -> GVL: Status = "Arrived at school"

@enduml
```