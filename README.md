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

