## Sayan_Biswas_OpenSTA_Workshop_Report
OpenSTA 5-Day Workshop Report - Team VSDIAT- Kunal Ghosh, Vikas Sachdeva

## SIGN-OFF TIMING ANALYSIS
![image](https://user-images.githubusercontent.com/125567197/220543510-934adf86-52b7-441a-b6bc-d2eba1dd7d2f.png)

  ##                                          :  TABLE OF CONTENT  :
# 1. Day - 1 :
  
  •	OpenSTA INTRODUCTION AND BASICS
  
  •	INPUTS OF OpenSTA
  
  •	CONSTRAINTS CREATION
  
  •	RUNSCRIPT FOR OpenSTA
  
  •	SLACK CALCULATION
  
# 2. Day - 2 :
  
  •	UNDERSTANDING LIBERTY FILE
  
  •	EXERCISE – 1
  
  •	UNDERSTANDING SPEF FILE
  
  •	EXERCISE – 2
  
# 3. Day - 3 :
  
  •	UNDERSTANDING SLACK COMPUTATION
  
  •	EXERCISE

# 4. Day - 4 :
  
  •	CLOCK GATING CHECKS EXERCISE
  
  •	ASYNC PIN CHECKS EXERCISE

# 5. Day - 5 :
  
  •	CPPR
  
  •	ECO INSERTION

# 6. ACKNOWLEDGEMENTS

# 7. AUTHOR


  ##                                          : INTRODUCTION TO STA :
  Before starting, we must understand what STA means in VLSI Domain. With the rapid advancement of technology nodes in today's VLSI industries, chip area has shrinked 
to a large extent that, it now created more complicated issues that we used to ignore earlier as their impact was negligible. A best example is the increased short-channel effects, leakage etc.,which ultimately hampers the proper functionality and speed of the circuit. Speed perhaps, is the most important and critical topic now-a-days for any engineer in vlsi industry.
  In this scenario, it is very important to analyse the timings for proper functioning of any circuit. As contrary to the chip size, the circuits have grown more complex for past few years. so, it is very tideous, complex and error prone task if done conventionally. Here comes STA tools to our rescue. STA tools are nothing but specialized tools being created to handle this complex task. STA tools are typically Exhaustive and Conservative i.e., it is "PESSIMISTIC" which allows it to rule out even the slightest errors. STA tools only works for synchronous part of the circuit. There are numerious open source STA tools available now-a-days to help the designers eg.- OpenSTA, OpenTimer etc.
  
  Inputs for a typical STA tool :
  (1).Netlist
  (2).SDC or Constraint file
  (3).Logic Libraries
  
  The STA tools works simply checks various timing constraints being fed to it and accordingly generate the result as timing is "MET" or "VIOLATED". the tool uses the relation : SLACK = REQUIRED TIME - ACTUAL ARRIVAL TIME. we have several set of commands that can be used in the constraint file to impose the required constraints.


## DAY - 1 :

# OpenSTA INTRODUCTION AND BASICS :

OpenSTA is a gate level static timing verifier. As a stand-alone executable it can be used to verify the timing of a design using standard file formats. An STA tool takes design, standard cell, constraints as input and perform timing checks on the design.
![image](https://user-images.githubusercontent.com/125567197/220551822-db087d61-78cc-407e-8fe4-97856dc0ec3c.png)

Above figure show the typical OpenSTA Network.

# INPUTS OF OpenSTA :

(1).Netlist - .v file

(2).SDC or Constraint file - .sdc file

(3).Logic Libraries - .lib file

Following figure shows the command and the path for the files associated :
![01](https://user-images.githubusercontent.com/125567197/220553934-37ccf7da-03d4-42fc-ba00-c2020fe2cb15.png)

Following figure shows the input design file written Verilog HDL :
![02](https://user-images.githubusercontent.com/125567197/220554348-ff97551d-e22c-4736-ae85-c499ae828312.png)

Following figure shows the input design :
![20230222_131220](https://user-images.githubusercontent.com/125567197/220555565-41aae663-3227-4320-abda-2fbc9331e084.jpg)

# CONSTRAINTS CREATION :

Following figure shows the command for liberty file :
![03](https://user-images.githubusercontent.com/125567197/220555335-af05f447-ead5-4b61-9cea-bb2c3ba42139.png)

Following figure shows the “sky130_fd_sc_hd__nand2_1" cell in liberty file :
![04](https://user-images.githubusercontent.com/125567197/220563517-70ad04c3-e74c-4698-aa83-be7c2c77cb05.png)
The cell - “sky130_fd_sc_hd__nand2_1" has pins: 'A' , 'B' and 'Y'.

Following figure shows the constraint file (simple.sdc) :
![06](https://user-images.githubusercontent.com/125567197/220564391-86b894e3-e485-4d79-9cde-03fa5d819213.png)

# RUNSCRIPT FOR OpenSTA :

Following figure shows the runscript file (run.tcl) :
![07](https://user-images.githubusercontent.com/125567197/220564620-6d731ec5-bf65-450c-b8d6-f274e56adaa1.png)

# SLACK CALCULATION :

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


## DAY - 2 :

# UNDERSTANDING LIBERTY FILE :

![image](https://user-images.githubusercontent.com/125567197/220569160-7fd15eee-5530-4269-924c-22d81e2c1f62.png)
![image](https://user-images.githubusercontent.com/125567197/220569340-cc31174d-bc79-4638-9a3c-d5d603cbe85a.png)

# EXERCISE – 1 :

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

(4). What is the difference between ‘simple_max.lib’ and ‘simple_min.lib' .
simple_max.lib files considers all the maximum time constraints, maximum fanout RC delays whereas, simple_min.lib includes all the minimum timing related specifications.

# UNDERSTANDING SPEF FILE :
following figure shows a glimps of spef parsing :
![image](https://user-images.githubusercontent.com/125567197/220575295-a77469c0-6271-4e5b-b768-20304626db07.png)

# EXERCISE - 2 :

Following figure shows the Slack Computation (STA Text Report):
![14](https://user-images.githubusercontent.com/125567197/220575875-b5543ed4-05cc-462f-9084-50c308bfacbe.png)

## DAY - 3 :

# UNDERSTANDING SLACK COMPUTATION :

Following figure shows the design used :
![01](https://user-images.githubusercontent.com/125567197/220577468-842fec87-6848-4787-bcae-d8f88c909409.png)

follwing are some of the paths we can easily notice :

F1:CK→U3→U4→U6:A2→U7:A1→F2:D

F1:CK→U6→U4→U5:A1→U7:A2→F2:D

F1:CK→U6:A1→U7:A1→F2:D

F1:CK→U6→U5:A2→U7:A2→F2:D

for the same design, various paths were choosen and slack report for the corresponding paths were captured.

# EXERCISE :

Change the number of paths being reported to 100
1. report_checks –from F1/CK -endpoint_count 100
2. Analyze each path in detail and understand

Following STA Text Report was obtained for count 100 :
![02(100)](https://user-images.githubusercontent.com/125567197/220578733-9e5441d4-158d-446a-95ca-fd8da0f5a5b9.png)

Following figures shows the STA Text Report for various test cases :

count 1 :
![image](https://user-images.githubusercontent.com/125567197/220613810-ed8b2f5a-e0db-46b9-98ea-c3a28fcf2a9f.png)

count 2 :
![image](https://user-images.githubusercontent.com/125567197/220614054-46395142-697a-4471-b812-cc2f0e0b6162.png)

count 3 :
![image](https://user-images.githubusercontent.com/125567197/220614247-5661cd96-4256-40b2-8bf2-6e6e6872c063.png)

count 4 :
![image](https://user-images.githubusercontent.com/125567197/220614372-434f3065-f6b6-4ca5-a385-fec61ce1ca59.png)

count 5 :
![image](https://user-images.githubusercontent.com/125567197/220614486-c13c2b29-adff-424f-a8ca-366cf4a32a99.png)

count 6 :
![image](https://user-images.githubusercontent.com/125567197/220614585-8aa7a5c9-50a4-474c-997a-1b658124f331.png)

count 7 :
![image](https://user-images.githubusercontent.com/125567197/220614737-219fc987-4dcd-4eee-9b18-0d90f9953ca8.png)

count 8 :
![image](https://user-images.githubusercontent.com/125567197/220614873-a002015e-4a75-488c-a5d0-6d4d3f5ef0db.png)


## DAY - 4 :

# CLOCK GATING CHECKS EXERCISE :

In this lab we have included the codes for "Active High Clock Gating"

This is visible in the run.tcl file as shown below :
![01](https://user-images.githubusercontent.com/125567197/220616456-47a02d9c-1eba-4076-b431-7698bf762716.png)
This can also be seen in Verilog HDL design file, i.e., inclusion of the clock gating :
![02](https://user-images.githubusercontent.com/125567197/220616801-76eb88a9-6a80-4adc-b341-5f1b48929714.png)
The constraints associated with this clock gate must also be included in the constraint file , in our case it is "s27.sdc", the glymps of which is as show below :
![03-](https://user-images.githubusercontent.com/125567197/220617176-9f5f75fc-f6f8-4a8d-b51a-7825429cffc7.png)
![-04](https://user-images.githubusercontent.com/125567197/220617341-57ddd913-5e47-4a9f-b970-8730794088a5.png)

Now let us run the STA analysis to get STA Text Report for our model with clock gate :
![05](https://user-images.githubusercontent.com/125567197/220618811-e0ce8f2b-e498-485c-8d65-5888386237f4.png)
The design and timing arc is as shown :
![20230222_175226](https://user-images.githubusercontent.com/125567197/220620589-d62b8c00-117d-471b-b17b-739d73519935.jpg)


# ASYNC PIN CHECKS EXERCISE :

Following is the verilog design file :
![07](https://user-images.githubusercontent.com/125567197/220619726-e8625ee7-2f89-488f-8301-68fa43616ceb.png)
In order to perform Async Pin check, we must include removal and recovery constraints in the file :

One can easily observe it's effect in tcl file, as shown :
![06](https://user-images.githubusercontent.com/125567197/220620280-f18773ea-1a2a-40f6-8b76-5d5b77ccab90.png)
Now, let us perform Slack Computation and generate the STA Text Report :
![08](https://user-images.githubusercontent.com/125567197/220621134-5856d6e8-f951-404d-9cb0-7dc85e0115d7.png)

The design and timing arc is as shown :
![20230222_180848](https://user-images.githubusercontent.com/125567197/220622574-9611deb1-0e8a-4924-b5de-d67decc24c79.jpg)


## DAY - 5 :

Slack Computation procedure was revisited and a quick revision was done on 'how to understand the STA Text Report'.

# CPPR :

"Common Path Pessimism Removal" also known as CPPR is one of the constraints or techniques used to remove the common path elements, as this particular path is taken into account multiple times while STA considers various timing arcs.

Below figure shows the circuit of interest :
![image](https://user-images.githubusercontent.com/125567197/220624401-bfeb8f41-b3f6-406b-9459-0169de6ea37d.png)

Now, let us compute the Slack 'WITHOUT mentioning (turning ON) CPRR in run.tcl file' :
![03](https://user-images.githubusercontent.com/125567197/220625479-dc6e5253-7a25-430b-a540-1b9d76b88581.png)
we observed a value of -398.10

Now, let us enable the CPRR in run.rcl :

(By, replacing 0 with 1)
![04](https://user-images.githubusercontent.com/125567197/220625993-e66bf47a-d883-4cb3-9934-e34f840ebfb6.png)

Now, let us re-compute the sclack :
![05](https://user-images.githubusercontent.com/125567197/220626115-3b75728f-0005-43e6-8223-a9e4123eae3d.png)
Now, we get a value of -391.43, which got slightly improved when compared withthe case of without CPRR. Moreover, one can clearly observe other timing improvements in the paths when compared.


# ECO INSERTION :

Engineering Change Order also known as "ECO".

In the ECO cycle, we perform various analysis one by one for every 
check which we need to close but not closed till PnR stage. There are specialized signoff tools that help us to analyze the issue and also suggest the changes we need to do in order to close the issue. The suggested change is captured in an eco file.

So, let insert timing ECO as show below in the run.tcl file :
![06](https://user-images.githubusercontent.com/125567197/220628030-e0ac1e03-091d-42f2-985d-a12ac323ff6f.png)
Now, let us re-compute the slack after ECO insertion :
![07](https://user-images.githubusercontent.com/125567197/220628185-6b721872-6c9e-47b7-8561-756c58587a7d.png)

Following Figures shows the difference in the "s27.v" and "s27_eco.v" :
![image](https://user-images.githubusercontent.com/125567197/220631441-a2014c8e-5935-45ef-a3c8-a6ed01834a8a.png)

Finally, let us compare the Slack Improvemet "Before and After ECO Insertion" side-by-side :
![10](https://user-images.githubusercontent.com/125567197/220628945-c2b38b13-845e-41da-a74d-b896aec0c6e1.png)


## ACKNOWLEDGEMENTS :

1. Kunal Ghosh, Co-founder of VLSI System Design (VSD) Corp. Pvt. Ltd.
2. Vikas Sachdeva, Advisor, Tech and VLSI Coach, Trainer and Innovator at vlsideepdive.

## AUTHOR :

Sayan Biswas, M.Tech in VLSI Design (2022-2024), VIT-Vellore, Vellore, Tamil Nadu-632014, INDIA.

Contact: saybi2311697@gmail.com
