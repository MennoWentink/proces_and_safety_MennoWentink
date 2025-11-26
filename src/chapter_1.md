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
title State Machine: traveling to school
hide empty description
[*] --> STATE_traveling_from_home_to_trainstation
state STATE_STUDYING {
 STATE_STUDYING : // Student = working //
 STATE_STUDYING : TimerStudy(IN := TRUE);
}
 
' koffie = Time over OR Tired
STATE_STUDYING --> STATE_ORDERING : [TimerStudy.Q OR bTired]
 
state STATE_ORDERING {
   ' Action: Write to GVL
   STATE_ORDERING : GVL.bRequestCoffee := TRUE;
}
 
STATE_ORDERING --> STATE_WAITING : [Direct]
 
state STATE_WAITING {
   STATE_WAITING : // wacht op machine //
   STATE_WAITING : // nothing //
}
 
'Wait until GVL variable becomes TRUE
STATE_WAITING --> STATE_DRINKING : [GVL.bCoffeeReady = TRUE]
 
state STATE_DRINKING {
   ' Als koffie -> reset request
   STATE_DRINKING : GVL.bRequestCoffee := FALSE;
   STATE_DRINKING : bEnjoying := TRUE;
}
 
STATE_DRINKING --> STATE_STUDYING : [bCupEmpty = TRUE]
@enduml
```