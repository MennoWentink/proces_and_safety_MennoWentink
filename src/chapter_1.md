# Chapter 1

In this assignment I simulate my journey going to school from home.
below is the flowchart for the complete program

![flowchart](https://kroki.io/plantuml/svg/eNpdj0sOwzAIBfc-BSfoAdJNbtGtUUCxFdtYmFbq7es4_SjdwXvDSHjva8Ji95zc3Ax1TGNwU2J8MATJDFgIVjaIBfITFtSRkMYOmIAp9qafWZRydVNF3ZjAAu_sBW6YtljWgfbsB6LuCgK0v-IwaiT-Lm_2ZGtLEEln0SdrJtW5mQvtP3nvX1hOU7Y=)

for the first car ride from my home to the train station, i have opted to use a function block. this will get called and simulate the car ride from my home to the train station.


The flowchart for the train ride is seperate, because this is running in a seperate program.

![flowchart](https://kroki.io/plantuml/svg/eNpFjEEKgDAMBO95Rd9RD_YpCRiwUNOSrr5fW1BvszOwzNyKGM6jUOoQnzSBYm1hV4RnIVdbF4pwyRaKyqX99Z8W9zy84E8dtREltW38MjPdYbkouA==)

The train ride is programmed in a different program compared to the main program and is always running in the back until it reads from the Global Variable List that it has to do his part. at that point it will complete it's own case structure and communicate it back by usting the Global Variable List


Below is the schematic that explains the communication between the Global Variable List, the main program, the train program and the function block.
it also shows the flow of information within the program.

![Flowchart](https://kroki.io/plantuml/svg/eNp9k81OwzAQhO9-ilUvnJDaIC6VQC0gfqSCkIrgGitxi4VjW9tNeX3Wdgq1FXpLdmYnnydJXdfeSEt9Z8RiRxLjFWkyCt5Q7pWBDboOHl2ngBysm0_njBCyIYfwuroVnnd0oz2HwPPy6SUbPLyvsnuO1Naj26LsMkH25O5vhOBEOL-OQXPwpoHE5EWYBIUT5zxUHq5gKsQZLHkTQtSvJWXNYR1W71DvFXsJeyWScuxpo0y6UwjYW6vt9siVMBqJEoOvPeRkMOsEcxlgPqT5CjUxNWlnS2rm-WbHrMxJz0lSzpIFBAOcQhl6mcViYteAui1MFOaR5ZDB46AevxwY82WGYmHwF_jlxh9AcYwBIYKOO8YOWk2z0tO3Od559X_n1anOs4CNNLtxkgsmKb4KSf2OlcnhHJIGwokQC2Xb8KPVdf0DB1ocyA==)
