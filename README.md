# VSD-SoC-Design-planning
# Day 1
# Simplified RTL to GDS flow
### The RTL to GDS flow consists of the steps of desiging a application specific integrated circuit(ASIC). It starts with a Register transfer level (RTL) file and ends at a Graphical Data System file (GDS).

![Screenshot 2024-05-26 200923](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/df0c35ef-c06b-4e18-998c-7533d34140ba)

# 1. Synthesis
### In synthesis design RTL is translated into circuit made out of components from Standared cell library 
### then the resultant circuit is described in HDL and reffered as Gate level netlist
![Screenshot 2024-05-26 201029](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/9d837449-45f5-4497-846a-6cdac66a960d)
### Cells (the building blocks of a chip) are designed with regular layouts. Each cell is usually enclosed in a rectangle with a fixed height, while the width can vary.
 ### These cells have different representations or "views" used by various Electronic Design Automation (EDA) tools:
 ### This view includes electrical models, such as delay and power models, which help in analyzing the performance and power consumption of the cells.
* **Liberty View:** This view includes electrical models, such as delay and power models, which help in analyzing the performance and power consumption of the cells.
* **HDL View:** This provides behavioral models of the cells, describing how they function logically.
* **Spice or CDL View:** These are detailed circuit-level representations used for precise electrical simulations.
* **Layout Views:**
   1. **Abstract View (Lib View):** A simplified representation of the cell layout, used for general placement and routing.
   2. **Detailed View (GDS View):** A highly detailed layout view used for the final physical design and fabrication of the chip.
# 2. Floor and power planning
![Screenshot 2024-05-27 182110](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/1cc4aa05-1061-41d5-b549-c683d0c4f9d9)
* ### Macro Floor-Planning: dimensions, pin locations, rows definition
![Screenshot 2024-05-27 182144](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/5f0c3135-6e19-44bb-a74e-5bb812239967)
*  **Power planning:** A chip is powered by multiple VDD and GND pins. The power pins are connected to all components through rings and vertical and horizontal metal straps.Such parallel structures are meant to reduce the resistance and hence the IR drop and to address the electro migration problem. Typically, the power distribution network uses the upper metal layers as they are thicker than lower metal layers. Hence, they have less resistance.
![Screenshot 2024-05-27 182204](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/cccdb1a6-8da6-4d1b-998f-06d878fd5903)
# 3. Placement
![Screenshot 2024-05-27 182305](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/692014b3-c17e-47ec-b3ac-092acd857e84)
* **1. Global placement**
* **2. Detailed placement**
 
  ![Screenshot 2024-05-27 182538](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/caf7c606-ea8c-4551-a966-c8a880fe31cb)

Global placement, optimal positions for all cells. Such positions are not necessarily legal so cells may overlap or may go off roads.
In detailed placement the positions obtained from global placement are minimally altered to be legal.
After placement comes routing, but before routing the signals we need to route the clock.
# 4. Clock distribution network
To deliver the clock to all sequential elements with minimum skew and in good shape. Clock skew means the arrival of the clock at different components at different times. Usually a tree like structure in which the clock source are the roots and the clocked elements are the leaves.

![Screenshot 2024-05-27 203024](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/966ebbf1-8bd8-4a8c-a890-1e1a14ed0b6c)
# 5. Signal Routing
Implement the interconnect using the available metal layers.For each (metal) layer the pdk defines the thickness, the pitch and the minimum width, also it defines the vias that can be used to connect different wire segments on different layers together.Sky130 pdk defines 6 routing layers. The lowest layer is called local interconnect. The following 5 layers over the local interconnect are aluminium layers.

![Screenshot 2024-05-28 100938](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/5ea717f8-ddfd-499c-8717-305f90aca20f)

**Most routers a grid router:** They construct the routing grid out of the metal layer tracks

Routing grid is huge therefore a divide and conquer technique is applied.
+ **Global routing** : generates routing guides
+ **Detailed routing** : uses the routing guides to implement the actual wiring
  # 6. Sign off
  ![Screenshot 2024-05-28 101753](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/b6e1763b-9225-4797-a1ee-1c17450d66f0)
  
# Day 1 Labs : Open Lane directory structure in detail

* Start by verifying the functionality of the virtual machine.
* Once confirmed, you should observe a terminal interface within the virtual environment.

![VirtualBox_vsdworkshop_28_05_2024_20_12_00](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/990c4110-58be-4b33-98dc-5de68ac3e4c3)

* Before proceeding, navigate to the following directory: cd Desktop/work/tools/openlane_working_dir/openlane.
* Next, execute the Docker command.

![VirtualBox_vsdworkshop_28_05_2024_20_26_02](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/c69d2b09-69bb-4991-a187-36eddf8d4fff)

* Proceed by running the script: flow.tcl -interactive.  This script contains instructions on how the different tools within openlane should collaborate and details on running the flow systematically.
* Then terminal look like below image

![VirtualBox_vsdworkshop_28_05_2024_20_32_37](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/2cc10601-c59b-4d73-ae20-861d4d0e1b4e)

* Then run 2 command : 1. package require openlane 0.9 and 2. prep -design picorv32a
* After running above command the terminal looks like below image

![VirtualBox_vsdworkshop_28_05_2024_20_49_22](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/29633264-0271-492a-8064-7ab0664a23e2)

* Now we are ready to initiate the synthesis process and generate a netlist from the design. Execute the command "run_synthesis" 
* It will take few minutes to complete Synthesis

![VirtualBox_vsdworkshop_28_05_2024_20_54_22](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/5adb6697-ea6c-4e67-99b4-8de9fca613fa)

 # Task 1.

 ## our objective is to find flop ratio

  * Here D-flipflop is metioned as dfxtp-2 and the count is 1613

![VirtualBox_vsdworkshop_02_06_2024_15_50_56](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/56f92d56-e625-41e5-ba0f-e32ba43d0992)

* And total number of cell is 14876

![VirtualBox_vsdworkshop_02_06_2024_15_51_25](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/e005314e-9f6c-49f0-bf8d-3a3ef8f7e973)

* So after calculating we get flop ration 0.10842 which is 10.8 in percentage

  # Day 2 : Floorplanning

* After exicuting command run_floorplan if floorplan completed successfully the terminal looks like below image 

![VirtualBox_vsdworkshop_02_06_2024_17_46_38](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/72f9710a-ce68-4b60-add3-1684c5e8e867)

* To visualize the constructed floorplan for our design we have to use open-source tool by writing the below command.
  
* magic -T /home/vsduser/desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &

![VirtualBox_vsdworkshop_02_06_2024_23_03_11](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/3892dea8-97c8-446f-a2e4-d09e1f211bb4)

* Press **S** and **V** to select the entire layout and center it on the screen.
* To zoom in on a specific area, **left-click** and **drag** to draw a box around the area you want to zoom into.
* **Right-click** to lock the box.
* Press **Z** to zoom into the selected area.

* Zoom in further to see the pins clearly.
* Press **S** and click on any pin to select it.
* Look at the **tkcon** terminal.
* Type **what** in **tkcon** to see the details of the selected pin.

![VirtualBox_vsdworkshop_02_06_2024_23_19_39](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/5fd0c5ec-89f3-4001-804a-adb3ea07055d)
![VirtualBox_vsdworkshop_02_06_2024_23_20_11](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/c909784e-fce9-4bb4-b32b-3236778f771a)

# placement

* After completion of Floorplan we have to type command run_placement
* Then the terminal will look like below image

 ![VirtualBox_vsdworkshop_03_06_2024_16_23_23](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/32d8099b-b372-4e57-a5d7-57d04e0b3dc5)

* When we see visually after writing **magic tool** command terminal looks like below immage

![VirtualBox_vsdworkshop_03_06_2024_19_03_06](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/77cccb82-5258-423c-95d7-e03e0d6b1236)

![VirtualBox_vsdworkshop_03_06_2024_19_06_59](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/dc825c85-7603-4808-9def-3ed4e315597b)

![VirtualBox_vsdworkshop_03_06_2024_19_05_44](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/1e83add1-0035-4bd4-aced-e2639ca01bd2)

# Day 3

* We've completed the placement stage so far.
* To understand library characterization, we'll focus on a simple cell, like an inverter, and perform transient analysis to extract timing information.
* At the end we'll try placing this cell in the existing design, picorv32a, to see if it works.

**Lab steps to git clone the VSDSTDcell Design:**

* We'll start with an example of a simple cell, an inverter, and try to insert it into the picorv32 design.
* First we need to thoroughly understand the cell. There's a GitHub repository with complete details about the inverter cell using Skywater.
* We'll clone that repository to our local system.

![Screenshot 2024-06-03 200055](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/723142a9-44d4-4b08-8ba6-6aeafb817e4d)

* Copy the GitHub link and paste it into the terminal with the **git clone** command.
*  Run command.
*  After cloning, you'll see a new directory named vsdstdcelldesign.

![VirtualBox_vsdworkshop_03_06_2024_20_15_28](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/d3fe58df-38f3-4e7d-91af-e45c9a564c99)

* To open the .mag file, we need the .tech file located in the pdks directory. Therefore, we should copy the .tech file from the pdks directory and paste it into the current directory.

![VirtualBox_vsdworkshop_03_06_2024_22_43_40](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/0329dc51-4826-4caf-aa82-1957726d3a37)

* Now we can see .tech file is copied in present directory

![VirtualBox_vsdworkshop_03_06_2024_22_44_57](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/908edb2d-5587-4238-864d-fee50989c5fb)

* We can visually see by giving command **magic -t sky130A.tech sky130_inv.mag &**

![VirtualBox_vsdworkshop_03_06_2024_22_51_14](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/15fddfa3-3b4c-46c0-a474-38768242f582)

* #### nmos

![VirtualBox_vsdworkshop_03_06_2024_23_06_53](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/a279c4eb-8e1f-4b94-8f69-1b51cdafea6b)

* #### pmos

![VirtualBox_vsdworkshop_03_06_2024_23_07_08](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/d0605946-5e26-496e-8942-6b1362b14b65)

* #### Drain of both nmos and pmos are connect to out

![VirtualBox_vsdworkshop_03_06_2024_23_11_34](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/00038b7c-028e-4668-bd01-98fb3f82577a)

* #### Source of pmos is connected to VDD

![s pmos](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/57f5011a-12cb-4c1d-9274-4027961d3552)

* #### Source of nmos is connected to GND

![s nmos](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/985722ce-d3f8-4d3b-abf3-363fa06b26f6)

* To know logical function of Inverter we need to extract the spice and we will do simulation on spice

![extract](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/82af3042-daef-45ee-953f-2796a0285ddb)
![ectracted](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/51b50f0f-0be2-41f1-867d-deed3004c3c7)
![ext2spice](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/0bb4994a-a043-433c-9ee2-2b6adfcd06fb)
![file created](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/1a709d22-c49f-4540-bc40-57c2617e2016)

# Day 4

#### First we need to follow these standard cell guidelines:
* Place the input and output ports where vertical and horizontal tracks meet.
* Make sure the width of the standard cell is a multiple of the track pitch.

![day 4](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/405cc697-196d-49ff-8925-b45b89525884)
![day 4 1](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/19697052-115a-4779-92d1-ba87ca98c442)
![d4 1](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/4a4dae40-3217-48b1-b1c9-7eb5088d2c26)
![d4 2](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/5f474821-945b-4a7b-8e6f-3c9ecf48fd32)

* lets save the cell with name sky130A_vsdinv.mag

 ![d4 3](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/6d1047a4-6f5e-4fcc-b4b0-941b629f8d60)
![d4 4](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/987549f0-eae9-4f25-a11e-c58ba709d14f)

* By giving command **lef write** we create lef file like given below
  
![d4 5](https://github.com/Samarthng/VSD-SoC-Design-planning/assets/170659984/40f901d3-aaae-4b90-a6a5-8bbedf108e84)

















