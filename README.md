# Sayan_Biswas_OpenSTA_Workshop_Report
OpenSTA 5-Day Workshop Report - Team VSDIAT- Kunal Ghosh, Vikas Sachdeva

SIGN-OFF TIMING ANALYSIS
![image](https://user-images.githubusercontent.com/125567197/220543510-934adf86-52b7-441a-b6bc-d2eba1dd7d2f.png)

                                                          :  TABLE OF CONTENT  :

                                                           : INTRODUCTION TO STA :
  Before starting, we must understand what STA means in VLSI Domain. With the rapid advancement of technology nodes in today's VLSI industries, chip area has shrinked 
to a large extent that, it now created more complicated issues that we used to ignore earlier as their impact was negligible. A best example is the increased short-channel effects, leakage etc.,which ultimately hampers the proper functionality and speed of the circuit. Speed perhaps, is the most important and critical topic now-a-days for any engineer in vlsi industry.
  In this scenario, it is very important to analyse the timings for proper functioning of any circuit. As contrary to the chip size, the circuits have grown more complex for past few years. so, it is very tideous, complex and error prone task if done conventionally. Here comes STA tools to our rescue. STA tools are nothing but specialized tools being created to handle this complex task. STA tools are typically Exhaustive and Conservative i.e., it is "PESSIMISTIC" which allows it to rule out even the slightest errors. STA tools only works for synchronous part of the circuit. There are numerious open source STA tools available now-a-days to help the designers eg.- OpenSTA, OpenTimer etc.
  
  Inputs for a typical STA tool :
  (1).Netlist
  (2).SDC or Constraint file
  (3).Logic Libraries
  
  The STA tools works simply checks various timing constraints being fed to it and accordingly generate the result as timing is "MET" or "VIOLATED". the tool uses the relation : SLACK = REQUIRED TIME - ACTUAL ARRIVAL TIME. we have several set of commands that can be used in the constraint file to impose the required constraints.


DAY - 1 :

OpenSTA Introduction and Basics :

OpenSTA is a gate level static timing verifier. As a stand-alone executable it can be used to verify the timing of a design using standard file formats. An STA tool takes design, standard cell, constraints as input and perform timing checks on the design.
![image](https://user-images.githubusercontent.com/125567197/220551822-db087d61-78cc-407e-8fe4-97856dc0ec3c.png)

