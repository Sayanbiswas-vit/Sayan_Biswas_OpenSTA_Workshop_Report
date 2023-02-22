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

OpenSTA INTRODUCTION AND BASICS :

OpenSTA is a gate level static timing verifier. As a stand-alone executable it can be used to verify the timing of a design using standard file formats. An STA tool takes design, standard cell, constraints as input and perform timing checks on the design.
![image](https://user-images.githubusercontent.com/125567197/220551822-db087d61-78cc-407e-8fe4-97856dc0ec3c.png)

Above figure show the typical OpenSTA Network.

INPUTS OF OpenSTA :

(1).Netlist - .v file

(2).SDC or Constraint file - .sdc file

(3).Logic Libraries - .lib file

Following figure shows the command and the path for the files associated :
![01](https://user-images.githubusercontent.com/125567197/220553934-37ccf7da-03d4-42fc-ba00-c2020fe2cb15.png)

Following figure shows the input design file written Verilog HDL :
![02](https://user-images.githubusercontent.com/125567197/220554348-ff97551d-e22c-4736-ae85-c499ae828312.png)

Following figure shows the input design :
![20230222_131220](https://user-images.githubusercontent.com/125567197/220555565-41aae663-3227-4320-abda-2fbc9331e084.jpg)

CONSTRAINTS CREATION :

Following figure shows the command for liberty file :
![03](https://user-images.githubusercontent.com/125567197/220555335-af05f447-ead5-4b61-9cea-bb2c3ba42139.png)

Following figure shows the “sky130_fd_sc_hd__nand2_1" cell in liberty file :
![04](https://user-images.githubusercontent.com/125567197/220563517-70ad04c3-e74c-4698-aa83-be7c2c77cb05.png)
The cell - “sky130_fd_sc_hd__nand2_1" has pins: 'A' , 'B' and 'Y'.

Following figure shows the constraint file (simple.sdc) :
![06](https://user-images.githubusercontent.com/125567197/220564391-86b894e3-e485-4d79-9cde-03fa5d819213.png)

RUNSCRIPT FOR OpenSTA :

Following figure shows the runscript file (run.tcl) :
![07](https://user-images.githubusercontent.com/125567197/220564620-6d731ec5-bf65-450c-b8d6-f274e56adaa1.png)

SLACK CALCULATION :

Following figure shows the command to run the timing analysis :
![08](https://user-images.githubusercontent.com/125567197/220564947-7f9d438a-b01c-4c74-acba-a33b4aebadce.png)

Following figure shows the run-time output (Slack Calculation) :
![09](https://user-images.githubusercontent.com/125567197/220565328-499acc03-ff37-47ef-95ac-e4c4c27157d5.png)

Now let us remove some commands in runscript and see the output :
let us comment the link command, which will prevent the STA to link our design :
![10](https://user-images.githubusercontent.com/125567197/220566626-6df14eba-1f2e-46cb-aef2-5541624e08b6.png)

Following is the output :
![11](https://user-images.githubusercontent.com/125567197/220566942-106f66cb-4929-4d4c-aace-a5d2f2a2fe58.png)

let us now, comment the liberty file reading operation :
![12](https://user-images.githubusercontent.com/125567197/220567115-ba4e4f6d-8fda-4bae-97c9-84f441ff2bd2.png)

following is the output :
![13](https://user-images.githubusercontent.com/125567197/220567323-2e492b69-28e8-48e4-852d-66107c931a24.png)

Now, let us comment the clock creation in sdc file :
![14](https://user-images.githubusercontent.com/125567197/220567567-eb0b1664-40e3-487c-9c0c-023184a54996.png)
 Following is the output :
![15](https://user-images.githubusercontent.com/125567197/220567842-5dbb6069-29aa-4c4c-941e-a8e88fe23d91.png)


DAY - 2 :

UNDERSTANDING LIBERTY FILE :

![image](https://user-images.githubusercontent.com/125567197/220569160-7fd15eee-5530-4269-924c-22d81e2c1f62.png)
![image](https://user-images.githubusercontent.com/125567197/220569340-cc31174d-bc79-4638-9a3c-d5d603cbe85a.png)

EXERCISE – 1 :

(1). Find all the cells in simple_max.lib.
following figure show the cell count to be 211 :
![01](https://user-images.githubusercontent.com/125567197/220569834-84e2425c-b9de-4393-acf4-367d265874e3.png)

(2). Find all the pins of the cell NAND2_X1 in simple_max.lib.
following figure shows all the cells :
![02](https://user-images.githubusercontent.com/125567197/220571155-af45221c-539d-4d16-8dcd-a7f74c74411b.png)
![03](https://user-images.githubusercontent.com/125567197/220571208-fe7364d3-1d3a-4330-8142-e54108b6b245.png)
![06](https://user-images.githubusercontent.com/125567197/220571255-9242238d-085a-4f43-9e5c-bb7f4034db63.png)
![07](https://user-images.githubusercontent.com/125567197/220571280-bed4e3a9-8173-4813-94db-673b260965fd.png)

(3).What difference you see between NAND2_X1 and NAND3_X1.
following figures shows the differences :
![image](https://user-images.githubusercontent.com/125567197/220572799-a0b8963d-9da1-4b8e-b20b-453197d160d8.png)
![image](https://user-images.githubusercontent.com/125567197/220573167-07bd96a6-2f8a-465a-829a-f7073b6fccb1.png)
