# Chapter 1

In this assignment I simulate my journey going to school from home. This is an assignment for proces and safety.

The assignment must contain:

    2 tasks running independetly(main and train program)

    the program must include 1 function(carride funciton)

    a global variable list where 2 task read and write variables in. 

For the documentation it was instructed to show:

    1 state diagram for each task

    1 diagram for showing the communication within the program

    1 sequence diagram for showing the calling of the function



below is the flowchart for the complete program this gives an overview for the reader how my journey to school is.

```plantuml
@startuml

start
:leave home and get in my car and drive to train station;
:parked the car. Walking to the station;
:arrived at the station;
:train ride;
:train arrived. Walking to school;
:arrived at school;
stop

@enduml
```


The statemachine for the main program is displayed below. 
```plantuml
@startuml
title State Machine: gvl.Step

[*] --> Step0

state "Step 0: Driving to Station" as Step0
Step0 : entry / gvl.bStartDrive := TRUE
Step0 : do / car(bStart, T#12S)

Step0 --> Step5 : car.bcararrived == TRUE
note on link
  Reset bStartDrive
  Reset Timer
end note

state "Step 5: Walking to Platform" as Step5
Step5 : entry / gvl.bStartWalk1 := TRUE
Step5 : do / tWalkHomeToStation(IN)

Step5 --> Step10 : tWalkHomeToStation.Q == TRUE
note on link
  Reset bStartWalk1
end note

state "Step 10: Train Ride" as Step10
Step10 : entry / gvl.bStartTrain := TRUE

Step10 --> Step20 : gvl.bArrived == TRUE
note on link
  Reset bStartTrain
end note

state "Step 20: Walking to School" as Step20
Step20 : entry / gvl.bStartWalk2 := TRUE
Step20 : do / tWalkStationToSchool(IN)

Step20 --> Step30 : tWalkStationToSchool.Q == TRUE
note on link
  Reset bStartWalk2
end note

state "Step 30: Arrived at School" as Step30
Step30 : entry / gvl.bArrivedAtSchool := TRUE

Step30 --> [*]
@enduml
```

The train ride is programmed in a different program compared to the main program and is always running in the back until it reads the message from the Global Variable List that it has to do his part. at that point it will complete it's own case structure and communicate it back by usting the Global Variable List. below is the corresponding state machine for it.

```plantuml
@startuml
title State Machine: gvl.train

[*] --> Step0

state "Step 0: IDLE" as Step0
state "Step 5: DRIVING" as Step5

Step0 --> Step5 : gvl.bStartTrain = TRUE \nAND NOT InternalStart
note on link
  Sets InternalStart = TRUE
  Sets bArrived = FALSE
end note

Step5 --> Step0 : Timer.Q = TRUE
note on link
  Sets bArrived = TRUE
  Sets InternalStart = FALSE
  Resets Timer
end note

footer TwinCAT Train Logic
@enduml
```

Below is the schematic that explains the communication between the Global Variable List, the main program, the train program and the function block.
it also shows the flow of information within the program.
```plantuml
@startuml
title Travel from Home to School

actor PLC
participant MAIN
participant GVL
participant Trainprogram
participant autoFB

PLC -> MAIN : plc startup
activate MAIN

== Step 0 ==
MAIN -> GVL : step = 0
MAIN -> autoFB : StartDrive = true
autoFB -> autoFB : drive timer running
autoFB -> MAIN : cararrived = true

== Step 5 ==
MAIN -> GVL : Step = 5
MAIN -> GVL : startwalk1 = true
MAIN -> MAIN : walk1 timer running
MAIN -> GVL : walk arrived = true

== Step 10 ==
MAIN -> GVL : step = 10
MAIN -> GVL : trainstart = true
GVL -> Trainprogram : trainstart = true
Trainprogram -> Trainprogram : train timer running
Trainprogram -> GVL : trainarrived = true
GVL -> MAIN : trainarrived = true

== Step 20 ==
MAIN -> GVL : step = 20
MAIN -> GVL : startwalk2 = true
MAIN -> MAIN : walk2 timer running
MAIN -> GVL : startwalk2 = false

== Step 30 ==
MAIN -> GVL : step = 30
MAIN -> GVL : Status = "arrived at school"

deactivate MAIN
@enduml
```

for the first car ride from my home to the train station, i have opted to use a function block. this will get called and simulate the car ride from my home to the train station. below is the sequence diagram for the calling of the carride function

```plantuml
@startuml
header TwinCAT Sequence Diagram
title Call of the Function Block "car" (Step 0)

participant "MAIN (PRG)" as MAIN
participant "GVL" as GVL
participant "car (FB_Car)" as FB

activate MAIN
MAIN -> GVL : Step = 0
MAIN -> GVL : Schrijf gvl.bStartDrive := TRUE

hnote over MAIN, FB #FFF9C4: Aanroep van het Function Block

MAIN -> FB : car(bStart := TRUE, TravelTime := T#12S)
activate FB
FB -> FB : Update interne timer logica
FB --[#black]> MAIN : Output: bcararrived
deactivate FB

deactivate MAIN
@enduml
```
