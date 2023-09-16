## PES Physical Design

**Course Name** : VLSI Physical Design for ASICs  
**Instructor** : Kunal Ghosh   
**About Course** : This course covers key aspects of RISC-V and chip design, spanning design cycles, RISC-V ISA, analog IPs, and mixed-signal flow. It delves into process design kits, libraries, RTL design synthesis, and gate-level simulation. The curriculum also includes RTL-to-GDS flow, encompassing SoC design implementation from floor planning to post-layout timing analysis.<br>

### **In this repository will be covering the `Physcial Design` Part of our Course.**

This is Week 3 of our course, th contents of week 1,2 are in this repository<br> https://github.com/vamsi-2312/pes_asic_class
<br>

Week 1 - Introduction<br>
Week 2 - RTL<br>
Week 3 - Physical Design<br>

## Contents of Week 3

### + Contents of Day 1
* How to talk to computers.
* Soc Design and Openlane
* Open Source EDA Tools.

## Course
<details>
<summary> Week 3 -> Day 1 </summary><br>

## Contents of Day 1
+ How to talk to computers.
+ Soc Design and Openlane
+ Open Source EDA Tools.

## How to talk to computers.

### Chip design
![image1](https://github.com/vamsi-2312/pes_pd/assets/142248038/a130d96f-9bf7-4e42-839e-05a3e89a25d0)

let get inside a chip

![image2](https://github.com/vamsi-2312/pes_pd/assets/142248038/552da4d7-b400-4800-a999-89ed310e9a86)

![image3](https://github.com/vamsi-2312/pes_pd/assets/142248038/5f4677d1-b412-4f2e-997a-2786a12992a5)

(before ths class we call as system but nw we call as package)

PADS - the ways signal comes inside or goes outside<br>
CORE - all the digital logic recides<br>
DIE - size of the chip<br>

Foundry IP's - PLL,adc,dac,sram<br>
foundry - factory where chip get manufactured<br>
macros - Soc, SPI<br>

ISA the way we talk to the computer<br>

How to run a C Program on a cpu, there is a certain flow<br>

RISC  Architecture -> Implementation(RTL) -> Layout<br>

C program -> Assemble Level program -> Machine level program<br>
![image4](https://github.com/vamsi-2312/pes_pd/assets/142248038/35bb44c2-0c93-4c59-9985-96da10278581)

Application software run on hardware<>br
How do they run?<br>

Applicatioin software -> System software -> Hardware<br>

System software has complier and assembler<br>
OS handles IO Operation, allocates memory ans low level system functions.<br>

*Application* --> OS --> C code --> *Complier* --> ISA --> *Assembler* --> Binary Code --> *Hardware*<br>

![image5](https://github.com/vamsi-2312/pes_pd/assets/142248038/01c756a1-ab75-4d42-a21e-2a46b76dd233)

ISA acts as the abstract interface between C language and the Hardware(Architecture of the Hardware)

ISA --> Assembler --> Binary --> RTL --> synthesis of RTL(netlist) --> Hardware(Physical Implementation of netlist)

![image6](https://github.com/vamsi-2312/pes_pd/assets/142248038/91cc27ce-f0c4-4b1e-93c5-f5d516adab06)

## Soc Design and Openlane

### **SoC Design Using Openlane**

ASIC - Application Specific Integrated Circits<br>

TO build ASIC, we need
1. RTL Design
2. EDA Tools
3. PDK Data

PDK - Process Design Kit<br>
Collection of files used to model fabrication process for the EDA tools used to design an IC.
* Process Design Rules. - DRC, LVS, PEX
* Device Models
* Digital Standard Cell Libraries
* I/O Libraries
* etc

![image7](https://github.com/vamsi-2312/pes_pd/assets/142248038/8282aad1-2db3-4c67-8b99-6ea8e9eb8e69)

### **Simplified RTL to GDSII Flow**

RTL -> Synthesis -> Floor and Power Planning -> Placement of Cells -> Clock Tree Synthesis  -> Routing -> Sign Off -> GDSII<br>

![image8](https://github.com/vamsi-2312/pes_pd/assets/142248038/23ddbf4c-bdcc-436e-9693-9dfbfec48453)

*Sythesis*<br>
Converts RTL to a circuit out of componets from the standard cell library(SCL)<br>

![image9](https://github.com/vamsi-2312/pes_pd/assets/142248038/bbb1a2c5-76df-4dde-9ab5-8f50d2ab57cb)

*Floor and Power Planning*<br>

![image10](https://github.com/vamsi-2312/pes_pd/assets/142248038/6bb51aae-d893-412c-a1ec-ef3dd5a8f2dc)

![image11](https://github.com/vamsi-2312/pes_pd/assets/142248038/1c52ec3a-0b12-46ca-ab7f-c982eda180e7)

![image12](https://github.com/vamsi-2312/pes_pd/assets/142248038/749b7d89-2c72-40b8-a244-a221f903da61)

Connecting power supply from VDD.<br>

*Placement*<br>
place the cells on the floorplan rows, aligned with the sites.<br>

<image 13>

2 steps
* Global placement
* Detailed placement

*Clock Tree Synthesis*
* to deliver the clock to all sequential elements
* to attain minimum skew
* usally in shape of tree

<image 14>

*Routing*<br>
Interconnect using metal layers

<image 15>

Global Routing - generated routing guides.<br>
Detailed Routing - Using the routing guides to implement the actual wiring.<br>

*Sign Off*<br>
Physical Verification
* DRC(Design rule check)
* LVS(Layout vs Schematic)
Timing Verification
*Static timing analysis

### **Introduction to OPENLANE**

OPENLANE is an open-source software platform for designing and verifying digital integrated circuits (ICs). Developed by Efabless, it streamlines the process of ASIC (Application-Specific Integrated Circuit) design by automating many tedious tasks. OPENLANE utilizes open-source EDA (Electronic Design Automation) tools and libraries, fostering collaboration and reducing design cycle times. It has gained popularity within the semiconductor industry for its ability to simplify and accelerate the chip design process, making it accessible to a wider range of designers and engineers.<br>

Main Goal:<br>
To produce a clean GDSII with no human ntervention.<br>

Clean meaning, no LVD erors, no DRC errors and timing violations(still work in progress).<br>

tuned for skyWater 130nm OpenPDK<br>

Containerized
* Functional out of the box
* Instructions to build and run natively will follow

Can be used to generate finall layouts of macros and chips<br>

Two modes of Operation
* Automonous and Interctive

Design Space Exploration
* To Find the best set of low configurations.

### **OpenLane ASIC Flow**

<image 16>

+ RTL Synthesis with constraints is done using Yosys and abc
+ The design exploration utility is also used for regression testing.
+ Openlane can run 70 designs and compare the results and find the best one.
+ Scan Insertion
+ Automatic Test Pattern Generation
+ Test Patter Compaction
+ Fault Coverage
+ Fault Simulation
+ Physical Implementation - F&PF,Placement,CTS,Routing
+ Verification is performed everytime netlist is modified.
+ LEC is used to formally confirm that the function did not change after modifying the netlist.
+ Antenna Checker
+ RC Extraction
+ Static timing Analysis
+ DRC and LVS

## Open Source EDA Tools.

In terminal
```
cd Desktop
```

we will be using sky130 pdk

<image 17>

tools files
<image 18>

process files
<image 19>

Openlane is used to automate rtl to gds flow<br>

```
cd ~/Desktop/work/tools/openlane_working_dir/openlane
```
```
docker
```
<image 20>

```
./flow.tcl -interactive
```
<image 21>

```
package reqire openlane 0.9
```
list of designs already present in openlane

<image 22>

<image 23>

<image 24>

design setup stage(preparing stage)
```
prep -design picorv32a
```

<image 25>

we can see that runs getting created

<image 26>

<image 27>

coming back to openlane

lets run the synthesis
```
run_synthesis
```
<image 28>

We can observe the results in the runs folder
</details>
