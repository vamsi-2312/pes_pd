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

How to come up with the Width and Height of the Core and Die
<image 1>

we will start with basic netlist
<image2>
contains flipflops, and gate, or gate

we are mostly intreseted in the dimensions of the standard cells.

Lets start with rough dimensions of Standard cells and Flip flops as 1unit x 1unit, area = 1sq. unit
<image 3>

lets calculate the area occupied by the netlist on a silicon wafer.
arranging the cells and flip flops
<image4>

What is the core and die of the chip?
A die which consists of core, is smallsemiconductor material specimen on which the fundamental circuit is fabricted.
We imprint the die multiple times in the chip.
<image5>

The netlist occuping 4sq. units in placed inside the core.
In this case we are at 100% utilization of the core area, because the logial cells occupies the complete are of the core.
<image6>
Utilization Factor = (Area Occupied by netlist)/(Total Area of the Core)
Utilization factor = 1

Usually we design with utilization factor of 0.5, 0.6

Aspect Ratio = Height/Width
Aspect Ratio = 1(square chip)

If the aspect ratio is other than 1, it means that the chip is in rectangular shape.

lets take another example,
<image7>
utilization factor = 0.5 (only 50% is being used, 50% is free)
aspect ratio = 0.5 (rectangle chip)

<image8>
utilization factor = 0.25
aspect ratio = 1 (sqaure chip)

Next step is Define the Locations of Perplaced cells.
What are preplaced cells - Preplaced cells in semiconductor design are manually positioned blocks on an integrated circuit chip. Unlike standard cells, they offer custom functionality, with fixed placements to optimize chip performance, power, and connectivity. Designers strategically place them to meet specific design requirements and ensure overall chip functionality.

<image9>
1. combinational logic
2. Cut into 2 halves
3. Put each half in one block and connect them.
4. Black box the boxs
5. Seperate the Black boxex as two different IP's or modules.
Then we can use this modules multiple times, rather than wrting everything.
<image10>

Similary there are other IP's also available
<image11>

The arrangement of these IP's in a chip is refered as `FloorPlanning`.
These IP's/blocks have user-defined loations, and hence are placed in chip before automated placement and routing are called as pre-placed cells.
Automated placement and routing tools places the remaining logical cells in the design onto chip.

Once these Preplaced cells are fixed, they arent going to be changed.

Preplaced cells are placed nearer to the input side, and their locations are going to changed.
Next we need to surround the preplaced cells with decoupling capacitors.

To prevent the delay in charging and discharging of the capacitor by the voltge source which is far away, we use decoupling capacitors which is completed filled with charge to voltage source. we call it decoupling capacitor because it decouples the circuit from the main supply. now there will be no drop in votage.
<image12>
<image13>
Placing the preplaced cells and decoupling capacitors.
<image14>

Next step is Power Planning.
We need to transfer the value long the red line.
Lets assume the read line is a 16-bit bus and i connected to an inverter.
<image15>
At once all the ones are made zero, and zeros are made ones, due to this there is bump in the ground tap point as all 16-bit are connected to the same ground.
<image16>
The phenomenon is called ground bounce and it will eventually settle down.
If the capacitors are charging from low to high, there is a Voltage drop in the Supply Voltage.
<image17>
This issue is coming because we are having only one power supply, it was having multiple power supplies we would have this issue. Now we are going to have multiple power supplies.
<image18>
It is called as mesh.
<image19>

Next step is Pin Placement.
lets take an example
<image20>
<image21>
the complete design
<image22>

The connectivity informtion beteen the gates is codes using VHDL and is called as the Netlist.

Usually we put all input ports in the left and all output ports in the right.
The ordering the ports are random.
<image23>

We have created bigger path for clks than inputs to prevent any resistance the flow of signal.
And in the remaining place in between the core and die we put logical cell placement blockage to prevent the automated and routing tool doesnt place any cells in this area.
<image24>

Next, Floorplan is ready for placement and routing.
open terminal
```
cd ~/Desktop/work/tools/openlane_working_dir/openlane/configuration
```
```
ls -ltr
```
<image24aaadell>
```
cat README.md
```
<image25dell>
<image26dell>
similary we have placement, CTS, routing, etc.
<image27dell>

open new terminl tab
```
cd ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a
```
<image28dell>

Start up openlane
```
run_synthesis
```
```
run_floorplan
```
<image29dell>
<image30dell>
<image31dell>
```
cd ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/16-09_17-39/results/floorplan
```
```
less picorv32a.floorplan.def
```
<image32dell>
```
cd ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/16-09_17-39/results/floorplan
```
```
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
```
<image33dell>
<image34dell>
<image35dell>
<image36dell>
Standard cells are present at the bottom left.
<image37dell>
<image38dell>

Next Step is Placement and Routing

##  Library Binding and Placement

Bind the netlist with physical cells
The nelist is containing the cells is represented as blocks which is the actual representation in the chip.
<image39>
Library - contain all the information about the cells.
It will also have different flavors of the same cells and use what we want based on the conditioin.
<image40>
The library also have the timing information of the cells.
Now we need to place these cells in our floorplan.
<image41>
Placing the cells.
<image42>
<image43>

OPtimize Placement
This is the stage where we estimate length and capacitance and, based on that, insert repreaters.
<image44>
<image45>
<image46>
<image47>

Need Characterisation
Library Characterisation and modelling
Every Design must go through if it wants to be implemented in a chip.
Step1 : Logic Synthesis
Step2 : FloorPlanning
Step3 : Placement
Step4 : CTS - Clock Tree Synthesis
Step5 : Routing
Step6 : Static timing Analysis
<image48>
<image49>

One common thing across all the stages are Gates and cells.

Placement occurs in 2 step - Global Placement and Detailed Placement.
In openlane
```
run_placement
```
<image50dell>
now to check our design after placement
```
cd ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/16-09_17-39/results/placement
```
```
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```
<image51dell>
<image52dell>

## Cell design and characterisation flows

Cell Design Flow
The Library contains all the cells and different flavors, different functionality, different sizes, Different threshold voltage, etc.

The cell design flow is divided into 3 different part, inputs, design steps, outputs
DRC and LVS Rules.
<image53i>
<image53>
there are many rules.
SPICE Models
<image54>
Library & User-Defined Specs
<image55>
<image56>
<image57>
<image58>
<image59>
Circuit Design
<image60>
Layout Design
<image61>
<image62>
<image63>
<image64>
Characterisation
We have the layout
<image65>
We have the descripition of the layout in form of ciruits.
<image66>
Now, we have extracted all that into a spice netlist.(these are the inputs available to us)
<image67>
1. We need to read the model files.
2. Read the extracted spice netlist
3. Recognise the Behaviour of the circuit.
4. Read the Subcircuits of the circuit.
5. Attach the necessary power supply.
6. Apply the Stimulus.
7. Provide the necessary capacitors.
8. Provide the necessary similation commands.

Next we need to give all the inputs from 1-8 in the form of configuration file to the **characterization software called GUNA**.
The output of GUNA is timing,noise,power,.lib,function

Classification of .lib
1. Timing Characterisation
2. Power Characterisation
3. Noise characterisation

## General timing characterisation parameters

**Timing Characterisation**
<image68>
<image69>
<image70>

**Propagation Delay**
Propagation Delay = time(out_fall_thr) - time(in_rise_thr)
<image71>
<image72>
<image73>
<image74>
Therefore while designing the cicuit we need to take care of the Design delays and thresholds.

**Transistion time**
Transistion time = time(slew_high_fall_thr) - time(slew_low_fall_thr)
<image75>

</details>
