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
