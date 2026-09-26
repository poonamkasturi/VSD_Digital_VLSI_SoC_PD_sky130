# 🖥️ VLSI Physical Design: DAY_2

## Floorplanning Fundamentals

![Domain](https://img.shields.io/badge/Domain-VLSI-blue)
![Flow](https://img.shields.io/badge/Flow-Physical%20Design-green)
![Stage](https://img.shields.io/badge/Stage-Floorplanning-orange)
![License](https://img.shields.io/badge/License-MIT-red)
![Status](https://img.shields.io/badge/Status-Learning%20Project-success)
> A comprehensive study of **VLSI Physical Design Floorplanning**, covering Core & Die estimation, Utilization Factor, Aspect Ratio, Macro Placement, Decoupling Capacitors, Power Planning, Pin Placement, and Placement Blockages.

## Placement, Routing, and Library Characterization
![Standard_Cell_Library](https://img.shields.io/badge/Standard_Cell_Library-Physical%20Functional%20Timing%20information-blue)
![Placement](https://img.shields.io/badge/Placement-Logical_Gate%20Mapping%20to%20Std_Cell-green)
![Placement_Optimization](https://img.shields.io/badge/Placement_Optimization-Maintain%20Signal%20Integrity-orange)
![Routing](https://img.shields.io/badge/Routing-Metal%20Layers-red)
![Timing_Analysis](https://img.shields.io/badge/Timing_Analysis-Ideal%20Clks%20Before%20CTS-success)
> The Placement and Routing (P&R) is the next stage that converts a synthesized gate-level netlist (obtained from floorplannig) into a physical layout that can be manufactured on silicon. During this stage, logical gates are mapped to physical standard cells, placed on the chip, optimized, and finally interconnected through routing. 

## Standard Cell Design Flow and Characterization

![Standard_Cell_Library](https://img.shields.io/badge/Standard_Cell_Library-Std%20Cells%20Macros%20IP%20De%Cap-blue)
![STD_Cell_Design_FLow](https://img.shields.io/badge/Std_Cell_Design_Flow-Inputs%20Design%20Characterization-green)
![Inputs](https://img.shields.io/badge/Inputs-PDKs%20User%20Defined-orange)
![Design](https://img.shields.io/badge/Design-Circuit%20Design%20Layout%20Design%20Characterization-red)
![Output](https://img.shields.io/badge/Output-CDL%20GDSII%20LEF%20LIB-success)
> Standard cell design is the process of developing reusable digital building blocks such as inverters, buffers, and logic gates for ASIC design. Starting with foundary PDK inputs, DRC/LVS rules, SPICE models and user specifications, cells undergo circuit design, layout design, parasitic extraction, and characterization to generate timing, power, and noise (.lib) models. The resulting LIB, LEF and GDSII files enable synthesis, STA, placement, routing, and signoff.

## Timing Characterization: Thresholds, Propagation Delay, and Transition Time

![Slew_Rise](https://img.shields.io/badge/Slew_Rise-Slew%20Low%20Rise%20Threshold%20Slew%20High%20Rise%20Threshols-orange)
![Slew_Fall](https://img.shields.io/badge/Slew_Fall-Slew%20Low%20Fall%20Threshold%20Slew%20High%20Fall%20Threshols-red)
![Delay_Rise](https://img.shields.io/badge/Delay_Rise-In%20Rise%20Threshold%20Out%20Rise%20Threshols-green)
![Delay_Fall](https://img.shields.io/badge/Delay_Fall-In%20Fall%20Threshold%20Out%20Fall%20Threshols-success)
> Timing characterization relies on specific voltage threshold definitions that are used to measure: Propagation delay and Transition time (slew)
---
## 📖 FLOORPLANNING Overview

Floorplanning is the first stage of the **Physical Design (PD)** flow. It determines:

- Core dimensions
- Die dimensions
- Utilization
- Aspect ratio
- Macro placement
- Decap placement
- Power distribution strategy
- I/O pin locations
- Placement blockages

A good floorplan significantly improves:

✅ Timing

✅ Routability

✅ Congestion

✅ Power Integrity

✅ Chip Area Utilization

---

## 🏗 Core and Die

#### Die - The complete silicon area allocated to the chip.

#### Core - The region inside the die where all standard cells, macros, and memories are placed.

---

## 📐 Utilization Factor
<img width="454" height="386" alt="image" src="https://github.com/user-attachments/assets/f6b71f74-cd83-41a3-833c-d52000589ff7" />

---

<img width="500" height="350" alt="image" src="https://github.com/user-attachments/assets/ea868ba8-66b8-4bcd-b8aa-e5e2a86c2628" />
<img width="500" height="350" alt="image" src="https://github.com/user-attachments/assets/a791a7bd-21b7-4614-a5a4-96cd140822ee" />

<img width="693" height="298" alt="image" src="https://github.com/user-attachments/assets/ac61bf9c-f12a-482b-920b-74687afd14b0" />



Utilization indicates the percentage of core area occupied by logic.

### Formula

```text
Utilization =
Netlist Area
------------
Core Area
```

### Example

```text
Netlist Area = 4 units²
Core Area    = 4 units²

Utilization = 4 / 4 = 1.0

100% Utilization
```

This means:

- Entire core is occupied
- No room for optimization
- No additional cells can be inserted
----
Another example


<img width="500" height="350" alt="image" src="https://github.com/user-attachments/assets/864dc24a-38e0-4a20-a275-bc8e650d6c71" />
<img width="500" height="350" alt="image" src="https://github.com/user-attachments/assets/1e3aac4a-4502-4735-9f23-06100516c8c2" />




### Industry Practice

Typical utilization:

```text
50% - 70%
```

This allows space for:

- Routing
- Buffers
- Timing fixes
- ECO modifications

---

## 📏 Aspect Ratio

Aspect Ratio determines the shape of the core.

### Formula

```text
Aspect Ratio =
Height
------
Width
```

### Square Core

```text
Height = 4
Width  = 4

AR = 1
```

✅ Square Shape

### Rectangular Core

```text
Height = 2
Width  = 4

AR = 0.5
```

✅ Rectangular Shape

---

## 🧩 Pre-Placed Cells (Macros)

Macros are large reusable IP blocks.

Examples:

- SRAM
- ROM
- Cache Memory
- PLL
- Multipliers
- Comparators
- Clock Generators

---
<img width="583" height="391" alt="image" src="https://github.com/user-attachments/assets/23096e29-cfd8-4c78-82ad-534d3d1c1bac" />

### Why Use Macros?

Instead of implementing a large block repeatedly:

```text
Build Once
Reuse Many Times
```

Advantages:

- Reduced design effort
- Faster implementation
- Better verification
- Reusability

---

### Macro Placement

Macros are placed according to connectivity requirements.
Benefits:

- Reduced wire length
- Better timing
- Lower congestion
- Easier routing

> Macro locations are fixed and cannot be moved by automatic placement tools.

---

## ⚡ Decoupling Capacitors

### Problem

When logic switches: 0 → 1
it requires instantaneous current.

Because power wires contain:

- Resistance (R)
- Capacitance (C)
- Inductance (L)

  the supply voltage may drop.
---

### Solution: Decaps

Place decoupling capacitors close to macros.

```text
Power Supply
     │
     ▼
   Decap
     │
     ▼
Logic Block
```

Benefits:

✅ Local charge storage

✅ Reduced IR drop

✅ Improved power integrity

✅ Stable switching operation

<img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/9d33b1a1-5c95-4a2e-82bf-7c716b230f60" />
<img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/2c8e0bf7-288e-4c08-8588-1edfdb26c000" />



---

## 🔋 Power Planning

Large chips contain multiple macros and millions of cells.

### Power Demand
If many nodes switch simultaneously: say from 
0 → 1
Power demand increases dramatically.
Voltage Drops
VDD decreases temporarily
Occurs when many circuits demand current simultaneously.

<img width="500" height="320" alt="image" src="https://github.com/user-attachments/assets/b06eb8ef-7bc2-4fe3-9e47-c145c0346a12" />
<img width="500" height="320" alt="image" src="https://github.com/user-attachments/assets/6418bf2a-c3c9-4a08-87de-efc8685dcbe1" />


### Ground Bounce
VSS rises temporarily
Occurs when many nodes discharge simultaneously.

Both effects can lead to:

- Timing failures
- Noise issues
- Signal integrity problems

---

## 🕸 Power Mesh

<img width="516" height="388" alt="image" src="https://github.com/user-attachments/assets/2231d6fd-318c-4a77-bc09-19b8ce0d539c" />

Power is distributed using a grid structure.

<img width="500" height="350" alt="image" src="https://github.com/user-attachments/assets/36de4c59-db24-4f59-aed8-f46279e89243" />
<img width="500" height="350" alt="image" src="https://github.com/user-attachments/assets/74eb9ead-0002-41f1-a58e-7c398592f211" />


Advantages:

- Uniform power distribution
- Low IR drop
- Reduced voltage droop
- Reduced ground bounce
- Improved reliability

---

## 📍 Pin Placement

Pins connect the chip to external signals.

## Typical Placement

```text
Inputs                     Outputs

DIN1      +----------+      DOUT1
DIN2      |          |      DOUT2
CLK1      |   CORE   |      DOUT3
CLK2      |          |      DOUT4
DIN3      +----------+      CLKOUT
```

Pin locations depend on:

- Connectivity
- Timing paths
- Macro positions
- Routing requirements

---
<img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/07394bcc-9a90-4f3e-81cb-85ff2e9da39b" />
<img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/919e18c1-b46d-4bc1-bbda-880d62ed4f93" />


## ⏰ Clock Pins vs Data Pins

Clock pins are generally larger than data pins.

Reason:

- Drive thousands of flip-flops
- Require lower resistance
- Require lower skew
- Operate continuously

```text
Clock Pin Width > Data Pin Width
```

---

## 🚫 Placement Blockages

Some regions are reserved and must not contain standard cells.

Examples:

- Macro boundaries
- Pin regions
- Reserved routing channels

<img width="646" height="391" alt="image" src="https://github.com/user-attachments/assets/e1bcc0db-9fdf-4156-a7f3-790613a8b1ec" />

---

## 🎯 Quick Revision - Floorplan

| Metric | Formula |
|----------|----------|
| Utilization | Netlist Area / Core Area |
| Aspect Ratio | Height / Width |
| AR = 1 | Square Core |
| AR ≠ 1 | Rectangular Core |


---

## ✅ Key Takeaways - Floorplan

Floorplanning forms the foundation of successful Physical Design.

Key activities include:

- Defining Core & Die dimensions
- Calculating Utilization
- Configuring Aspect Ratio
- Macro Placement
- Decap Insertion
- Power Mesh Creation
- Pin Placement
- Placement Blockage Definition

After floorplanning is completed, the design proceeds to:

```text
Placement → CTS → Routing → Signoff
```

**Floorplanning = Creating an optimized chip layout framework before Placement & Routing (P&R).**

---
---

## Placement, Routing and Library Characterization

![Standard_Cell_Library](https://img.shields.io/badge/Standard_Cell_Library-Physical%20Functional%20Timing%20information-blue)
![Placement](https://img.shields.io/badge/Placement-Logical_Gate%20Mapping%20to%20Std_Cell-green)
![Placement_Optimization](https://img.shields.io/badge/Placement_Optimization-Maintain%20Signal%20Integrity-orange)
![Routing](https://img.shields.io/badge/Routing-Metal%20Layers-red)
![Timing_Analysis](https://img.shields.io/badge/Timing_Analysis-Ideal%20Clks%20Before%20CTS-success)
---

### 📖 PLACE_n_ROUTE (PnR) Overview

The Placement and Routing (P&R) is the next stage that converts a synthesized gate-level netlist (obtained from floorplannig) into a physical layout that can be manufactured on silicon. During this stage, logical gates are mapped to physical standard cells, placed on the chip, optimized, and finally interconnected through routing. 

<img width="563" height="411" alt="image" src="https://github.com/user-attachments/assets/37d7b04f-7232-4c01-b486-7e6c80cdf59a" />


### Standard Cell Library
A standard cell library contains the physical, functional, and timing information of cells such as AND gates, OR gates, buffers, and flip-flops. 

**Library Information:**
- Cell dimensions (width & height)
- Pin locations
- Propagation delay
- Setup & hold times
- Slew and timing data
- Multiple drive-strength variants (X1, X2, X4, etc.)

Multiple drive-strength versions of the same cell are available to balance timing, power, and area.

     | Cell   |   Size |  Delay | 
     |--------|--------|--------| 
     | AND_X1 | Small  | Higher | 
     | AND_X2 | Medium | Lower  | 
     | AND_X4 | Large  | Lowest | 
     
Characteristics: 
- Larger cells have lower delay. 
- Larger cells can drive larger loads. 
- Larger cells consume more area and power.

<img width="676" height="198" alt="image" src="https://github.com/user-attachments/assets/103042e8-ce5d-4a68-a51c-87745e877ce9" />


---

### Placement 
After floorplanning, logical gates are mapped to physical standard cells and placed inside the core area. 
This process of assigning physical implementations to logical gates is called **binding the netlist with physical cells**

The objective is to:
- Minimize wire length
- Reduce delay
- Improve timing
- Avoid congestion
- Optimize area utilization

Connected cells are placed close together for better performance.

<img width="694" height="376" alt="image" src="https://github.com/user-attachments/assets/0999fffe-16fe-41b3-b191-da0e9c3419bc" />


---
### Placement Optimization
Long interconnects introduce resistance and capacitance, causing delay and signal degradation. To maintain signal integrity, **buffers/repeaters** are inserted along long routes.

```text
Before:
DIN ─────────────── FF

After:
DIN → BUF → BUF → FF
```
**Benefits:** include Better signal integrity, Reduced slew degradation, Improved timing

**Trade-off:** is Increased area and power

Critical timing paths may use **cell abutment**, where cells are placed adjacent to reduce wire delay.

```text
FF1 | Gate1 | Gate2 | FF2
```
Cell Abutment provides advantage in terms of Minimal wire delay, Higher performance and Better timing closure

<img width="703" height="392" alt="image" src="https://github.com/user-attachments/assets/6185d314-ab7d-4f13-87b9-543a9b76a8f4" />
<img width="699" height="402" alt="image" src="https://github.com/user-attachments/assets/15ab57f4-1970-429c-b705-50f07d1c3dc0" />
<img width="697" height="400" alt="image" src="https://github.com/user-attachments/assets/5d8c0ee4-23e0-4d87-9983-3c0ca9d66f06" />
<img width="705" height="393" alt="image" src="https://github.com/user-attachments/assets/2cb6ec6b-adc2-49cb-8692-416896fbff47" />




---

### Routing

Routing connects all placed cells using multiple metal layers while avoiding wire crossings and shorts.

---

### Timing Analysis
A preliminary timing check is performed after placement using ideal clocks to verify timing feasibility before CTS and routing.
**ideal clocks**: imply Clock delay is 0 and Clock skew is also 0

### OpenLane Placement Flow

1. **Global Placement**
   - Minimizes HPWL (Half-Perimeter Wire Length)
   - Reduces congestion

2. **Detailed Placement**
   - Legalizes placement
   - Removes overlaps
   - Aligns cells to standard rows

---
<img width="664" height="381" alt="image" src="https://github.com/user-attachments/assets/0b5d10fb-9001-4576-b92e-a4363845610a" />


### Key Takeaways - PnR

✅ Standard cell libraries provide physical and timing data.  
✅ Logical gates are mapped to physical standard cells.  
✅ Placement determines cell locations on the chip.  
✅ Placement Optimization minimizes wire length and improves timing.  
✅ Buffers improve signal integrity on long nets. 
✅ Cell abutment helps critical timing paths.  
✅ Routing connects cells using multiple metal layers.  
✅ Library characterization drives synthesis, placement, CTS, routing, and STA.  
✅ OpenLane uses **Global Placement → Detailed Placement (Legalization)**.


---
---

## Standard Cell Design Flow and Characterization

![Standard_Cell_Library](https://img.shields.io/badge/Standard_Cell_Library-Std%20Cells%20Macros%20IP%20De%Cap-blue)
![STD_Cell_Design_FLow](https://img.shields.io/badge/Std_Cell_Design_Flow-Inputs%20Design%20Characterization-green)
![Inputs](https://img.shields.io/badge/Inputs-PDKs%20User%20Defined-orange)
![Design](https://img.shields.io/badge/Design-Circuit%20Design%20Layout%20Design%20Characterization-red)
![Output](https://img.shields.io/badge/Output-CDL%20GDSII%20LEF%20LIB-success)
---
### Overview - STANDARD CELL DESIGN FLOW

In a digital IC design flow, the final placed-and-routed design consists of many logic elements such as:

- Inverters
- Buffers
- AND gates
- OR gates
- Flip-flops
- Latches
- Clock Gating Cells (ICG)

These logic elements are called **Standard Cells** and are stored inside a **Library**.

---

<img width="656" height="388" alt="image" src="https://github.com/user-attachments/assets/73c9a688-dfe7-417d-8178-ef8af04d3645" />


## Standard Cell Library

A library is a collection of cells used by synthesis, STA, CTS, placement, and routing tools.

The library contains:

- Standard cells
- Decap cells
- Macros
- IP blocks
  
### Library Characteristics

#### Each standard cell has a Different Functionality - A unique Logic Function

- Inverter (INV)
- Buffer (BUF)
- NAND
- NOR
- XOR
- Flip-Flop

#### Has Different Drive Strengths

- BUF_X1
- BUF_X2
- BUF_X4
- BUF_X8


| Higher Drive-Strength Cells | Lower Drive-Strength Cells |
|-----------------------------|----------------------------|
| Drive larger loads | Drive smaller loads |
| Have larger transistor widths | Have smaller transistor widths |
| Occupy more area | Occupy less area |
| Typically consume more power | Consume less power |
| Provide faster signal transitions | Suitable for lighter loads |
<img width="644" height="407" alt="image" src="https://github.com/user-attachments/assets/cf4f959a-e547-43c8-bf41-4b4dae64f9d5" />

#### Different Threshold Voltages (VT)

Libraries usually contain:

- LVT (Low VT)
- SVT (Standard VT)
- HVT (High VT)

| LVT (Low Threshold Voltage) Cells | HVT (High Threshold Voltage) Cells |
|-----------------------------------|------------------------------------|
| Faster switching speed | Slower switching speed |
| Higher leakage power | Lower leakage power |
| Often used in critical timing paths | Often used in non-critical timing paths |
| Higher performance | Better power efficiency |

These cells are heavily used during timing optimization and leakage recovery.


---
<img width="609" height="394" alt="image" src="https://github.com/user-attachments/assets/0aae2e7c-987b-456b-9504-d287b16cb556" />


## Standard Cell Library Design Flow
- 1. Inputs
- 2. Design Phase - Circuit Design, Layout Design, Characterization
- 3. Outputs from each Design Stage

## 1. Inputs Required for Cell Design

- Process Design Kit (PDK)
- User-Defined Specifications

### Process Design Kit (PDK)

The PDK is provided by the foundry.

It contains:
- DRC Rules (Design Rule Check)
- LVS Rules (Layout Versus Schematic)
- SPICE Models


#### DRC Rules (Design Rule Check)

Examples:

```text
Poly Width = 2λ
Poly Extension over Active = 3λ
Poly-to-Active Spacing = 1λ
```
These rules ensure manufacturability.

#### LVS Rules (Layout Versus Schematic)

Ensures:

```text
Layout ≡ Schematic
```

#### SPICE Models

Foundry-provided transistor models containing:

- Threshold voltage (VTH)
- Oxide thickness (TOX)
- Mobility parameters
- Junction capacitances
- Process-specific parameters

Used for circuit simulation and transistor modeling.



### User-Defined Specifications

These specifications come from the library architect or top-level designer.
- Cell Height : Determined by the spacing between Power Rail (VDD) and Ground Rail (VSS)
- Drive Strength Range : say from X1 to X10
- Supply Voltage : say 0.8, 1.0, 1.2
- Metal Layer Requirements : Libraries may be constrained to specific metal layers such as METAL1, METAL2, METAL3
- Pin Locations : Input/output pins may be required at predefined locations.
- Drawn Gate Length : Specified according to process-node requirements.

###### Cell Height

```text
Power Rail (VDD)
        ↓
     Cell Height
        ↑
Ground Rail (VSS)

All standard cells must maintain the same height.
```
<img width="459" height="417" alt="image" src="https://github.com/user-attachments/assets/c757e752-e2e9-4ed1-96a1-0df568b809df" />
<img width="445" height="397" alt="image" src="https://github.com/user-attachments/assets/c928e1f2-e9e6-44fa-b349-5c69b471208a" />
<img width="619" height="393" alt="image" src="https://github.com/user-attachments/assets/1d9ed633-3a29-473c-b12a-6171336f5ba6" />



---

## 2. Design Phase

The design stage consists of:

- Circuit Design
- Layout Design
- Characterization


### Circuit Design

Implement the required logic function using PMOS and NMOS transistors.

##### Transistor Sizing

Determine:

```text
Wp/Lp
Wn/Ln
```

to satisfy:

- Drive current requirements
- Switching threshold
- Delay targets
- Noise margin requirements

SPICE simulations are used extensively during sizing.

##### Output of Circuit Design

```text
CDL (Circuit Description Language)
```

### Layout Design

Convert the transistor-level schematic into a manufacturable physical layout.

#### Layout Design Flow
- Step 1: Implement the Function - Build the transistor-level circuit
- Step 2: Generate Network Graphs
  - PMOS Network Graph
  - NMOS Network Graph
- Step 3: Find Euler Path
  - Reduced diffusion breaks
  - Reduced area
  - Better performance
- Step 4: Create Stick Diagram
  - A → C → E → F → D → B
  - Poly gates are arranged according to the Euler path.
- Step 5: Generate Physical Layout
  - Create the layout while satisfying:
    - DRC rules
    - LVS requirements
    - Metal constraints
    - Pin constraints
    - User specifications
- Step 6: Draw Layout in CAD Tool - Magic Layout Tool

<img width="610" height="398" alt="image" src="https://github.com/user-attachments/assets/c8dfa201-f2f3-431b-8872-43d99cd20811" />
<img width="625" height="397" alt="image" src="https://github.com/user-attachments/assets/551ee20d-0d41-4770-b70a-03767aa4a007" />
<img width="619" height="402" alt="image" src="https://github.com/user-attachments/assets/628343c2-a1e3-45c8-ac2f-cb7aaadfe03b" />




### Outputs of Layout Design

##### GDSII

Industry-standard layout database used for fabrication.

Contains:

- All geometric information
- Mask data

##### LEF (Library Exchange Format)

Contains:

- Cell width
- Cell height
- Pin locations
- Placement information

Used by place-and-route tools.

##### Extracted SPICE Netlist from layout

Contains parasitic:

```text
R (Resistance)
C (Capacitance)
```

Used for accurate timing and power analysis.

<img width="638" height="417" alt="image" src="https://github.com/user-attachments/assets/1e1c2190-553a-4bc4-a1a8-43cc1689c4ca" />

### Characterization

Generate timing, power, and noise models required by EDA tools.
- Inputs to Characterization
- Characterization Flow
- Characterization Tool
- Characterization Outputs

#### Inputs to Characterization

- Layout (GDS/LEF)
- Circuit netlist
- Extracted SPICE netlist
- Subcircuits
- NMOS/PMOS model files

#### Characterization Flow
- Step 1 : Read transistor model files.
- Step 2 : Read extracted SPICE netlist.
- Step 3 : Recognize cell functionality - Inverter, Buffer, NAND, NOR etc.
- Step 4 : Read subcircuit descriptions.
- Step 5 : Apply power supplies - VDD and VSS
- Step 6 : Apply input stimulus.
  - Rising transition
  - Falling transition
  - Different slew rates
- Step 7 : Apply output load capacitance.
  - Different loads are swept during characterization.
- Step 8 : Run simulations.
          - .tran : for transient analysis.

<img width="656" height="435" alt="image" src="https://github.com/user-attachments/assets/1323d7f6-1098-4e52-ada8-472ee1651933" />
<img width="656" height="407" alt="image" src="https://github.com/user-attachments/assets/7ba179cd-13b7-4cd0-8e03-dfacca95e740" />
<img width="626" height="401" alt="image" src="https://github.com/user-attachments/assets/bb6b3f14-882c-4b84-84b3-f0623a4c3dd0" />


#### Characterization Tool

characterization software: GUNA

Inputs:

- SPICE models
- Extracted netlists
- Stimulus definitions
- Load capacitances

#### Characterization Outputs

- Timing models
- Power models
- Noise models

##### Timing Library (.lib)

Contains:

- Cell delay
- Rise delay
- Fall delay
- Transition time
- Setup time
- Hold time

Used by:

- Synthesis
- Static Timing Analysis (STA)
- Place-and-Route

##### Power Library

Contains:

- Dynamic power
- Internal power
- Leakage power

##### Noise Library

Contains:

- Noise characteristics
- Noise margins
- Crosstalk information

---
### Key Takeaways - STANDARD CELL CHARACTERIZATION

Although a standard cell such as an **inverter** appears simple, it undergoes a complete development flow involving:

✅ PDK and user specifications
✅ Circuit design
✅ Layout design
✅ Parasitic extraction
✅ Characterization


The final result is a characterized library containing **timing, power, and noise models (.lib)** 
along with **LEF** and **GDSII** files, which are essential for the digital backend design flow.

---
---

## Timing Characterization: Thresholds, Propagation Delay, and Transition Time

![Slew_Rise](https://img.shields.io/badge/Slew_Rise-Slew%20Low%20Rise%20Threshold%20Slew%20High%20Rise%20Threshols-orange)
![Slew_Fall](https://img.shields.io/badge/Slew_Fall-Slew%20Low%20Fall%20Threshold%20Slew%20High%20Fall%20Threshols-red)
![Delay_Rise](https://img.shields.io/badge/Delay_Rise-In%20Rise%20Threshold%20Out%20Rise%20Threshols-green)
![Delay_Fall](https://img.shields.io/badge/Delay_Fall-In%20Fall%20Threshold%20Out%20Fall%20Threshols-success)

---
### Overview - TIMING CHARACTERIZATION

Timing characterization relies on specific voltage threshold definitions that are used to measure:

- Propagation delay
- Transition time (slew)
- Current waveforms
- Timing models used in `.lib` files

These thresholds are important because characterization tools such as GUNA use them as input variables for timing, power, and noise library generation.

---
<img width="632" height="393" alt="image" src="https://github.com/user-attachments/assets/50ef64ff-c38d-4d0b-9e6c-35f32e46a020" />

### 1. Timing Threshold Definitions

A waveform requires reference points to measure its slope (slew) and delay.

#### Slew Threshold Parameters

##### Slew Low Rise Threshold

- Defines the lower reference point for a rising waveform.
- Typically:
  - 20% of VDD
  - Sometimes 30% of VDD

##### Slew High Rise Threshold

- Defines the upper reference point for a rising waveform.
- Typically:
  - 80% of VDD
  - Sometimes 70% of VDD

##### Slew Low Fall Threshold

- Lower threshold for a falling waveform typically 20% of VDD

##### Slew High Fall Threshold

- Upper threshold for a falling waveform typically 80% of VDD


---

#### Delay Threshold Parameters

Delay measurement requires one point on the input waveform and one point on the output waveform.

##### In Rise Threshold

- Input rising waveform reference point.
- Typically chosen at 50% of VDD.

##### Out Rise Threshold

- Output rising waveform reference point.
- Typically chosen at 50% of VDD.

---

##### In Fall Threshold

- Input falling waveform reference point.
- Typically chosen at 50% of VDD.

##### Out Fall Threshold

- Output falling waveform reference point.
- Typically chosen at 50% of VDD.

---


### 2. Propagation Delay

Propagation delay is defined as:

```text
Delay
= Time(Output Threshold)
  - Time(Input Threshold)

Delay = Out - In
```

Since the output occurs after the input, the delay should normally be positive.

---

##### Example: Positive Delay

Given:

```text
In Rise Threshold Time  = 3.207 ns
Out Fall Threshold Time = 3.230 ns

Delay = 3.230 − 3.207
Delay = 23 ps
```

This is a valid propagation delay.

<img width="643" height="403" alt="image" src="https://github.com/user-attachments/assets/a695d3de-3700-42af-a371-50fadad1f020" />


---

### 3. Negative Delay Problem

Negative delays are generally undesirable and indicate either:

1. Incorrect threshold selection
2. Poor circuit implementation

---

#### Case 1: Improper Threshold Selection

Suppose threshold points are moved upward on the waveform.

```text
Input Threshold Time  = 3.263 ns
Output Threshold Time = 3.221 ns

Delay = 3.221 − 3.263
Delay = −42 ps
```
<img width="1191" height="682" alt="image" src="https://github.com/user-attachments/assets/b731544e-8d00-41b9-99ae-0d3d2c8613c8" />

##### Reason

The threshold points were chosen incorrectly, causing the output crossing point to appear before the input crossing point.

---

#### Case 2: Excessive Wire Delays

Even with correct threshold choices, long interconnects can create heavily degraded waveforms.

Example:

```text
Input Threshold Time  = 4.215 ns
Output Threshold Time = 4.207 ns

Delay = 4.207 − 4.215
Delay = −8 ps
```
<img width="1243" height="693" alt="image" src="https://github.com/user-attachments/assets/012b4be0-e315-434e-b9b4-405605615658" />

##### Possible Causes

- Large wire parasitics
- Excessive routing delay
- Poor physical placement
- Long distance between cells

---

#### Important Observation

Negative delays can occur due to:

- Incorrect timing threshold definitions
- Poor layout implementation
- Excessive interconnect delay

Therefore:

> Correct threshold selection and good circuit design are essential during characterization.

---

### 4. Transition Time (Slew) Measurement

Transition time represents how fast a signal changes state.

#### Rise Transition

```text
Rise Transition
= Time(80% VDD)
  - Time(20% VDD)

Rise Slew
= Slew High Rise Threshold
  - Slew Low Rise Threshold
```

---

#### Fall Transition

```text
Fall Transition
= Time(80% VDD)
  - Time(20% VDD)

Fall Slew
= Slew High Fall Threshold
  - Slew Low Fall Threshold
```
<img width="1307" height="697" alt="image" src="https://github.com/user-attachments/assets/d0e804c2-bb0b-4e60-aa15-e2bbdbd1b0cf" />

---


### Key Takeaways - TIMING CHARACTERIZATION

Although a standard cell such as an **inverter** appears simple, it undergoes a complete development flow involving:

✅ Timing characterization depends on properly defined threshold points.
✅ 50% thresholds are widely used for propagation delay calculations.
✅ 20%-80% thresholds are widely used for slew calculations.
✅ Delay should ideally be positive.
✅ Negative delays can result from:
  - Wrong threshold selection
  - Excessive wire parasitics
  - Poor circuit layout

---


#### 📂 Resources
```text
└── resources/
    ├── lecture_videos
    └── references.md
```
