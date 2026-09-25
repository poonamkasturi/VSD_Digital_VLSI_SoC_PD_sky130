# VSD_Digital_VLSI_SoC_PD_sky130
Notes and learning documentation for the OpenLane Sky130 Workshop conducted by VLSI System Design. 

Workshop duration - 10 Days 

Dates - September 16, 2026 - September 25, 2026


# OpenLANE Sky130 Digital VLSI SoC Design Workshop Summary

# Topics Covered

## Day 1: Introduction to Open-Source ASIC Design

- Basics of how computers execute software and hardware concepts.
- Introduction to:
  - QFN-48 packages
  - Chips, dies, cores, pads, and IPs
  - RISC-V architecture
  - SoC (System-on-Chip) design concepts
  - Open-source digital ASIC design flow
- Understanding the RTL-to-GDSII flow using OpenLANE.
- Exploring OpenLANE directory (project) structure and workflow.
- Invoking the toolflow OpenLANE, getting in the package required
- Design preparation of picorv32a.
- Running synthesis, and analysis of synthesis results and reports.

---

## Day 2: Floorplanning and Library Cells

- Chip floorplanning concepts:
  - Utilization factor
  - Aspect ratio
  - Power planning
  - Pin placement
  - Decoupling capacitors
- Cell Placement and Congestion-aware optimization techniques.
- Library binding and characterization.
- Timing concepts:
  - Timing thresholds
  - Propagation delay
  - Transition time

---

## Day 3: Standard Cell Design and Characterization

- CMOS inverter design using ngspice.
- SPICE deck creation and simulation.
- CMOS fabrication process:
  - N-well/P-well formation
  - Gate creation
  - Source/drain formation
  - Metal layers and interconnects
- Standard Cell Layout design in Magic.
- DRC (Design Rule Check) Verification and extraction of SPICE netlists.
- Modification needed in extracted SPICE netlist to make it compatible to be executed in ngspice
- Sky130 technology-file exploration and rule checking.
- Characterizing cells using Sky130 technology files.

---

## Day 4: Timing Analysis and Clock Tree Synthesis

- Timing modeling using delay tables.
- Creating LEF files from layouts.
- Using OpenSTA for timing analysis.
- Setup and hold time analysis.
- Clock uncertainty and jitter.
- Clock Tree Synthesis (CTS) using TritonCTS.
- Signal integrity and crosstalk considerations.

---

## Day 5: Routing and Final RTL-to-GDSII Steps

- Global and Detailed Routing conepts 
- Routing algorithms, including Lee's Maze Routing.
- Design Rule Checking (DRC).
- Building Power Distribution Networks (PDN).
- Global and detailed routing using TritonRoute - TritonRoute routing flow and features.
- Handling routing connectivity and topology.
- Final post-route outputs and verification steps.
- Post-routing timing analysis and final RTL-to-GDS completion.

---

## Tools and Technologies Used

- OpenLANE
- Sky130 PDK
- Magic Layout Tool
- ngspice
- OpenSTA
- TritonCTS
- TritonRoute
- RISC-V Architecture

---


## Overall Takeaway

By the end of this workshop, participants will be able to:

- Understand the complete open-source ASIC design flow starting with a given RTL netlist.
- Perform RTL-to-GDSII implementation using OpenLANE.
- Progressing through synthesis, floorplanning, placement, CTS, and routing techniques.
- Design and characterize standard cells.
- Perform timing analysis and DRC verification.
- Ending with final GDS Generation using OpenLANE toolchain + Sky130 open-source pdk.


## Acknowledgment
I express my sincere gratitude to Kunal Ghosh and Team VLSI System Design (VSD) for providing me with such a great opportunity to participate and learn through the ongoing RISC-V SoC Tapeout Program.









