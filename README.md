# Advanced_Physical_Design
This file contains the information learnt during the [Advanced Physical Design](https://www.vlsisystemdesign.com/advanced-physical-design-using-openlane-sky130/) workshop done using picorv32 core. We perform a complete RTL2GDS Analysis using Openlane.

# Table of Contents
- [Introduction To RTL to GDSII flow](https://github.com/Shris7/Advanced_Physical_Design/edit/main/README.md#intoduction-to-rtl-to-gdsii-flow)
- [Open Source Tools used](https://github.com/Shris7/Advanced_Physical_Design/edit/main/README.md#open-source-tools-used)
- [Day 1: Inception of open-source EDA,OpenLANE and sky130 PDK](https://github.com/Shris7/Advanced_Physical_Design/edit/main/README.md#day-1-inception-of-open-source-edaopenlane-and-sky130-pdk)
   - [How to talk to computers](https://github.com/Shris7/Advanced_Physical_Design/edit/main/README.md#how-to-talk-to-computers) 
      -  [Intordution to die,core,pads](https://github.com/Shris7/Advanced_Physical_Design/edit/main/README.md#intordution-to-diecorepads)
      -  [Introduction to RISC-V](https://github.com/Shris7/Advanced_Physical_Design/edit/main/README.md#introduction-to-risc-v)
   -  [SOC Design and OpenLANE](https://github.com/Shris7/Advanced_Physical_Design/edit/main/README.md#soc-design-and-openlane)
      -   [Introduction to RTL2GDS flow](https://github.com/Shris7/Advanced_Physical_Design/edit/main/README.md#introduction-to-rtl2gds-flow) 
      -   [Introduction to OpenLANE](https://github.com/Shris7/Advanced_Physical_Design/edit/main/README.md#introduction-to-openlane)
   -  [Open-source EDA tools](https://github.com/Shris7/Advanced_Physical_Design/edit/main/README.md#open-source-eda-tools)
      -   [Initialisation of OpenLANE](https://github.com/Shris7/Advanced_Physical_Design/edit/main/README.md#initialisation-of-openlane)
      -   [Design Preperation Step](https://github.com/Shris7/Advanced_Physical_Design/edit/main/README.md#design-preperation-step)
      -   [Run Synthesis](https://github.com/Shris7/Advanced_Physical_Design/edit/main/README.md#run-synthesis)   
 
 
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
 - Die : it is a block of semiconductor material on which a given circuit is fabricated.
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
 OpenLANE is a open source tool using which we can perfomr a complete RTL to GDSII analysins. It compromises of various open soruce tools such as yosys,magic,netgen,fault, openROAD. The figure below describes the architecture of OpenLANE.
 
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
