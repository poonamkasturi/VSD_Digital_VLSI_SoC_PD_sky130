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

---

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

#### 📂 Resources

```text
└── resources/
    ├── lecture_videos
    └── references.md
```
