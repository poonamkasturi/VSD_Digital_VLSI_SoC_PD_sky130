## Understanding Chip Architecture, Packaging, and RISC-V Fundamentals

### Electronic Boards and Chip Integration
A typical electronic system, such as an arduino board or FPGA board, consists of a processor connected to multiple peripherals including Flash memory, SDRAM, ADC, I2C, SPI, EEPROM, power supplies, and programming interfaces like JTAG. These components communicate together to perform complete system-level operations.

<img width="558" height="318" alt="image" src="https://github.com/user-attachments/assets/b422e79f-1610-4665-a7a8-4528ce935594" />


### Chip Packaging Basics
The silicon chip is enclosed inside a package, such as a **QFN (Quad Flat No-Lead) package**. The package provides electrical connections between the external board and the internal chip through pins and wire bonds.

Key terms:
- **Package**: Protective enclosure containing the chip.
- **Pins**: External electrical connections.
- **Wire Bonds**: Connections between package pins and chip pads.
<img width="506" height="315" alt="image" src="https://github.com/user-attachments/assets/a9f596cc-7de5-43da-bf48-5e01bf7c1c05" />
<img width="383" height="319" alt="image" src="https://github.com/user-attachments/assets/dbe2c262-5654-46c1-8ea3-1cc28a4a574b" />



### Internal Structure of a Chip
A chip is composed of:

- **Pads**: Entry and exit points for signals.
- **Core**: Region containing digital logic such as AND gates, OR gates, multiplexers, and processors.
- **Die**: The complete silicon area fabricated on the wafer.
<img width="452" height="304" alt="image" src="https://github.com/user-attachments/assets/b45596f4-0a0d-4e0f-b648-be64e461532d" />


### System-on-Chip (SoC)
A typical RISC-V SoC contains:

- RISC-V Processor Core
- SRAM
- ADC (Analog-to-Digital Converter)
- DAC (Digital-to-Analog Converter)
- PLL (Phase-Locked Loop)
- SPI and other communication interfaces

These blocks work together to implement a complete computing system on a single chip.

### Foundry and Foundry IPs
A **Foundry** is a semiconductor manufacturing facility where chips are fabricated using specialized equipment such as lithography and deposition machines.

Important concepts:
- **Foundry IPs**: Pre-designed and verified analog/mixed-signal blocks such as PLLs, ADCs, DACs, and SRAMs.
- **Macros**: Digital design blocks integrated into the chip.
- Designers communicate with foundries using technology files and process design kits (PDKs).
<img width="536" height="315" alt="image" src="https://github.com/user-attachments/assets/b90b4420-3af9-44fa-a46b-799ac12855a5" />

### RISC-V Instruction Set Architecture (ISA)
RISC-V ISA acts as the language between software and hardware.

Execution flow:

```text
C Program
↓
Compiler
↓
RISC-V Assembly Instructions
↓
Assembler
↓
Machine Code (Binary)
↓
Hardware Execution
```

<img width="641" height="414" alt="image" src="https://github.com/user-attachments/assets/20f72669-7089-42de-a9b5-8fa2fbcd4a4a" />
<img width="843" height="420" alt="image" src="https://github.com/user-attachments/assets/06c134ee-ef8a-4d86-ab26-d08c5199c228" />
<img width="638" height="409" alt="image" src="https://github.com/user-attachments/assets/46387d90-fe67-4533-842c-b3f47344f996" />
<img width="650" height="411" alt="image" src="https://github.com/user-attachments/assets/a59f4307-5328-475c-b720-f5cfd2884eff" />
<img width="652" height="399" alt="image" src="https://github.com/user-attachments/assets/3633299b-454c-4577-a4c0-a7df2b1990c9" />

# OpenLANE Flow and Sky130 PDK: Key Learnings

## What is OpenLANE?

OpenLANE is an open-source ASIC design flow that automates the complete **RTL-to-GDSII** implementation process. It integrates multiple open-source EDA tools into a single workflow, reducing manual intervention.

### Major Tools Used in OpenLANE

- **Yosys** – RTL Synthesis
- **ABC** – Logic Optimization and Technology Mapping
- **OpenSTA** – Static Timing Analysis (STA)
- **OpenROAD** – Floorplanning, Placement, CTS, and Routing
- **Magic** – Layout Viewing and DRC
- **Netgen** – Layout vs Schematic (LVS) Verification

### RTL-to-GDSII Flow

```text
RTL Design
    ↓
Synthesis (Yosys)
    ↓
Timing Analysis (OpenSTA)
    ↓
Floorplanning
    ↓
Placement
    ↓
Clock Tree Synthesis (CTS)
    ↓
Routing
    ↓
GDSII Layout
```

---

# Linux Commands Used

Basic Linux commands required for running OpenLANE:

```bash
cd          # Change directory
ls          # List files
ls -ltr     # List files chronologically
pwd         # Print current directory
clear       # Clear terminal
```

---

# Sky130 Process Design Kit (PDK)

The workshop uses the **SkyWater SKY130 Open-Source PDK**, which contains all technology information required for chip design and fabrication.

## PDK Directory Structure

```text
pdks/
├── skywater-pdk/
├── open_pdks/
└── sky130A/
```

### Important Components

#### `libs.ref`
Contains process-specific reference files:

- Timing Libraries (.lib)
- Cell LEF Files
- Technology LEF Files
- Process Corners

#### `libs.tech`
Contains tool-specific technology files for:

- Magic
- KLayout
- Netgen
- OpenROAD
- ngspice

---
<img width="664" height="617" alt="image" src="https://github.com/user-attachments/assets/e287adce-a302-4a34-b81f-140eb0b65f87" />




# Sky130 Library Naming Convention

Example:

```text
sky130_fd_sc_hd
```

Where:

- `sky130` = SkyWater 130nm Technology
- `fd` = Foundry Design
- `sc` = Standard Cell
- `hd` = High Density Library

---

# OpenLANE Design Directory Structure

```text
designs/
└── picorv32a/
    ├── src/
    ├── config.tcl
    └── sky130A_sky130_fd_sc_hd_config.tcl
```
<img width="1376" height="199" alt="image" src="https://github.com/user-attachments/assets/8dc1621f-4691-49b4-88fc-1e46f2b80938" />

### src/

Contains:

- RTL Verilog files
- Constraint files

### config.tcl

Contains design-specific settings:

```tcl
CLOCK_PERIOD
CLOCK_PORT
VERILOG_FILES
SYNTHESIS_OPTIONS
```

### Configuration Priority

```text
Default OpenLANE Settings file -- flow
        ↓
Design Specific config.tcl - config.tcl in designs/picorv32a folder
        ↓
PDK-specific config.tcl  - sky130A_sky130_fd_sc_hd_config.tcl

Higher levels override lower-level settings.

```
---

# Launching OpenLANE

run docker command to come in bash mode

directory hierarchy
```
~/Desktop/work/tools/openlane_working_dir/openlane $ docker
```

Start OpenLANE in interactive mode:

```bash
bash~4.2$ ./flow.tcl -interactive
```
This opens the OpenLANE flow and brings the prompt to %
<img width="1280" height="768" alt="openlane stepsdocker_n_flow" src="https://github.com/user-attachments/assets/48ac8c05-1d16-4e36-a08c-b3b3758d4b9d" />

Load the OpenLANE package:

```tcl
% package require openlane 0.9
```

Prepare the design:

```tcl
% prep -design picorv32a
```

This step:

- Creates run directories
- Loads configuration files
- Generates merged LEF files
- Sets up project structure
<img width="1280" height="768" alt="VirtualBox_vsdworkshop_24_09_2026_06_11_15 openlane_2" src="https://github.com/user-attachments/assets/0a42fa85-b628-4cb5-9348-98140cb96e6c" />
---

# Generated Run Structure

After preparation, OpenLANE creates:

```text
runs/
└── <run-date>/
    ├── configs/
    ├── logs/
    ├── reports/
    ├── results/
    └── tmp/
```

### Folder Description

| Folder | Purpose |
|----------|----------|
| configs | Active design configurations |
| logs | Execution logs |
| reports | Timing and synthesis reports |
| results | Outputs generated at each stage |
| tmp | Temporary/intermediate files |

---

# LEF File Merging

OpenLANE merges:

```text
Technology LEF
        +
Cell LEF
        =
Merged LEF
```

Benefits:

- Single database access
- Faster execution
- Simplified processing


---

# Running Synthesis

Start synthesis:

```tcl
% run_synthesis
```


### Synthesis Stages

1. RTL Parsing
2. Logic Optimization
3. Technology Mapping
4. Gate-Level Netlist Generation
5. Timing Analysis

### Output

Generated netlists can be found in:

```text
runs/<date>/results/synthesis/
```

---


# OpenLANE Inputs and Outputs

## Inputs

- RTL Verilog Files
- Constraints
- Sky130 PDK

## Outputs

- Synthesized Netlist
- DEF Files
- Routed Design
- GDSII Layout

---

# Synthesis Statistics

Example synthesis report:

```text
In VIDEO LECTURE
Total Cells      = 17,323
D Flip-Flops     = 1,634

Total Chip Area = 

In My RUN
Total Cells      = 14876
D Flip-Flops     = 1,613

Total Chip Area = 148708.87
```

## Flop Ratio Calculation

```text
In VIDEO LECTURE
(1634 / 17323) × 100
= 9.43%

In MY RUN
```(1613/14876)*100 = 10.84 %
```

<img width="640" height="337" alt="Synthesis_dff_ total cell count" src="https://github.com/user-attachments/assets/a60f17cf-6566-44f9-bf4c-4e833c316149" />
<img width="640" height="337" alt="VirtualBox_vsdworkshop_23_09_2026_18_49_18 synthesis stat report dff count" src="https://github.com/user-attachments/assets/c2186c82-1ccd-49e2-b587-a50b544748d1" />



---

# Key Learning Outcomes

- Understand the first step of OpenLANE RTL-to-GDSII flow.
- Learn essential Linux commands used in ASIC design.
- Explore the Sky130 PDK structure.
- Understand configuration files and design setup.
- Run synthesis using Yosys and OpenLANE.
- Analyze synthesis reports.
- Understand GitHub repositories and documentation.
- Calculate important design metrics such as flop ratio.
- Learn the first step in the complete open-source ASIC physical design workflow.

---

# Summary
- config files have a priority
- config file generated in the runs folder post synthesis gives a glimpse of the values used for various switches set in the config files
- this file is a place where we can ascertain if the values of the switches have been considered as desired
- switch values should be modified in the highest priority config file which is the technology specific config file in the design folder













