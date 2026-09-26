# 🖥️ VLSI Physical Design: Floorplanning Fundamentals

![Domain](https://img.shields.io/badge/Domain-VLSI-blue)
![Flow](https://img.shields.io/badge/Flow-Physical%20Design-green)
![Stage](https://img.shields.io/badge/Stage-Floorplanning-orange)
![License](https://img.shields.io/badge/License-MIT-red)
![Status](https://img.shields.io/badge/Status-Learning%20Project-success)

> A comprehensive study of **VLSI Physical Design Floorplanning**, covering Core & Die estimation, Utilization Factor, Aspect Ratio, Macro Placement, Decoupling Capacitors, Power Planning, Pin Placement, and Placement Blockages.

---
# 📖 Overview

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



## ✅ Summary

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

---

## 🎯 Quick Revision

| Metric | Formula |
|----------|----------|
| Utilization | Netlist Area / Core Area |
| Aspect Ratio | Height / Width |
| AR = 1 | Square Core |
| AR ≠ 1 | Rectangular Core |

**Floorplanning = Creating an optimized chip layout framework before Placement & Routing (P&R).**
#### 📂 Resources

```text
└── resources/
    ├── lecture_videos
    └── references.md
```

---

