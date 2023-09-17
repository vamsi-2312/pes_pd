## PES Physical Design

**Course Name** : VLSI Physical Design for ASICs  
**Instructor** : Kunal Ghosh   
**About Course** : This course covers key aspects of RISC-V and chip design, spanning design cycles, RISC-V ISA, analog IPs, and mixed-signal flow. It delves into process design kits, libraries, RTL design synthesis, and gate-level simulation. The curriculum also includes RTL-to-GDS flow, encompassing SoC design implementation from floor planning to post-layout timing analysis.<br>

### **In this repository will be covering the `Physcial Design` Part of our Course.**

This is Week 3 of our course, the contents of week 1,2 are in this repository<br> https://github.com/vamsi-2312/pes_asic_class
<br>

Week 1 - Introduction<br>
Week 2 - RTL<br>
Week 3 - Physical Design<br>

## Contents of Week 3

### + Contents of Day 1
* How to talk to computers.
* Soc Design and Openlane
* Open Source EDA Tools.

### + Contents of Day 2
* Chip Floor planning considerations.
* Library Binding and Placement
* Cell Design and Characterisation flow.
* General timinig and Characterisation parameters.

### + Contents of Day 3
* Labs for CMOS inverter ngspice simulations.
* Inception of Layout CMOS fabrication process.
* sky130 Tech file Labs

### + Contents of Day 4
* Timing modeling using delays.
* Timing analysis with ideal clocks using openSTA
* Clock tree synthesis TritonCTS and signal integrity.
* Timing analysis with real clocks using openTA

### + Contents of Day 5
* Routing and Design rule check(DRC)
* Power Distribution Network and routing.
* TritonRoute Features.

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

![image13](https://github.com/vamsi-2312/pes_pd/assets/142248038/862e7259-49d1-4460-b71d-799357ee997e)

2 steps
* Global placement
* Detailed placement

*Clock Tree Synthesis*
* to deliver the clock to all sequential elements
* to attain minimum skew
* usally in shape of tree

![image14](https://github.com/vamsi-2312/pes_pd/assets/142248038/cf73679f-b3fd-4c30-b0af-f776985fe0dd)

*Routing*<br>
Interconnect using metal layers

![image15](https://github.com/vamsi-2312/pes_pd/assets/142248038/757d22d6-e846-4505-81d6-522e2977033b)

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

![image16](https://github.com/vamsi-2312/pes_pd/assets/142248038/c7dee39a-9fe8-4ede-8e54-c5ffa375e4a6)

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

![image17](https://github.com/vamsi-2312/pes_pd/assets/142248038/204392df-84a8-4873-8909-fe8ef1d81c53)

tools files
![image18](https://github.com/vamsi-2312/pes_pd/assets/142248038/2920e46a-87da-41e0-a160-004aa23ccc6a)

process files
![image19](https://github.com/vamsi-2312/pes_pd/assets/142248038/d2d3cb64-a8a5-47b0-a4c0-924dbdf94d7b)

Openlane is used to automate rtl to gds flow<br>

```
cd ~/Desktop/work/tools/openlane_working_dir/openlane
```
```
docker
```
![image20](https://github.com/vamsi-2312/pes_pd/assets/142248038/079f2f22-412c-450e-bd29-3c3e598c5546)

```
./flow.tcl -interactive
```
![image21](https://github.com/vamsi-2312/pes_pd/assets/142248038/42ccb948-63b2-476c-b1cc-0afa73b20b21)

```
package require openlane 0.9
```
list of designs already present in openlane

![image22](https://github.com/vamsi-2312/pes_pd/assets/142248038/004acec0-75fe-46be-b000-05b8ef3f745b)

![image23](https://github.com/vamsi-2312/pes_pd/assets/142248038/1e503208-7a4b-4cd8-b6f2-5c0a5262e15c)

![image24](https://github.com/vamsi-2312/pes_pd/assets/142248038/9efa9e1a-13d3-4b7d-88ed-a8b049e0ac1e)

design setup stage(preparing stage)
```
prep -design picorv32a
```

![image25](https://github.com/vamsi-2312/pes_pd/assets/142248038/770c5449-2d93-4a5d-8008-9237e8762228)

we can see that runs getting created

![image26](https://github.com/vamsi-2312/pes_pd/assets/142248038/e7f86f88-e105-4f54-87d6-2f0072caf7d5)

![image27](https://github.com/vamsi-2312/pes_pd/assets/142248038/56b109e6-5a2f-43ed-825b-b62078b683b9)

coming back to openlane

lets run the synthesis
```
run_synthesis
```
![image28](https://github.com/vamsi-2312/pes_pd/assets/142248038/a39df1a0-92d8-4086-82f3-407ac3cf1a0d)

We can observe the results in the runs folder

![Screenshot from 2023-09-16 18-31-43](https://github.com/vamsi-2312/pes_pd/assets/142248038/dc52f3a3-51f6-4356-b31c-3310a23951f0)
![calimg2](https://github.com/vamsi-2312/pes_pd/assets/142248038/42ed2e89-a308-41a2-b749-b699a099f461)

We are getting flip flop ratio as 10.8% <br>

![netlist_gen](https://github.com/vamsi-2312/pes_pd/assets/142248038/9fe8ffb5-162f-4b65-a25e-404df04f33b0)

Netlist generated
</details>

<details>
<summary> Week 3 -> Day 2 </summary><br>

## Contents of Day 2
+ Chip Floor planning considerations.
+ Library Binding and Placement
+ Cell Design and Characterisation flow.
+ General timinig and Characterisation parameters.

## Chip Floor planning considerations

How to come up with the Width and Height of the Core and Die.<br>
![image1](https://github.com/vamsi-2312/pes_pd/assets/142248038/b8fc80da-1a20-442c-81fa-ce7f84204fc8)

we will start with basic netlist<br>
![image2](https://github.com/vamsi-2312/pes_pd/assets/142248038/2f87c0ed-09ae-4a82-b0cb-00c620af82f9)

contains flipflops, and gate, or gate<br>

we are mostly intreseted in the dimensions of the standard cells.<br>

Lets start with rough dimensions of Standard cells and Flip flops as 1unit x 1unit, area = 1sq. unit<br>
![image3](https://github.com/vamsi-2312/pes_pd/assets/142248038/0f990515-b828-4571-a72c-a6251dd69c2e)

lets calculate the area occupied by the netlist on a silicon wafer.<br>
arranging the cells and flip flops<br>
![image4](https://github.com/vamsi-2312/pes_pd/assets/142248038/36963d3a-ace4-4092-b39b-1c02bc1b65f0)

What is the core and die of the chip?<br>
A die which consists of core, is smallsemiconductor material specimen on which the fundamental circuit is fabricted.<br>
We imprint the die multiple times in the chip.<br>
![image5](https://github.com/vamsi-2312/pes_pd/assets/142248038/d10fc15d-3269-48c2-a654-fa889d443c7b)

The netlist occuping 4sq. units in placed inside the core.<br>
In this case we are at 100% utilization of the core area, because the logial cells occupies the complete are of the core.<br>
![image6](https://github.com/vamsi-2312/pes_pd/assets/142248038/b154b5e8-dc87-40e5-aa47-7896fd65af25)

Utilization Factor = (Area Occupied by netlist)/(Total Area of the Core)<br>
Utilization factor = 1<br>

Usually we design with utilization factor of 0.5, 0.6<br>

Aspect Ratio = Height/Width<br>
Aspect Ratio = 1(square chip)<br>

If the aspect ratio is other than 1, it means that the chip is in rectangular shape.<br>

lets take another example,<br>
![image7](https://github.com/vamsi-2312/pes_pd/assets/142248038/0fc0ee58-8a58-4443-abd2-40e3bcc60d3f)

utilization factor = 0.5 (only 50% is being used, 50% is free)<br>
aspect ratio = 0.5 (rectangle chip)<br>

![image8](https://github.com/vamsi-2312/pes_pd/assets/142248038/1518cdca-11b5-424b-8fde-5da9389e4f71)

utilization factor = 0.25<br>
aspect ratio = 1 (sqaure chip)<br>

Next step is Define the Locations of Perplaced cells.<br>
What are preplaced cells - Preplaced cells in semiconductor design are manually positioned blocks on an integrated circuit chip. Unlike standard cells, they offer custom functionality, with fixed placements to optimize chip performance, power, and connectivity. Designers strategically place them to meet specific design requirements and ensure overall chip functionality.<br>

![image9](https://github.com/vamsi-2312/pes_pd/assets/142248038/9499696e-5e05-4937-9134-78bacd8be5af)

1. combinational logic
2. Cut into 2 halves
3. Put each half in one block and connect them.
4. Black box the boxs
5. Seperate the Black boxex as two different IP's or modules.
Then we can use this modules multiple times, rather than wrting everything.<br>
![image10](https://github.com/vamsi-2312/pes_pd/assets/142248038/484fb214-29ba-41ee-9c87-a24998777e79)

Similary there are other IP's also available<br>
![image11](https://github.com/vamsi-2312/pes_pd/assets/142248038/a56a6fc9-f818-443d-9f95-5359b183c95e)

The arrangement of these IP's in a chip is refered as `FloorPlanning`.<br>
These IP's/blocks have user-defined loations, and hence are placed in chip before automated placement and routing are called as pre-placed cells.<br>
Automated placement and routing tools places the remaining logical cells in the design onto chip.<br>

Once these Preplaced cells are fixed, they arent going to be changed.<br>

Preplaced cells are placed nearer to the input side, and their locations are going to changed.<>br
Next we need to surround the preplaced cells with `decoupling capacitors`.<br>

To prevent the delay in charging and discharging of the capacitor by the voltge source which is far away, we use decoupling capacitors which is completed filled with charge to voltage source. we call it decoupling capacitor because it decouples the circuit from the main supply. now there will be no drop in votage.<br>
![image12](https://github.com/vamsi-2312/pes_pd/assets/142248038/f34bb459-b0e4-42fd-bdf4-d185500a376f)

![image13](https://github.com/vamsi-2312/pes_pd/assets/142248038/faf8f9fe-decf-4905-8d5e-b5ccedb6df5a)

Placing the preplaced cells and decoupling capacitors.<br>
![image14](https://github.com/vamsi-2312/pes_pd/assets/142248038/88ac1d7f-7cb2-483f-925f-bf00a8eeb183)

Next step is Power Planning.<br>
We need to transfer the value long the red line.<br>
Lets assume the read line is a 16-bit bus and i connected to an inverter.<br>
![image15](https://github.com/vamsi-2312/pes_pd/assets/142248038/c7f946b9-0029-49ba-990f-9e1fd8f2ee40)

At once all the ones are made zero, and zeros are made ones, due to this there is bump in the ground tap point as all 16-bit are connected to the same ground.<br>
![image16](https://github.com/vamsi-2312/pes_pd/assets/142248038/e8473520-31dc-47ab-8873-9bda4f89b9d6)

The phenomenon is called ground bounce and it will eventually settle down.<br>
If the capacitors are charging from low to high, there is a Voltage drop in the Supply Voltage.<br>
![image17](https://github.com/vamsi-2312/pes_pd/assets/142248038/4d61bb1e-d634-4822-b932-c8af5ba3e966)

This issue is coming because we are having only one power supply, it was having multiple power supplies we would have this issue. Now we are going to have multiple power supplies.<br>
![image18](https://github.com/vamsi-2312/pes_pd/assets/142248038/e9444942-aa20-4a32-80d9-27a17721042e)

It is called as mesh.<br>
![image19](https://github.com/vamsi-2312/pes_pd/assets/142248038/7b0b49f3-fab5-4e0a-990b-38ffe02794b8)

Next step is Pin Placement.<br>
lets take an example<br>
![image20](https://github.com/vamsi-2312/pes_pd/assets/142248038/2bd1789e-9edf-4de6-9a43-886066ea37cf)

![image21](https://github.com/vamsi-2312/pes_pd/assets/142248038/973df839-2ba7-4f1f-a45a-3dc1f68988e0)

the complete design<br>
![image22](https://github.com/vamsi-2312/pes_pd/assets/142248038/00f878f2-eca3-49a1-ae4e-2a4d38ea83b6)

The connectivity informtion beteen the gates is codes using VHDL and is called as the Netlist.<br>

Usually we put all input ports in the left and all output ports in the right.<br>
The ordering the ports are random.<br>
![image23](https://github.com/vamsi-2312/pes_pd/assets/142248038/07f15ba4-ba2e-4c4f-961f-6d503c2786f3)

We have created bigger path for clks than inputs to prevent any resistance the flow of signal.<br>
And in the remaining place in between the core and die we put logical cell placement blockage to prevent the automated and routing tool doesnt place any cells in this area.<br>
![image24](https://github.com/vamsi-2312/pes_pd/assets/142248038/4cb27f37-5219-45ce-a65f-40e99bdc9526)

Next, Floorplan is ready for placement and routing.<br>
open terminal<br>
```
cd ~/Desktop/work/tools/openlane_working_dir/openlane/configuration
```
```
ls -ltr
```
![image24aaadell](https://github.com/vamsi-2312/pes_pd/assets/142248038/1fa30691-d607-41ce-a5e1-aa469c3d18e9)
```
cat README.md
```
![image25dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/377e40a6-eb07-4846-8662-99c2133d5ba5)

![image26dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/edbc5a3d-800e-4610-ac12-002b3a55ae1c)

similary we have placement, CTS, routing, etc.<br>
![image27dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/1574ec80-beb8-45e3-92e2-de40216125e9)

open new terminl tab<br>
```
cd ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a
```
![image28dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/ea579514-c486-41cb-947b-6aa812d9d5f8)

Start up openlane<br>
```
run_synthesis
```
```
run_floorplan
```
![image29dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/0b65db51-145c-4d77-b79c-fcb3b2b115b2)

![image30dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/b903785c-d237-47ec-bade-71b204f8c6c0)

![image31dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/eddf3dfc-72cc-46fc-9354-12c42c3aad1e)

```
cd ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/16-09_17-39/results/floorplan
```
```
less picorv32a.floorplan.def
```
![image32dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/ffe283ce-464e-423d-8b11-0fdf213408ae)

```
cd ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/16-09_17-39/results/floorplan
```
```
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
```
![image33dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/7eb70075-62a6-4f2a-a6aa-5503d00a2649)

![image34dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/21906e06-8387-49ed-924f-f36eb1ee2600)

![image35dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/a715c463-ab94-45c9-8210-53b332317ee0)

![image36dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/00e8935e-af67-4002-a6b6-0f8a45a8878a)

Standard cells are present at the bottom left.<br>
![image37dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/0a35aa28-5b0a-4054-b308-3d6a69594752)

![image38dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/9e27ff91-cae0-4c26-8e0a-5a6cc4dae53d)

Next Step is Placement and Routing<br>

##  Library Binding and Placement

Bind the netlist with physical cells.<br>
The nelist is containing the cells is represented as blocks which is the actual representation in the chip.<br>
![image39](https://github.com/vamsi-2312/pes_pd/assets/142248038/6aac2d0d-c48e-4aa2-880c-1cb8d96c9c4a)

Library - contain all the information about the cells.<br>
It will also have different flavors of the same cells and use what we want based on the conditioin.<br>
![image40](https://github.com/vamsi-2312/pes_pd/assets/142248038/b233fcdc-d8cc-4088-a9d5-97e0863916ad)

The library also have the timing information of the cells.<br>
Now we need to place these cells in our floorplan.<br>
![image41](https://github.com/vamsi-2312/pes_pd/assets/142248038/622b13eb-6b4a-4260-9046-d0d5a6ab0134)

Placing the cells.<br>
![image42](https://github.com/vamsi-2312/pes_pd/assets/142248038/aa5ec0cf-c8dd-435c-9b5f-8201ce80a8c9)

![image43](https://github.com/vamsi-2312/pes_pd/assets/142248038/574816a4-d10b-4182-9cb6-b12544e11e93)

OPtimize Placement<br>
This is the stage where we estimate length and capacitance and, based on that, insert repreaters.<br>
![image44](https://github.com/vamsi-2312/pes_pd/assets/142248038/87e00c3c-ec5a-4aec-acec-930113f224f2)

![image45](https://github.com/vamsi-2312/pes_pd/assets/142248038/288113d4-70ee-4c49-9e4b-c8ab1494efe2)

![image46](https://github.com/vamsi-2312/pes_pd/assets/142248038/4bf8d314-c829-4ea8-9a8c-d1fdad337aa9)

![image47](https://github.com/vamsi-2312/pes_pd/assets/142248038/dbe93cdd-de26-42bd-b4ef-b3f318b27586)

Need Characterisation<br>
Library Characterisation and modelling<br>
Every Design must go through if it wants to be implemented in a chip.<br>
Step1 : Logic Synthesis<br>
Step2 : FloorPlanning<br>
Step3 : Placement<br>
Step4 : CTS - Clock Tree Synthesis<br>
Step5 : Routing<br>
Step6 : Static timing Analysis<br>
![image48](https://github.com/vamsi-2312/pes_pd/assets/142248038/5c2152bd-47ab-4259-ad53-c848480ea2e2)

![image49](https://github.com/vamsi-2312/pes_pd/assets/142248038/2caaff64-6882-4e22-b49f-5bbddd29f291)

One common thing across all the stages are Gates and cells.<br>

Placement occurs in 2 step - Global Placement and Detailed Placement.<br>
In openlane<br>
```
run_placement
```
![image50dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/29a6f99f-b1e7-4886-b12b-f43f5db9cc8f)

now to check our design after placement<br>
```
cd ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/16-09_17-39/results/placement
```
```
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```
![image51dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/e911f63b-1aef-4d26-9773-8a1f2a26dee9)

![image52dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/24ad2c4f-94dc-4763-b962-59949b4bb798)

## Cell design and characterisation flows

Cell Design Flow<br>
The Library contains all the cells and different flavors, different functionality, different sizes, Different threshold voltage, etc.<br>

The cell design flow is divided into 3 different part, inputs, design steps, outputs<br>
DRC and LVS Rules.<br>
![image53i](https://github.com/vamsi-2312/pes_pd/assets/142248038/4b4429a4-cf66-4b05-85a0-5bb602a0d88b)

![image53](https://github.com/vamsi-2312/pes_pd/assets/142248038/22203a12-3fe6-4c4f-b653-984a7bac698f)

there are many rules.<br>
SPICE Models<br>
![image54](https://github.com/vamsi-2312/pes_pd/assets/142248038/ca86486d-7d3a-4989-bf28-056f0dc3bca0)

Library & User-Defined Specs<br>
![image55](https://github.com/vamsi-2312/pes_pd/assets/142248038/036709bf-c434-4102-aef7-f1f5df84a571)

![image56](https://github.com/vamsi-2312/pes_pd/assets/142248038/09b00652-99c4-4093-8fb8-2f621f79e1b7)

![image57](https://github.com/vamsi-2312/pes_pd/assets/142248038/dbb0a5b8-d4c6-489c-ae47-bf12c09cfcfb)

![image58](https://github.com/vamsi-2312/pes_pd/assets/142248038/94f07b53-c116-43bf-88ab-810ff4b3bbfa)

![image59](https://github.com/vamsi-2312/pes_pd/assets/142248038/bc30febe-7b1f-401a-a68a-049247535528)

Circuit Design<br>
![image60](https://github.com/vamsi-2312/pes_pd/assets/142248038/cfae029c-983f-4b48-a2d5-8540dd2bfc36)

Layout Design<br>
![image61](https://github.com/vamsi-2312/pes_pd/assets/142248038/8c309861-41ea-4e91-ae7e-c5b77d04e4d9)

![image62](https://github.com/vamsi-2312/pes_pd/assets/142248038/5b178e42-0778-4b91-b580-cf713fe0b7ff)

![image63](https://github.com/vamsi-2312/pes_pd/assets/142248038/68db6ed1-5d2e-4b6c-9f79-bfb8ec4a89e0)

![image64](https://github.com/vamsi-2312/pes_pd/assets/142248038/05272e31-b1a3-49bd-9a62-999256a4d302)

Characterisation<br>
We have the layout<br>
![image65](https://github.com/vamsi-2312/pes_pd/assets/142248038/1002d277-0eef-4ffb-ba5e-50a540562a49)

We have the descripition of the layout in form of ciruits.<br>
![image66](https://github.com/vamsi-2312/pes_pd/assets/142248038/90cefa74-6940-4e08-a562-f20008c97331)

Now, we have extracted all that into a spice netlist.(these are the inputs available to us)<br>
![image67](https://github.com/vamsi-2312/pes_pd/assets/142248038/5da5c94a-9f8b-4743-800b-1787716e8790)

1. We need to read the model files.
2. Read the extracted spice netlist
3. Recognise the Behaviour of the circuit.
4. Read the Subcircuits of the circuit.
5. Attach the necessary power supply.
6. Apply the Stimulus.
7. Provide the necessary capacitors.
8. Provide the necessary similation commands.

Next we need to give all the inputs from 1-8 in the form of configuration file to the **characterization software called GUNA**.<br>
The output of GUNA is timing,noise,power,.lib,function<br>

Classification of .lib<br>
1. Timing Characterisation
2. Power Characterisation
3. Noise characterisation

## General timing characterisation parameters

**Timing Characterisation**
![image68](https://github.com/vamsi-2312/pes_pd/assets/142248038/374af282-3ef7-4d5c-8cb8-7aaf78450ef8)

![image69](https://github.com/vamsi-2312/pes_pd/assets/142248038/ee89c13c-0ceb-4e15-9acf-9ae652591273)

![image70](https://github.com/vamsi-2312/pes_pd/assets/142248038/ae89f5b7-36e3-4314-ae0b-952ea3a89ed9)


**Propagation Delay**
Propagation Delay = time(out_fall_thr) - time(in_rise_thr)<br>
![image71](https://github.com/vamsi-2312/pes_pd/assets/142248038/965e93a8-bac3-42bd-8819-b8e3112b79d2)

![image72](https://github.com/vamsi-2312/pes_pd/assets/142248038/536a317d-c19d-41a7-adf3-4c450cd51d8f)

![image73](https://github.com/vamsi-2312/pes_pd/assets/142248038/be73d9a3-bfeb-48d6-86c6-b3920c8379ac)

![image74](https://github.com/vamsi-2312/pes_pd/assets/142248038/1ea5994b-4e5b-43eb-85bd-95b94fda4400)

Therefore while designing the cicuit we need to take care of the Design delays and thresholds.<br>

**Transistion time**
Transistion time = time(slew_high_fall_thr) - time(slew_low_fall_thr)<br>
![image75](https://github.com/vamsi-2312/pes_pd/assets/142248038/a86db6d8-45ba-430a-b2a8-3f9e21ca2372)

</details>
