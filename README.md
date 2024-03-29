# Advanced_Physical_Design
This file contains the information learnt during the [Advanced Physical Design](https://www.vlsisystemdesign.com/advanced-physical-design-using-openlane-sky130/) workshop done using picorv32 core. We perform a complete RTL2GDS Analysis using Openlane.

# Table of Contents
- [Introduction To RTL to GDSII flow](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#intoduction-to-rtl-to-gdsii-flow)
- [Open Source Tools used](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#open-source-tools-used)
- [Day 1: Inception of open-source EDA,OpenLANE and sky130 PDK](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#day-1-inception-of-open-source-edaopenlane-and-sky130-pdk)
   - [How to talk to computers](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#how-to-talk-to-computers) 
      -  [Intordution to die,core,pads](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#intordution-to-diecorepads)
      -  [Introduction to RISC-V](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#introduction-to-risc-v)
   -  [SOC Design and OpenLANE](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#soc-design-and-openlane)
      -   [Introduction to RTL2GDS flow](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#introduction-to-rtl2gds-flow) 
      -   [Introduction to OpenLANE](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#introduction-to-openlane)
   -  [Open-source EDA tools](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#open-source-eda-tools)
      -   [Initialisation of OpenLANE](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#initialisation-of-openlane)
      -   [Design Preperation Step](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#design-preperation-step)
      -   [Run Synthesis](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#run-synthesis)   
 - [Day 2: Good floorplan vs bad floorplan and introduction to library cells](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#day-2-good-floorplan-vs-bad-floorplan-and-introduction-to-library-cells)
   - [Chip Floor planning Consideration](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#chip-floor-planning-consideration)
      - [Utilization Factor and aspect Ratio](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#utilization-factor-and-aspect-ratio) 
      - [Pre-placed Cells and De-coupling Capacitors](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#pre-placed-cells-and-de-coupling-capacitors)
      - [Power Planning](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#power-planning)
      - [Pin Placement and Logical Cell Placement Blockage](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#pin-placement-and-logical-cell-placement-blockage)
    - [Library Binding and Placement](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#library-binding-and-placement)
      - [Placement](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#placement)
      - [Placement using OpenLANE](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#placement-using-openlane)
    - [Cell Design and Charecterization Flows](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#cell-design-and-charecterization-flows)
      - [Inputs](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#inputs)
      - [Design Steps](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#design-steps)
      - [Outputs](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#outputs)
      - [Characterization flow](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#characterization-flow) 
 - [Day 3: Design Cell Library using Magic Layour and ngspice characterization](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#day-3-design-cell-library-using-magic-layour-and-ngspice-characterization)
     - [Labs for CMOS inverter ngspice simulation](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#labs-for-cmos-inverter-ngspice-simulation)
     - [Create Standard Cell Layout and Extract SPICE Netlist](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#create-standard-cell-layout-and-extract-spice-netlist)
     - [Transient Analysis Using Ngspice](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#transient-analysis-using-ngspice)
 - [Day 4: Pre-layout Timing Analysis and Importance of Good Clock Tree](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#day-4-pre-layout-timing-analysis-and-importance-of-good-clock-tree)
   - [Steps to convert Grid Info to Track Info](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#steps-to-convert-grid-info-to-track-info)
   - [Steps to convert Magic layout to std cell LEF](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#steps-to-convert-magic-layout-to-std-cell-lef)
   - [Timing analysis with ideal clocks using openSTA](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#timing-analysis-with-ideal-clocks-using-opensta)
   - [Clock Tree Synthesis TritonCTS and signal integrity](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#clock-tree-synthesis-tritoncts-and-signal-integrity)
- [Day 5: Final steps for RTL2GDSII using tritonRoute and openSTA](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#day-5-final-steps-for-rtl2gdsii-using-tritonroute-and-opensta)
   - [Routing and DRC Rule Check](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#routing-and-drc-rule-check)
   - [Power Distribution Network and Routing](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#power-distribution-network-and-routing)
   
- [Acknowledgement](https://github.com/Shris7/Advanced_Physical_Design/blob/main/README.md#acknowledgement)


 # Intoduction To RTL to GDSII flow
 RTL to GDSII flow is the process of converting a RTL design that is, a register to transfer level that consists of synchronous digital blocks and signals between the hardware registers and the logical operations performed on these signals, to a GDSII design which is a database file. GDSII is the de facto industry standard for EDA data exchange for integrated circuits.
 A complete RTL to GDSII flow consists of the following steps:
 - Synthesis and STA
 - Floorplanning
 - PLacement
 - CTS
 - Routing
 - GDSII Streaming
 
 ![image](https://user-images.githubusercontent.com/92938137/182756972-cb19a8da-36d1-44ea-80c9-abe59fd562f8.png)

 # Open Source Tools Used
 OpenLANE uses various open source tools that include:
 - Yosys : synthesis of RTL
 - ABC : mapping netlist
 - Magic: layout
 - Netgen : SPICE exratraction and simulation
 - OpenSTA : Static timing analysis
 - OpenROAD : Floorplanning,Placement,CTS and routing
 
 # Day 1: Inception of open-source EDA,OpenLANE and sky130 PDK
 ## How to talk to computers
 ### Intordution to die,core,pads
 Before we start with the RTL2GDSII flow we must first familiarize ourselves with some terms.
 - Die : it is a block of semiconductor material on which a given circuit is fabricated.It surrounds the core.
 - Core : is the region in a chip where the logic of the design is placed.
 - Pad : are intermediate structures connecting the internal signals to the external pins of a chip package.
 ![image](https://user-images.githubusercontent.com/92938137/182757008-5a5db95e-518b-40ca-8d93-600c260f6c7b.png)

 ### Introduction to RISC-V
 RISC-V is a open source ISA that is free,easy and simple to use when compared to other ISAs such as ARM or intel-86. RISC-V processors are royality free and thus are very much cheaper too. Further more their Instruction Set has very few instructions which are easy to understand and use. Th basic format of RISC-V that can be implemented is RV32I -integer base which has only 47 instructions in total. More information about RISC-V is provided [here](https://github.com/Shris7/riscv_myth)
 
 ## SOC Design and OpenLANE
 ### Introduction to RTL2GDS flow
 All the pdks are present in the ```pdks/``` directory. 
 
![image](https://user-images.githubusercontent.com/92938137/182759376-8d1e21b1-8bf5-4983-b86c-1726d083e353.png)
![image](https://user-images.githubusercontent.com/92938137/182759422-e72ffdf5-8deb-4a15-adab-530fad25903c.png)

 ### Introduction to OpenLANE
 OpenLANE is a open source tool using which we can perfome a complete RTL to GDSII analysis. It compromises of various open soruce tools such as yosys,magic,netgen,fault, openROAD. The figure below describes the architecture of OpenLANE.
 
 ![image](https://user-images.githubusercontent.com/92938137/182760008-1ce00f18-20e4-4e08-9223-d0694ec9f2af.png)

More information can be obtained from [here](https://github.com/efabless/openlane)
 
 ## Open-source EDA tools
 ### Initialisation of OpenLANE
 OpenLANE can be invoked in linux using docker. We must do this everytime we want to invoke openLANE.This can be done in two ways:
 - ```docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) openlane:rc6```
 - ```docker```
 To invoke openLANE use ```./flow.tcl```
 Once invoked it can be used in interactive mode or autonomous mode.
 To use interactive mode uss ```-interactive``` flag with ```./flow.tcl```.
 
 ![image](https://user-images.githubusercontent.com/92938137/182760948-22e398ec-c3d0-416e-a645-b89dd6e509eb.png)

 ### Design Preperation Step
 After invoking OpenLANE we must import the package of the required version.This can be done useg the following command:
 ```package require openalne 0.9```
 The package version used is 0.9.
 We next have to prepare our design using the following command:
 ```prep -design <design-name>```.
 Here since we are working with picorv32a our design-name is picorv32a.
 
 ![image](https://user-images.githubusercontent.com/92938137/183097067-520aa347-741d-4bb2-94a0-3456fad2c120.png)

 ### Run Synthesis
Once the design preperation is done, our first step is to perform synthesis of the loaded design. This is done using the following command:
```run_synthesis```

![image](https://user-images.githubusercontent.com/92938137/182761642-0f2de8f8-9f2d-492d-b060-0dfd6a7806ee.png)
![image](https://user-images.githubusercontent.com/92938137/182761696-9ab9811d-3efd-4669-8251-48e6629cbf4b.png)
![image](https://user-images.githubusercontent.com/92938137/182761730-cc886b74-909e-4747-a194-5acf4c25c433.png)

- Task 1: Find the flop count.
Flop count = 0.108423 = 10.843%

- Static Report:

![image](https://user-images.githubusercontent.com/92938137/182761915-dc800564-52bc-4689-863c-9206f4d69349.png)
![image](https://user-images.githubusercontent.com/92938137/182761951-2ffe8b82-507f-42cd-992c-8586db4f6386.png)


# Day 2: Good floorplan vs bad floorplan and introduction to library cells
## Chip Floor planning Consideration
Floorplanning involves determining the shape,size and location of modules in a chip and also estimating the chip area,delay and thus providing a ground work for building a layout.
The modules are optimized in such a way that we can reduce the area occupied by them.

### Utilization Factor and aspect Ratio
Utilization factor is defined as the ratio of the area occupied by the netlist to the area of the core.Theoritically it is 1 or 100% utilization and practically it is 0.5/0.6 or 50%-60% utilization.
Aspect ratio is the ratio of height to width of the core.If aspect ratio is 1 it implies that our chip is square shaped.

### Pre-placed Cells and De-coupling Capacitors
Pre-placed cells are pre-defined cells or built-in cells. They can be macros or IPs.
The location of these cells depends on its connectivity with the netlist.These IPs have user-defined loactions and hence are placed in a chip before automated placement and routing and thus the name pre-placed cells.
De-coupling capacitors are responsible for charging/discharging the capacitors in the pre-placed cells completely.

### Power Planning
Power planning is mesh/grid kind of structure that is responsible for supplying power equally to the cells at any point in the cell or chip block.This takes care of the global communication in a chip. They ensure there is no sudden droop in the supply voltage or ground bounce.

### Pin Placement and Logical Cell Placement Blockage
Pin placement is the process of placing input or output pins in the space between the core and die.Different types of pin placement include high density placement and equidistant placement.
Logical cell placement blockage ensure no logical cell will be placed in the area between core and die.

### Floorplanning Using OpenLANE
Floorplanning in OpenLANE is done using the following command:
```run_floorplan```
The result of this is a ```def``` file.
![image](https://user-images.githubusercontent.com/92938137/182833333-f09be8af-ba55-432f-a6c0-5e5ebe1b7b9b.png)
![image](https://user-images.githubusercontent.com/92938137/182840953-616fb0c9-87d6-4e75-90f0-cb1c6cfe4c74.png)

### Review floorplan layout using Magic
To visualix=ze the layout after floorplan we use magic. We need three files:Tech file(```sky130A.tech```),Merged lef file(```merged.lef```) and the ```def``` file.

![image](https://user-images.githubusercontent.com/92938137/182842391-714a825f-166d-4ff7-9d5a-0843ce703873.png)
![image](https://user-images.githubusercontent.com/92938137/182842902-fedd5adb-79dc-4870-9a8a-a24d0aa3198a.png)

## Library Binding and Placement
### Placement
Once floorplanning is done,the next step is placement.Placement places the cells on the chip in the appropriate location. It optimizes the design therby removing any timing voilations present.

### Placement using OpenLANE
Placement is done using the command:
```run_placement```

Placement in OpenLANE occurs in 2 stages:
- Global Placement
- Detailed Placement

![image](https://user-images.githubusercontent.com/92938137/182850293-bacbe177-2ac6-48ea-a79b-42ba9d6d9818.png)
![image](https://user-images.githubusercontent.com/92938137/182850477-af131735-68cb-4974-86b3-a1df56ae54dd.png)
![image](https://user-images.githubusercontent.com/92938137/182850890-ca606e86-3902-413a-a709-df44f2831769.png)

## Cell Design and Characterization Flows
Cell design flow comprises of stages that provides entire flow for the design of standard cells.
Standard cells are present in a library and they have information of the different componenets,their functionality and sizes too. The sizes of a componenet refers to their drive strength.It also has information on different threshold voltage which inadvertly affect the speed of the component.
Cell Design flow has 3 typical steps:
- Inputs
- Design Steps
- Outputs

![image](https://user-images.githubusercontent.com/92938137/182854282-3538eef0-ade4-4f72-a214-f61def1a71ea.png)

### Inputs
Inputs include:
- Process design kits(PDKs)
- DRC and LVS rules,SPICE Models
- Library and User-Defined specs

### Design Steps
Design steps include:
- Circuit Design
- Layout Design
- Characterization
### Outputs
Ouptus include:
- CDL(Circuit Description Language)
- GDSII,LEF,extracted spice netlist(.cir)
- Timing,noise,power.libs,function

### Characterization flow
Types of characterization include:
- Timing characterization
- Power characterization
- Noise characterization


# Day-3: Design Cell Library using Magic Layour and ngspice characterization
## Labs for CMOS inverter ngspice simulation
The inverters is designed using Magic tool. It takes the tech file,that is,```sky130A.tech``` and the ```.mag``` file as the input.
The below snapshot shows the inverter layout with and without drc.DRC is a tool in magic that ensures that our layout is error free.

![image](https://user-images.githubusercontent.com/92938137/183023069-20dda582-b380-42a5-ad09-0db6b4af521f.png)

![image](https://user-images.githubusercontent.com/92938137/183023531-dcd2e5da-d5ad-466a-955d-54497e391546.png)

## Create Standard Cell Layout and Extract SPICE Netlist
In order to simulate and verify the standard cell designed, we must first extract it to obtain its SPICE netlist. There are two steps to extract a file.
- Create a ```.ext``` file: ```extract all```
![image](https://user-images.githubusercontent.com/92938137/183024993-ce6210be-4457-44b3-b3b3-2d678175dc1e.png)

.ext file:

![image](https://user-images.githubusercontent.com/92938137/183024922-f988d3d1-f12a-475a-a6ad-29407608ed9b.png)
![image](https://user-images.githubusercontent.com/92938137/183024877-46b60f09-ee4a-46a7-8990-d549cd35ae46.png)

- Extract to SPICE along with extracting the parasitic capacitors. This creates a ```.spice``` file.

``` ext2spice cthresh 0 rthresh 0```

```ext2spice```

.spice file:

![image](https://user-images.githubusercontent.com/92938137/183025499-c9ab9379-2021-4f13-b7a5-82232175337e.png)
![image](https://user-images.githubusercontent.com/92938137/183025707-fceb9e6a-55a0-4d1c-ae62-61220c020292.png)

Edited .spice file

![image](https://user-images.githubusercontent.com/92938137/183046129-73bcb09a-388c-4b87-bd03-4bb06e4282f5.png)
![image](https://user-images.githubusercontent.com/92938137/183049455-c640ad9d-0ccd-46fa-a304-9eecd67b932e.png)

## Transient Analysis Using Ngspice
The spice netlist generated is provided as source to the ngspice tool using the below command:
```ngspice<source-file-name.spice>```

Use: ```plot y vs time a``` to plot the graph

![image](https://user-images.githubusercontent.com/92938137/183048662-064270ca-ca54-40ed-a61e-7c54edc8c8bd.png)
![image](https://user-images.githubusercontent.com/92938137/183048616-9bf494cd-ef27-4bdb-a95d-3953e4c8874e.png)
![image](https://user-images.githubusercontent.com/92938137/183049712-c086fddb-bee9-4de5-8a29-9d4f5f52b118.png)

From the graph we characterize the cell.

Rise time = 0.07823ns

Cell Rise Delay = 0.05384ns

Cell Fall Dealy = 0.0289ns

# Day 4: Pre-layout Timing Analysis and Importance of Good Clock Tree
To perform placement and routing one does not need the amount of detailing magic provides us with. We only need information about the input/output port,the power and ground port. All this information is provided to us by the LEF file.

## Steps to convert Grid Info to Track Info
There are certain guidelines that one must follow while making a std cell set:
- Input and Output port must lie on the intersection of the vertical and horizantal tracks
- Width of the std cell must be in the odd multiple of horizantal pitch and lenght must be odd multiple of vertical pitch.Tracks are used during the routing phase.

![image](https://user-images.githubusercontent.com/92938137/183089300-28cef31e-3c00-4b79-9ad9-acbc722d694a.png)
![image](https://user-images.githubusercontent.com/92938137/183090067-ecafb019-c758-4546-a695-074323f54332.png)
From the above snippet,we can conclude that the layout satifies both the above conditions above.

## Steps to convert Magic layout to std cell LEF
Once the layout satisfies the guidelines and the port along with the purpose of each port is set, one can extract the LEF file.
The command used to create a LEF File is :

```lef write```

If we dont specify any file name, the lef file gets created with the same name as the ```.mag``` file by default.

![image](https://user-images.githubusercontent.com/92938137/183093691-035e5211-013c-401d-89be-c42db205fcfb.png)
![image](https://user-images.githubusercontent.com/92938137/183093428-a8d7ca5b-1442-4801-a721-469f4ecb4738.png)

Once we create the ```.lef``` file copy the ```.lef``` and ```sky130_fd_sc_hd__*``` in the picorv32a folder. Run the openlane process again.
Instead of running ```prep -design <design-name>``` we run ```prep -design <design-name> -tag <folder-name> -overwrite``` to overwrite in the same folder instead of creating a new one.
![image](https://user-images.githubusercontent.com/92938137/183240688-0bb96d91-645a-4e92-a471-50c7a06802ef.png)
![image](https://user-images.githubusercontent.com/92938137/183240783-49a1f416-855e-4d39-9dbc-c27a8df3c6f5.png)
![image](https://user-images.githubusercontent.com/92938137/183240879-4593965c-9560-4b28-8ad7-5c101b03a90b.png)

## Timing analysis with ideal clocks using openSTA
The results obtained after running ```sta pre_sta.conf```.

![image](https://user-images.githubusercontent.com/92938137/183268731-05f44672-bd0b-4236-b844-38f2ebbaf482.png)
![image](https://user-images.githubusercontent.com/92938137/183269112-e64b0664-1b4d-45c9-8d5d-a25634448404.png)
![image](https://user-images.githubusercontent.com/92938137/183341406-56fb0dc3-7cb5-486d-b72c-f806e974e97a.png)

Timing can be improved by:
- Scaling the buffer.
- Setting a maximum fan-out for the logic.
- Increasing the time period of the clock.

## Clock Tree Synthesis TritonCTS and signal integrity
Clock tree synthesis is used to ensure that the clock signal is distributed equally to all the blocks of a sequential logic.One of the way to do so is using H-tree algorithm where it focuses on equilizing the clock wire length.
Clock Net Shielding is used to protect the clock net from the outside signals to prevent unnecessary coupling that could cause problems like glitches and delay.
In OpenLANE we perform CTS using TritonCTS tool.

To perform CTS use the command:

```run_cts```

![image](https://user-images.githubusercontent.com/92938137/183269498-0b8cd9dd-6947-46a3-9008-126504e04350.png)

Once the CTS flow is done, we need to do the STA after the entire clock tree is built.
This is done by invoking ```openroad``` inside openlane.

![image](https://user-images.githubusercontent.com/92938137/183270292-64a89760-663c-4c19-ab76-dd0803c47885.png)
![image](https://user-images.githubusercontent.com/92938137/183270385-0888b95c-e8e0-4fe3-91c3-738e9bd9c034.png)

This leads to huge stack voilations.Instead we perform STA only for the typical libraries.

![image](https://user-images.githubusercontent.com/92938137/183270862-89e102ee-9e99-408e-91f2-2622a9cd03e0.png)

# Day 5: Final steps for RTL2GDSII using tritonRoute and openSTA
## Routing and DRC Rule Check
Routing is a process of not only connecting the input or output pin or  with the logic block or two points but also finding the best possible route to connect the source and target.
These points must be connected with very limited zig-zag lines and as much as possible with L-shaped lines. 
One of the way to perform routing is using the Maze Routing or Lee's Algorithm.
There are few rules to be followed while perfomring routing including criteria to obey minimum wire width, minimum wire pitch,minimum wire spacing,etc.

## Power Distribution Network and Routing
To perform power distribution use the following command:

```gen_pdn```

![image](https://user-images.githubusercontent.com/92938137/183272220-d2c6e682-53e9-4657-93ab-a3ce2f9530ce.png)
![image](https://user-images.githubusercontent.com/92938137/183272279-c40d2750-ee17-45fb-8cda-a98ac3989ace.png)
![image](https://user-images.githubusercontent.com/92938137/183272247-57044c12-179d-4d6d-a9d1-bc87359967de.png)

To perform Routing:
OpenLANE uses TritonRoute as the routing engine.Like placement, routing consists of two stages:
- Global Routing-this is done by fast route
- Detailed Routing-this is done by detailed route

Routing is done using the following command:

```run_routing```

![image](https://user-images.githubusercontent.com/92938137/183272470-03f12bc0-7f51-4b87-a8db-4ba3b5f25dda.png)

After performing routing if there are any drc errors we must manually check and correct them out with the help of ```tritonRoute.drc``` file.
Also as done with placement we can view the magic terminal after performing routing.

![image](https://user-images.githubusercontent.com/92938137/183342172-570b09e2-bef5-4336-b625-bc7897d3855c.png)



# Acknowledgement
- [Nickson Jose,](https://github.com/nickson-jose)VSD VLSI Engineer
- [Kunal Ghosh,](https://github.com/kunalg123)Co-founder VSD Corp,Pvt Ltd.
