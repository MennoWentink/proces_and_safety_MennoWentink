# Chapter 1

In this assignment I simulate my journey going to school from home.
below is the flowchart from the complete program

```plantuml
@startuml
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

for the first car ride from my home to the train station, i have opted to use a function block. this will get called and simulate the car ride from my home to the train station.


The flowchart for the train ride is seperate, because this is a seperate program.

```plantuml
@startuml
start
:op het station?;
:train leaves station;
:train arrives at station;
stop

@enduml
```

The train ride is programmed in a different program compared to the main program and is always running in the back until it reads the message from the Global Variable List that it has to do his part. at that point it will complete it's own case structure and communicate it back by usting the Global Variable List


The diagram below shows the calling of the program and the function.

```plantuml
@startuml
title PLC Task Calling MAIN and Function Block

actor Task as "PLC Task"
participant MAIN as "MAIN Program"
participant FB_Train as "Train program"

Task -> MAIN: Cyclic call

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