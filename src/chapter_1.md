# Chapter 1

In this assignment I simulate my journey going to school from home.
below is the flowchart from the complete program

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

@enduml
```

The flowchart for the train ride is seperate, because this is a seperate function.

```plantuml
@startuml state diagram train towards enschede

start
:op het station?;
:train leaves station;
:train arrives at station;
stop

@enduml
```

The train ride is programmed in a function this will be called from the main program.
The diagram below shows the calling of the program and the function.

```plantuml
@startuml
title PLC Task Calling MAIN and Function Block

actor Task as "PLC Task"
participant MAIN as "MAIN Program"
participant FB_Train as "Train Function Block"

Task -> MAIN: Cyclic call (every PLC cycle)

MAIN -> MAIN: Execute Step logic\n(timers, states)
MAIN -> FB_Train: TrainFB(Start, TravelTime)

FB_Train -> FB_Train: TON timer logic
FB_Train --> MAIN: Arrived status returned

MAIN -> MAIN: Update Step based on Arrived

@enduml
```
Below is the schematic that explains the communication between the Global Variable List, the main program and the function block.
it also shows the flow of information within the program.
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