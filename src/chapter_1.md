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


below is the flowchart for the complete program this gives an idea for the reader how my journey to school is.

![flowchart](https://kroki.io/plantuml/svg/eNpdj0sOwzAIBfc-BSfoAdJNbtGtUUCxFdtYmFbq7es4_SjdwXvDSHjva8Ji95zc3Ax1TGNwU2J8MATJDFgIVjaIBfITFtSRkMYOmIAp9qafWZRydVNF3ZjAAu_sBW6YtljWgfbsB6LuCgK0v-IwaiT-Lm_2ZGtLEEln0SdrJtW5mQvtP3nvX1hOU7Y=)


The statemachine for the main program is displayed below. 

![flowchart](https://kroki.io/plantuml/svg/eNqNlFFPwjAUhd_7K27wATGCW8lelmAgYqJGjbIZH4wPhV2gsbSkLRj-vW3ZpkNN2MOWrd8999zTZkNjmbablSBLZAVqyD-5vBrlcKc2WuIO7tWCz4jlViBkllmEBzZbcokpLLail1lcE9KGMc655OgECoQtauMYIVC6N-OrDAkPaPkCiFIYa77lcgFWBVmuZAuYAb8cNdgkhVcmPkr2STA7V3pVw0kDjp1yrhmXMOEF1lDclKRRQzObLZUSNUybcN_BI-3cYlEj_Yj4oTOf3XojLXk7e4du97K0T8IDUkBp9Q4uQlLTQPuxEdIB5JOX65orlINmTJ_uoXPIT2Kadcr1SjhxpIN6U3dje0cwKJWkcoaVBMHlBwGYoEELP1rW33K-Qk3cxoAv2VtN_rTqE4obVpPKali7USvMVbl5p7ePnZKp7MZ-st9k7_kY06H5gc3470j3-_3TZ_ydGfU1gR0dn1hQPGhOo39Doo3mNGqkVE7txg-nrM6Jfnvs10EdwMdHRQ_cBknj5TbGu2tX54VZMEG7XXHehTu-xF9Dp-L-BV8B-03W)

The train ride is programmed in a different program compared to the main program and is always running in the back until it reads the message from the Global Variable List that it has to do his part. at that point it will complete it's own case structure and communicate it back by usting the Global Variable List. below is the corresponding state machine for it.

![flowchart](https://kroki.io/plantuml/svg/eNptkUFLw0AQhe_zKx49Flq8eAkoDSaWQIyYrF60h20zpIvbiWzW-vfdJA2k4mXZnffmfQ9203nt_PfJ0pF1zQ7qx8hDrKCcNoK8bcyBvPGWUXntGU_6cDTCEZqzXfveRNQNyqLy_IWbCFmSpwvoDllt-Uq8jZCU2VtWbAc9ceZspCF6X-6wWt2PC9Sfw_OiY4Ttq77q2OsOqnxNPyQuEhTPCpl4dqLtYCFpA7EVWCOfBFTsu2vHZX_S9rELJK7D-DHOq5RYavQhRFOFqV3oosyJ3fplyvgPNgucc_52GGFAyV0vD8Ez9iZcw8_8AmbhhXw=)



Below is the schematic that explains the communication between the Global Variable List, the main program, the train program and the function block.
it also shows the flow of information within the program.

![Flowchart](https://kroki.io/plantuml/svg/eNp9k81OwzAQhO9-ilUvnJDaIC6VQC0gfqSCkIrgGitxi4VjW9tNeX3Wdgq1FXpLdmYnnydJXdfeSEt9Z8RiRxLjFWkyCt5Q7pWBDboOHl2ngBysm0_njBCyIYfwuroVnnd0oz2HwPPy6SUbPLyvsnuO1Naj26LsMkH25O5vhOBEOL-OQXPwpoHE5EWYBIUT5zxUHq5gKsQZLHkTQtSvJWXNYR1W71DvFXsJeyWScuxpo0y6UwjYW6vt9siVMBqJEoOvPeRkMOsEcxlgPqT5CjUxNWlnS2rm-WbHrMxJz0lSzpIFBAOcQhl6mcViYteAui1MFOaR5ZDB46AevxwY82WGYmHwF_jlxh9AcYwBIYKOO8YOWk2z0tO3Od559X_n1anOs4CNNLtxkgsmKb4KSf2OlcnhHJIGwokQC2Xb8KPVdf0DB1ocyA==)

for the first car ride from my home to the train station, i have opted to use a function block. this will get called and simulate the car ride from my home to the train station. below is the sequence diagram for the calling of the carride function

![flowchart](https://kroki.io/plantuml/svg/eNpdkltvwjAMhd_zK6zupUgwsT0iMXEbaNJuomWvk0kNzRaSLrjd35_bMm59aWMff8cn6mjPGLjcWZUTZhQg_TVuOk4hoZ-SnCaYGdwG3Ck2bAmmaC34DXBOMC-dZuMdTKzX3xBpDBHECVMB_Y5ShYCNNgU6huhl_PQK8fty0YkA91AfLwWLj-emI-_LhlAhnk8-pxja2fZbKYXiXiFTS1MyCb3eQ3OCATR7DKGvVFOQRi2Qus6D-drAtrK366ROPwumIhgMIV2uHpVyXpC-kruoB7sHP5kcowteoBU6yImv8h9tjnrZPG4d_uFdSANWZFOzaw1v7u6TzinIIdqBcM5aFVktMI4pOAIWQADrt0bjUX7K_lZyUfIA1rIChjpepjK6tpHnrNhc4ohcJj_DH_UZpwA=)