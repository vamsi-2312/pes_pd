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

<details>
<summary> Week 3 -> Day 3 </summary><br>

## Contents of Day 3
+ Labs for CMOS inverter ngspice simulations.
+ Inception of Layout CMOS fabrication process.
+ sky130 Tech file Labs

## Labs for CMOS inverter ngspice simulations

### IO Placer

open terminal<br>
start openlane<br>
select the picorv32a<br>
```
run_synthesis
```
```
run_floorplan
```
then in new terminal<br>
```
cd ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/17-09_08-49/results/floorplan
```
```
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
```
![image1dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/d0a449eb-2903-4e46-a213-50a7f2d1893d)

we can observe that the input and output ports are placed uniformaly.<br>

In the floorplan.tcl file<br>
![image2dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/89c188f3-92ba-4d17-90bc-b06b171a78e9)

```
set ::env(FP_IO_MODE) 2
```
```
run_floorplan
```
![image3dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/afeab1fa-a815-4493-8dbe-ebfb89938fb2)

```
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
```
![image4dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/13ed05ad-dc45-4efb-9be7-999007995975)

now we can see that the ports arent placed equidistantly.<br>

### Spice deck creation for CMOS inverter

**VTC - SPICE simulations**<br>

First we need to create a spice deck.<br>
Spice deck -Contains the connectivity information, inputs that has to be given to the simulation, tap points.<br>

1. Component Connectivity
2. Component values.<br>
(ideally pmos must be 2-3 times bigger than nmos)
3. Identify nodes.
4. Name nodes. 

![image5](https://github.com/vamsi-2312/pes_pd/assets/142248038/1dca6d63-81ba-4a4a-bb8b-0e393ea9fc50)


Lets start with writing the spice deck.<br>
![image6](https://github.com/vamsi-2312/pes_pd/assets/142248038/c8c9d22c-facf-4dfc-ba21-9c9257ccf96c)

![image7](https://github.com/vamsi-2312/pes_pd/assets/142248038/ed7ed5c7-2587-4e98-9c35-3a1ccb859762)

**Spice Waveforms**<br>
![image8](https://github.com/vamsi-2312/pes_pd/assets/142248038/7315295a-1612-4706-8b9e-4119b612a767)

![image9](https://github.com/vamsi-2312/pes_pd/assets/142248038/52fd81c3-0c37-40f3-9cd2-5d62a5a60a76)

![image10](https://github.com/vamsi-2312/pes_pd/assets/142248038/df54e6f5-2222-41d0-85ce-953396cb99b3)


**Switching Threshold Vm**<br>
The shapes of the waveforms are same.<br>
The characterisation of the cmos inverter is maintained same.<br>

**Static Behavior Evaluation** : CMOS inverter Robustness<br>
1. switching threshold(Vm) is the point at which the the device switches.<br>
Vm is the point where Vin = Vout<br>
![image11](https://github.com/vamsi-2312/pes_pd/assets/142248038/4b464048-14ac-475f-9db7-15196b3b4044)

![image12](https://github.com/vamsi-2312/pes_pd/assets/142248038/d55a30b9-6b9b-4b59-8def-e9a768e64766)

![image13](https://github.com/vamsi-2312/pes_pd/assets/142248038/c2f5fe22-8903-41c0-a3ac-158d5452669c)

![image14](https://github.com/vamsi-2312/pes_pd/assets/142248038/7128899f-a7ec-42f3-888e-66cb87ee95f7)

![image15](https://github.com/vamsi-2312/pes_pd/assets/142248038/f1cb8761-3f42-4a93-90f6-173ca87b923a)

**Git cloning vsdstdcelldesign**
```

git clone https://github.com/nickson-jose/vsdstdcelldesign.git
```
```
cd ~/Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign
```
We can see that there a new folder being created in openlane file, and it is containing the inverter .mag file.<br>

Before we open the .mag file we need to have the .tech file.<br>
![image16dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/3926094b-dcb8-4f8b-9c4a-90403437a6e6)

We need to copy this .tech file into vsdstadcelldesign folder.<br>
```
cp sky130A.tech /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign/
```
![image17dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/7f937a5f-dafd-4db2-9df9-619aa9823d3c)

```
cd ~/Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign
```
```
magic -T sky130A.tech sky130_inv.mag &
```
![image18dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/2d60a5a3-9558-4a9b-a45f-714956558b58)

## Inception of Layout CMOS fabrication process

**Create Active Region**
Lets begin with 16-mask CMOS process
1. Selecting a Substrate.<br>
Ptype, high resistivity, doping level, orientation
2. Creating an Active region for transistors.
3. Formation of N and P well.
4. Foormation of Gate terminals.

Mask 1<br>
![image19](https://github.com/vamsi-2312/pes_pd/assets/142248038/405f6ea1-a083-4725-b95e-1a5134dd08b3)

![image20](https://github.com/vamsi-2312/pes_pd/assets/142248038/c05faab0-ef3b-438e-a34d-f35062b39a4c)

![image21](https://github.com/vamsi-2312/pes_pd/assets/142248038/524be500-39da-4b30-a455-45c2cd64bd5f)

![image22](https://github.com/vamsi-2312/pes_pd/assets/142248038/0a29d004-2ee3-4f28-ba83-673b7a9e330b)

![image23](https://github.com/vamsi-2312/pes_pd/assets/142248038/226fd508-0cfb-480e-987d-8ab9c0987970)

![image24](https://github.com/vamsi-2312/pes_pd/assets/142248038/3066a48f-b32e-4f2d-b755-f6921bf75217)

Field Oxides is grown, This process is called "LOCOS" - Local Oxidation of Silicon.<br>
![image25](https://github.com/vamsi-2312/pes_pd/assets/142248038/c509c8b4-edc8-4c8b-a782-8a81ede73ae9)

![image26](https://github.com/vamsi-2312/pes_pd/assets/142248038/aaeafe64-58aa-416b-af72-7001a0f7bf8d)

**N well and P well formation**
Desposite Photoresist and mask 2<br>
![image27](https://github.com/vamsi-2312/pes_pd/assets/142248038/a38ec257-2a08-4522-bbbb-97000a7f1c3f)

creating the P well<br>
![image28](https://github.com/vamsi-2312/pes_pd/assets/142248038/b97526a8-9aec-4a56-91e3-9deaac90efce)

Creating the N well<br>
![image29](https://github.com/vamsi-2312/pes_pd/assets/142248038/81668252-d3b0-480e-a78a-0c8f6e956e12)

Next we need to take into High Temperature furnace which will drive-in diffusion.<br>
![image30](https://github.com/vamsi-2312/pes_pd/assets/142248038/8894b190-b312-4688-9639-0369fc6eff10)

And this process is call Twin tub Process.<br>
![image31](https://github.com/vamsi-2312/pes_pd/assets/142248038/dd0260c0-933b-4324-86ee-e3d6371fda51)

**Formation og Gate**
Fabrication of the gate terminal is very important.<br>
We try to maintain the doping voltage and oxide capaitance, as they control threshold voltage.<br>

![image32](https://github.com/vamsi-2312/pes_pd/assets/142248038/f8e466dd-4b13-4625-a795-0533ffe07283)

![image33](https://github.com/vamsi-2312/pes_pd/assets/142248038/70985f31-a870-4952-8d02-7c174812771f)

the  the original oxide is etched/stripped using dilute hydrfluric(HF) solution<br>
![image34](https://github.com/vamsi-2312/pes_pd/assets/142248038/edd22340-19ae-4f5e-b274-a8f8c1f14bca)

Then we can re-grow the oxide layer which of high quality.<br>
Next, deposition of polysilicon layer using CVD(chemical vapor decomposition) method<br>
![image35](https://github.com/vamsi-2312/pes_pd/assets/142248038/750e8c9c-332f-47a8-8b4b-2900eb66755f)

Then again photoresist, and mask 6 for gate terminals.<br>
![image36](https://github.com/vamsi-2312/pes_pd/assets/142248038/ad032bc2-b743-4892-b6fa-574d1683549e)

Etch exposed area, then we get our terminals.<br>
![image37](https://github.com/vamsi-2312/pes_pd/assets/142248038/9e3936ad-683b-4fad-89ba-195dd8a36da2)

**Lightly doped drain(LDD) formation**
Why do we need this doping?<br>
* Hot electron effect - High nergy crrier break Si-Si bonds 3.2eV barrier between Si condution band ans SiO2 conduction band.
* Short channel Effect - When we go for smaller length mos, then drain field penertrates channel.

Create Mask 7, and create the nmos(doped with N-) in the p well.<br>
![image38](https://github.com/vamsi-2312/pes_pd/assets/142248038/948aad83-7c07-4694-b3a9-416f294cb2cd)

Similarly Mask8, and create the pmos(doped with P-) in the n well.<br>
![image39](https://github.com/vamsi-2312/pes_pd/assets/142248038/0ddd8aba-373e-47c8-b40a-ecb5360425df)

Then deposite thich SiO2, after Plasma anisotropic etchiping.<br>
![image40](https://github.com/vamsi-2312/pes_pd/assets/142248038/189a32a6-d502-4801-8c8f-268753f9f273)

we get side wall spacers.<br>

**Source and Drain Formation**
Apply Thin screen oxide is grown to aoid channeling during implantation.<br>
Then doping, in p well we get N+ doped region.<br>
![image41](https://github.com/vamsi-2312/pes_pd/assets/142248038/6a3d9520-6baf-4e3b-90ad-45ed8b7efedd)

Then doping, in n well we get P+ doped region.<br>
![image42](https://github.com/vamsi-2312/pes_pd/assets/142248038/704800d4-7f70-4097-8c5c-4c471460d6af)


![image43](https://github.com/vamsi-2312/pes_pd/assets/142248038/5c497f96-8a74-449c-9760-d0dfc2fa08ee)

Then put them into high tempertaure furnace, which will push the inpurities inside, and the source and drain are formed.<br>
![image44](https://github.com/vamsi-2312/pes_pd/assets/142248038/03953ce5-04cc-4226-960a-cf55e7023c46)

**Building the contacts and interconnects**

First we need to remove the thhin oxide using HF solution.<br>
Then deposite titanium on wafer surface, using sputtering.<br>
![image45](https://github.com/vamsi-2312/pes_pd/assets/142248038/f3d3d7c0-0d4d-4e1b-a227-d8ba0091ed00)

![image46](https://github.com/vamsi-2312/pes_pd/assets/142248038/5e7f7c2f-4ee9-4dc8-9ad3-d7eaf805922e)

Then heat the wafer.<br>
![image47](https://github.com/vamsi-2312/pes_pd/assets/142248038/7b806772-75c1-4eec-8f8f-cb293398c5a4)

Low resistant TiSi2 is formed.<br>
There is another reaction happening, TiN is formed which is used for local communication.<br>
![image48](https://github.com/vamsi-2312/pes_pd/assets/142248038/3b7bdf7c-b189-4959-b82d-f6a0328ab280)

Then unwanted TiN layer is etched away using RCA cleaning.<br>
![image49](https://github.com/vamsi-2312/pes_pd/assets/142248038/201d6bff-01dd-409a-8d63-22a5145fea61)

![image50](https://github.com/vamsi-2312/pes_pd/assets/142248038/68a5beb1-4e36-4054-a108-6626db64b2d3)

![image51](https://github.com/vamsi-2312/pes_pd/assets/142248038/4cf17a1b-869a-46e1-b33d-49eeae9c0fa1)

**Higher level Metal Formation**
SiO2 is deposited on wafer<br>
![image52](https://github.com/vamsi-2312/pes_pd/assets/142248038/15c8d551-0c70-4d13-82a9-6ef3a27cf772)

Chemical Mechanical polishing<br>
![image53](https://github.com/vamsi-2312/pes_pd/assets/142248038/61b7330b-e0a7-4c5e-b8ec-5acf83de03a7)

Making Contacts<br>
![image54](https://github.com/vamsi-2312/pes_pd/assets/142248038/8e9587c0-b9bb-472d-8dbb-5a4552c2d0a5)

![image55](https://github.com/vamsi-2312/pes_pd/assets/142248038/dfe5b777-e1cc-460d-a8d7-df1fbbb060e9)

Deposite Thin TiN and then lanket Tungsten layer.<br>
![image56](https://github.com/vamsi-2312/pes_pd/assets/142248038/de45f354-d28c-44d0-a348-4856af606c3d)

then CMP<br>
![image57](https://github.com/vamsi-2312/pes_pd/assets/142248038/de90d411-b7a8-4c2a-b466-8167a17b7152)

Deposite Al layer, then Mask 13<br>
![image58](https://github.com/vamsi-2312/pes_pd/assets/142248038/b26b4dfe-5f6e-4440-a980-b219327ed655)

then again to define the contact hole, mask 14<br>
![image59](https://github.com/vamsi-2312/pes_pd/assets/142248038/6137f22e-1808-40e6-b7bb-49f4278a9bd0)

mask 15<br>
![image60](https://github.com/vamsi-2312/pes_pd/assets/142248038/b428e158-d983-429a-afe4-494c963bb094)

Then the last level is to deposite dielectric Si3N4 to protect the chip<br>
![image61](https://github.com/vamsi-2312/pes_pd/assets/142248038/32f7767a-aa34-4e6c-a250-94add80a15a0)

finally<br>
![image62](https://github.com/vamsi-2312/pes_pd/assets/142248038/eaf2ce6b-b301-43ea-9ca0-d2f057d1b1a8)


**Lab introduction to sky130 basic layers layout ns LEF usinf inverter**

![image63dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/a7f1e7c6-b73d-4547-931a-6af7ac9bfd43)

red - polysilicon <br>
green - n diffusion<br>
peach - p diffusion<br>
blue - metal<br>
![image64dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/9ebca447-3276-4624-abec-460f7c5155b7)

![image65dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/a1b188bf-4985-4e6a-9558-43590bde45b0)

drains connected to output y<br>
![image66dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/d0bb1177-db18-4b76-b2ca-1f2f10d8c055)

vdd connection<br>
![image67dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/cd674e25-ca1c-44c8-a80d-ee04f35b4170)

gnd connection<br>
![image68dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/34e7ff59-dc48-448b-b6b6-85f94abbc00c)

LEF is on the right it contains the meatal connection(pr boundaries and ports)<br>
![image69](https://github.com/vamsi-2312/pes_pd/assets/142248038/c924e728-4563-4e81-9568-f8ff91f5e075)


**Lab steps to create std cell layout and extract spice netlist**

For a detailed procedure, on how to crete a standard cell visit hhtps://github.com/nickson-jose/vsdstdcelldesign<br>

Extracting infromation into spice<br>
In magic terminal<br>
```
extact all
```
![image70dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/f1e654d7-79d6-41c2-bb67-e81ecf1cf18c)

![image71dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/cc263c40-8b7a-467e-9e31-4c3c363f493a)

![image72dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/eafe13c6-49ec-42a2-9b03-c9a28d4da3ca)

## Sky130 Tech file Labs

![image73dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/71fcfb5d-812c-4ef2-8f1f-cff3c502b733)

![image74dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/76baddcc-e04a-4696-81e9-5a4c17cea8fe)

![image75dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/ce0f59a2-7055-41ca-ad95-d0d0806083f6)


![image76dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/77e32990-2aca-46f3-bba4-319c74b8e722)

rise time = 80% of rise - 20% of rise = (2.8906 - 2.6491)*1E-9<br>
![image77dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/b1b1c976-6f54-4fa7-94af-52087b6e54f2)

fall time = 20% of fall - 80% of fall = (0.02664)*1E-9<br>
![image78dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/d395e964-4b42-48a5-bb87-fabfeb42d309)

Cell rise delay = 50% of output - 50% of input = (0.005324)*1E-9<br>
![image79ell](https://github.com/vamsi-2312/pes_pd/assets/142248038/97bf1eee-0f95-46a0-b231-ad9f76d159af)

Cell fall delay = 50% of output - 50% of input = (0.07542)*1E-9<br>

Later, we are going to use layout and create LEF file.<br>

**Magic DRC**<br>
we can refer to this webpage opencircuitdesign.com/magic/<br>
CIF Ouput Section<br>
![image80dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/f685e304-74cb-41a8-907e-ffde8886cc6b)

![image80idell](https://github.com/vamsi-2312/pes_pd/assets/142248038/3b77c0a2-3d09-4206-96fb-a401a86f5ab9)

DRC Section<br>
![image81dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/cba3aed0-b76e-4610-878a-7c026be4d779)


Basic DRC rules are Edge based rules.<br>
There are rules that are not edge based such as area,etc.<br>

We are using Google's Skywater 130nm technology.<br>
https://www.skywatertechnology.com/technology-and-design-enablement/<br>
Documentation in github.<br>
https://github.com/google/skywater-pdk<br>

To downoad the examples and .tech file<br>
search this is google, it will download automatically<br>
```
opencircuitdesign.com/open_pdks/archive/drc_tests.tdz
```

in terminal, to launch magic<br>
```
magic
```
Open met3.mag file<br>
we can move to console from layout window by pressing colon.<br>
to find out what the drc error is, in console type<br>
```
drc why
```
![image82dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/47179920-4417-46fb-8860-eee8e8f6719c)

![image83dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/6c4fb692-06e5-4ff5-88f7-9a0f0e806439)


select an area, to see the contacts<br>
```
cif see VIA2
```
![image84](https://github.com/vamsi-2312/pes_pd/assets/142248038/5eedad68-793b-4169-940c-6c32a5996732)

to see the dimensions of any area, select it.<br>
then type `box` in console.<br>
to perform drc<br>
```
drc check
``` 
![image85dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/fdaac6be-005c-4725-9ee9-3af4f85106c2)

![image86dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/15de9d91-13df-4bfb-8fce-b1eb2fa94a50)

![image87dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/c891b0f0-e67d-4ce5-9eae-e8aed65d0a27)

updating the new .tech file<br>
![image88dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/10d9c461-3318-43ae-b249-357608753fcb)

![image89dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/faa0c356-6396-4170-9dce-9dbd89e79222)

![image90dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/5528f20b-50c5-4bb4-8f83-14756edf0960)

we can see that the resistor drc error are fixed.<br>

![image91dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/b234d39e-3277-4fd0-a049-4fb14a68b029)

![image92dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/47c83b4f-73c6-4ff6-8218-1ef78160916a)

![image93dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/0651de48-ed44-49fb-8d41-7ebe1dfd70e1)

![image94dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/0d807a0d-285d-4440-b14d-6a1edc930cda)

![image95dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/bcb28412-16d3-42e5-875d-aeee9caacda4)

![image96dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/147fba26-8d98-406a-8eb7-0d4d0f294598)
the drc has been resolved after putting anthor layer<br>

![image97dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/97003267-9e06-43e6-886b-c100f3483f30)

</details>

<details>
<summary> Week 3 -> Day 4 </summary><br>

## Contents of Day 4
+ Timing modeling using delays.
+ Timing analysis with ideal clocks using openSTA
+ Clock tree synthesis TritonCTS and signal integrity.
+ Timing analysis with real clocks using openTA

### Timing modeling using delay tables

** Lab to convert grid info t track info**<br>
Extract the layout into a LEF file. <br>

```
cd ~/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/openlane/sky130_fd_sc_hd
```
```
less tracks.info
```
![image1dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/778f505f-1a09-4708-a655-b0819ee63a47)

in our layout<br>
press g<br>
we can see a grid
![image2dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/760b59ce-33f0-4724-b51a-353859398286)

after making our grid
by executing the below command in magic console
  
```
grid 0.46um 0.34um 0.23um 0.17um
```
![image3dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/0c6e512f-ed2d-4784-bd54-024023c34868)

the width of the standard cell must be in odd multiples of x pitch.
![image4dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/53f8f8fa-0ce0-410d-8921-b5f77a4c4f72)

we can there are 2 full boxes and 2 half boxes being used for the ports.

same way we need for height also.
![image5dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/4cf46473-1500-4030-9789-7f91ef3094d0)

1 and half boxes being used.

how to name any port.
![image6dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/980cf1a3-dbe2-4a49-8ce9-06e99148070b)

![image7dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/6c6c1caa-63f2-4fbe-bb9c-8f8e2ac97d62)

save the file as sky130_vsdinv.mag

```
save sky130_vsdinv.mag
```

to make lef file
```
lef write
```
![image8dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/2b4868c2-a14f-45c1-b6ab-82b5f25c04de)

![image9dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/469e2ea5-4c31-496a-9454-571d1b6e3a90)

now we have our lef file ready
we need to put it into picorv32a

next copying our lef file into this destination ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src

![image10dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/2aaa6019-d55a-41f8-b828-72e90737d42c)

![image11dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/ae18a42b-93c5-45ed-ac0a-c55d3e7ab2e0)

![image12dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/50f34329-5c92-482d-8ea7-ab1939704854)

```
cd ~/Desktop/work/tools/openlane_working_dir/openlane
```
```
docker
```
```
./flow.tcl -interactive
```
```
package require openlane 0.9
```
```
prep -design picorv32a -tag 16-09_17-39 -overwrite
```
```
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
 
add_lefs -src $lefs
```
```
run_synthesis
```
It is getting violated.

**Introdunction to delay tables**<br>
for and gate, enable pin is 1
for or gate, enable pin is 0
![image4](https://github.com/vamsi-2312/pes_pd/assets/142248038/6e12e75a-013f-4019-a0e9-d9094181233f)

spliting the load into 2 buffers and then 1 buffer
![image5](https://github.com/vamsi-2312/pes_pd/assets/142248038/d0712464-8039-41d7-9b20-15c65181f217)

assumption
![image6](https://github.com/vamsi-2312/pes_pd/assets/142248038/3296a4d0-4654-4ca2-9ac7-937e275c7d03)

observation
![image7](https://github.com/vamsi-2312/pes_pd/assets/142248038/914eb61f-1854-4e8e-9b6c-8370ec72d87c)

the capcitance load at output node of each buffer is varying.
Delay tables - representation of delays
![image8](https://github.com/vamsi-2312/pes_pd/assets/142248038/48992324-85f3-457e-b55c-9b710ca20c17)

![image9](https://github.com/vamsi-2312/pes_pd/assets/142248038/e16b3931-19f5-4842-ba75-cd325750f727)

if next input capcitance is in between a range then we need extrpolate.
![image10](https://github.com/vamsi-2312/pes_pd/assets/142248038/ddbad1d0-ca77-40a1-953a-e7d1f3c69aca)

the delay for flip flop would be x9' + y15
![image11](https://github.com/vamsi-2312/pes_pd/assets/142248038/a0644b09-fdf4-413a-9f30-95f908e85eb5)

skew = 0
if there was different delays then skew would have some value
Skew is the time delta between the actual and expected arrival time of a clock signal

coming back to solve our issue in violation of run_synthesis
![image13dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/3cacb300-9139-4fbd-bb98-df5fdda7f226)

![image14dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/e26ebc3b-6b6c-4c55-a2d5-7a5a5b18d1d8)

![image15dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/9fc87005-64f4-4e4f-8afe-1f47beb6e1d4)

```
init_floorplan
```
```
run_placement
```
```
cd ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/16-09_17-39/results/placement
```
```
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```
![image16dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/bcbff8d2-e935-446d-862c-7015f34c1510)

![image17dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/8d0a58fc-bfc1-4763-bdc4-1891c04cba50)

**sky130_vsdinv _14086_**
![image18dell](https://github.com/vamsi-2312/pes_pd/assets/142248038/fea4dfc8-a664-4145-857a-0c8a59b44aa8)

### Timing analysis with ideal clocks using openSTA

![image19](https://github.com/vamsi-2312/pes_pd/assets/142248038/ef1d1541-0bb4-447c-9b70-379f73bb2552)

![image20](https://github.com/vamsi-2312/pes_pd/assets/142248038/fdc7afa9-f83c-4a1b-8116-839628c3f524)

![image21](https://github.com/vamsi-2312/pes_pd/assets/142248038/3d139c40-d1b6-4683-aaae-e945ef9e7035)

Setup time: Minimum time data must be stable before the clock edge to guarantee correct flip-flop operation.

Hold time: Minimum time data must remain stable after the clock edge to ensure reliable flip-flop operation.
jitter - in yellow
![image22](https://github.com/vamsi-2312/pes_pd/assets/142248038/5bcb9f02-abd9-4b0d-9b56-41a491560f44)

![image23](https://github.com/vamsi-2312/pes_pd/assets/142248038/f08f4ad2-cef1-46ba-aa9f-7062a43c6949)

![image24](https://github.com/vamsi-2312/pes_pd/assets/142248038/edfbe86b-dd14-4d2a-ac89-11909fb88e31)

![image25](https://github.com/vamsi-2312/pes_pd/assets/142248038/f6cef1ff-d725-4e0b-9fab-186426ea5524)

create two file one is pre_sra.conf and my_base.sdc
save the first file in this loaction ~/Desktop/work/tools/openlane_working_dir/openlane
the second file in this location ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src

<image26dell>
<image27dell>
After setting env(SYNTH_MAX_FANOUT) = 4
<image28dell>
the violation is reduced
By upsizing the slack is reduced.
<image29dell>

### Clock tree synthesis TritonCTS and signal integrity
We should ideally get skew = 0
<image30>
Clock tree synthesis (CTS) is a crucial step in digital integrated circuit design. It optimizes clock distribution, minimizing skew and jitter, ensuring synchronous operation, and enhancing overall chip performance, critical for modern high-speed electronics.

We are installing buffer, so that the signal is sent properly.
<image31>

Clock net shielding employs techniques like differential signaling, ground planes, and shielding layers to minimize electromagnetic interference and crosstalk in high-frequency clock signals. This enhances signal integrity and reduces the risk of timing errors in complex electronic systems.
<image32>

Crosstalk-induced delta delay or skew can disrupt signal timing in digital circuits, causing errors and reducing performance. It results from unwanted coupling between adjacent signals, introducing unpredictable delays that can lead to data corruption and functional failures, necessitating careful signal integrity analysis and mitigation techniques.
<image33>

to run CTS
in openlane
```
run_cts
```
<image34dell>
<image35dell>
<image36dell>

### Timing analysis with real clocks using openSTA

Refer Hold time and Setup time definition above.

Doing Timing analysis with real clocks
<image37>
<image38>
setup time slack
<image39>
hold time slack
<image40>
<image41>

start openlane
```
docker
```
```
./flow.tcl -interactive
```
```
package require openlane 0.9
```
```
prep -design picorv32a -tag 16-09_17-39 -overwrite
```
```
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
 
add_lefs -src $lefs
```
```
run_synthesis
```
```
init_floorplan
```
```
run_placement
```
```
run_cts
```
<image43dell>
<image44dell>

```
openroad
```
<image42dell>

reading the .lef file
```
read_lef /openLANE_flow/designs/picorv32a/runs/16-09_17-39/tmp/merged.lef
```
<image45dell>
reading the .def file

```
read_def /openLANE_flow/designs/picorv32a/runs/16-09_17-39/results/cts/picorv32a.cts.def
```
<image46dell>

```
write_db pico_cts.db
```
```
read_db pico_cts.db
```
```
read_verilog /openLANE_flow/designs/picorv32a/runs/16-09_17-39/results/synthesis/picorv32a.synthesis_cts.v
```
<image47dell>

```
read_liberty -max $::env(LIB_SLOWEST)
```
```
read_liberty -max $::env(LIB_FASTEST)
```
<image48dell>

```
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc
```
<image49dell>

```
set_propagated_clock [all_clocks]
```
```
report_checks -path_delay min_max -format full_clock_expanded -digits 4
```
hold slack
<image50adell>
setup slack
<image50dell>
<image51del>

</details>
