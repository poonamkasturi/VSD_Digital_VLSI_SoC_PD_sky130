### 1. SYNTHESIS COMMAND EXECUTED
```
% run_synthesis
```

Values taken for certain switches for the flow of execution of the design as per the priority of the *.tcl file

### floorplan.tcl - openlane tool default file - lowest priority
~/Desktop/works/tools/openlane_working_dir/openlane/configurations/floorplan.tcl

<img width="1586" height="835" alt="VirtualBox_vsdworkshop_24_09_2026_16_23_55 floorplan_tcl" src="https://github.com/user-attachments/assets/35711140-caa2-48bd-a00f-bd7e26c0cd7d" />

- Aspect Ratio = 1
- core utilization = 50
- FP_TO_VMETAL = 3
- FP_TO_HMETAL = 4
- clock = 
---

### design specific config file - higher priority than floorplan.tcl (tool default file)
File is in the specific designfolder
in our case - picorv32a

~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/

Modified values of some switches
<img width="1280" height="674" alt="VirtualBox_vsdworkshop_23_09_2026_20_35_35 config_tcl_picorv32a" src="https://github.com/user-attachments/assets/d8a39f0d-027d-4683-87c0-c116118ffeb9" />

- Aspect Ratio = 1
- core utilization = 65
- FP_TO_VMETAL = 4
- FP_TO_HMETAL = 3
- clock = 10.000

---

### Technology specific config file
~/Desktop/works/tools/openlane_working_dir/openlane/designs/picorv32a/sky130A_sky130_fd_sc_hd_config.tcl

<img width="1280" height="674" alt="VirtualBox_vsdworkshop_23_09_2026_20_36_15 sky130config_tcl_picorv32a" src="https://github.com/user-attachments/assets/d2bd81f2-22b2-4bfe-944b-2bcf6deded4b" />

- Aspect Ratio = 1
- core utilization = 50
- FP_TO_HMETAL = NOT MENTIONED
- FP_TO_VMETAL = NOT MENTIONED
- clock = 12.000
  
---

### config.tcl  actually considered when the flow is executed on the selected design (picorv32a)
It is in folder 
#### ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/date/

showing values taken up by the run for some of the environment switches as

- Aspect Ratio = 1
- core utilization = 50
- FP_TO_VMETAL = 4
- FP_TO_HMETAL = 3
- clock = 12.00

<img width="1586" height="835" alt="Hmetal VMetal" src="https://github.com/user-attachments/assets/53f13321-b1c1-41b9-953a-26dfb2456214" />
<img width="1586" height="835" alt="run config clk" src="https://github.com/user-attachments/assets/57c99e76-3b64-4d9c-9522-125ba66fea81" />


The highlighted values indicate the **priority** of files in **descending order**
**sky130A_sky130_fd_sc_hd_config.tcl** --   **config.tcl (~/designs/picorv32a)** --  **floorplan.tcl (~/openlane/configuration)**

---
---

### 2. FLOORPLAN COMMAND EXECUTED

```
% run_floorplan
```
<img width="1280" height="674" alt="VirtualBox_vsdworkshop_23_09_2026_21_49_07 Check Legality" src="https://github.com/user-attachments/assets/3b670bb2-7031-4992-b30a-0cd9d3c87ad7" />
Checking legality for HPLW - Half Pitch Line Width

Logs created after floorplan - giving details like die area and chip area
<img width="1280" height="674" alt="VirtualBox_vsdworkshop_23_09_2026_20_42_30 DieArea" src="https://github.com/user-attachments/assets/c42953de-cafc-4cfd-8fb4-d847869c8a0e" />


<img width="1280" height="674" alt="VirtualBox_vsdworkshop_23_09_2026_20_32_07 ioplacer_log" src="https://github.com/user-attachments/assets/05568328-9f16-43a7-8441-1a7ab6269d05" />

> ioplacer log file -  does not mentions the HP_TO_VMETAL and HP_TO_HMETAL layers as mentioned in the lecture videos

- though same could be seen in def files and also in magic
- Point to note -
    - as mentioned in video the metal layers will be one higher than what has been specified in the file
    - It does not appear to be happening - Rather it is one less 
    - Probably due to change of version used in the video lectures and what we are working with -
    - This is my interpretation - i can't authenticate it as of now - due to limited knowledge at present

<img width="1280" height="768" alt="VB_vsd_memory_Metal_Layer" src="https://github.com/user-attachments/assets/f5a068c4-a7ac-4077-aa4b-2aa7671b021e" />

### 2a. MAGIC - TO VIEW FLOORPLAN SO CREATED
##### command to be executed To view the layout in magic
```
~/Desktop/work/tools/openlane_working_directory/openlane/designs/picorv32a/runs/date/results/floorplan$ magic -T ~/Desktop/ork/tools/openlane_working_directory/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
```

<img width="1280" height="674" alt="10  VirtualBox_vsdworkshop_23_09_2026_20_54_29 Floorplan_Magic" src="https://github.com/user-attachments/assets/d7194dad-d82e-4f95-aa12-d64cdcc2cef1" />

The input output pins are equi-spaced and all the standard cells are collated at the bottom left corner

<img width="1280" height="674" alt="11  VirtualBox_vsdworkshop_23_09_2026_21_09_48 euispaced pins" src="https://github.com/user-attachments/assets/d1cd1635-bba6-4602-862a-1f8aff99abc4" />

<img width="1280" height="674" alt="12  VirtualBox_vsdworkshop_23_09_2026_21_11_16 equispaced pins CellClustered" src="https://github.com/user-attachments/assets/f301092e-603e-40b6-9959-ad7985d995be" />

The horizontal IO pins are attached to metal 2 -- 1 less than FP_TO_HMETAL (3) as per config.tcl in design runs folder

<img width="1280" height="674" alt="13  VirtualBox_vsdworkshop_23_09_2026_21_14_55 HcomponentSelect_what" src="https://github.com/user-attachments/assets/00a67932-0319-4dd6-9a48-717432fa2816" />

The vertical IO pins are attached to metal 3 -- 1 less than FP_TO_VMETAL (4) as per config.tcl in design runs folder

<img width="1280" height="674" alt="14  VirtualBox_vsdworkshop_23_09_2026_21_17_01 VcomponentSelect_what" src="https://github.com/user-attachments/assets/bf5dee84-929e-409b-8b5e-fca6bf048217" />

Tap Cells diagonally alligned

<img width="1280" height="674" alt="15  VirtualBox_vsdworkshop_23_09_2026_21_21_05 tap cells" src="https://github.com/user-attachments/assets/3c0184eb-67b5-4377-9df0-adda51fea031" />

DeCap Cells at the IO pads

<img width="1280" height="674" alt="16  VirtualBox_vsdworkshop_23_09_2026_21_23_58 decapCells" src="https://github.com/user-attachments/assets/7e9f3f28-f887-408f-b61f-b9893c927782" />

one of the Standard cells collated at the bottom left corner
<img width="1280" height="674" alt="17  VirtualBox_vsdworkshop_23_09_2026_21_30_30 standardCellCluster" src="https://github.com/user-attachments/assets/2f1bc681-7edf-40a2-9fa8-d9ace5fb8620" />
another Standard cell collated at the bottom left corner
<img width="1280" height="674" alt="18  VirtualBox_vsdworkshop_23_09_2026_21_36_10 instance StandardCell" src="https://github.com/user-attachments/assets/dc49a8a9-db58-40f4-a561-233db76c3078" />


### 3. PLACEMENT COMMAND EXECUTED and MAGIC - TO VIEW FLOORPLAN SO CREATED
```
% run_placement
```
##### command to be executed To view the layout in magic
```
~/Desktop/work/tools/openlane_working_directory/openlane/designs/picorv32a/runs/date/results/placement$ magic -T ~/Desktop/ork/tools/openlane_working_directory/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```
set :: env(SYNTH_   )  was default
<img width="1280" height="674" alt="19  VirtualBox_vsdworkshop_23_09_2026_21_58_59 standardCell_Placement" src="https://github.com/user-attachments/assets/bf80e008-e6e8-4dce-bf2a-65286991a964" />

Expanded view showing cell abutment

<img width="1280" height="674" alt="20  VirtualBox_vsdworkshop_23_09_2026_22_03_28 expanded view placement" src="https://github.com/user-attachments/assets/1aee3eba-a0da-40c0-ade5-0fdef4896606" />

### 4. Exploring various switch values
1. set :: env(FP_TO_MODE) 2
   changes the way IO pins are placed around the periphery of the chip

<img width="1280" height="674" alt="21  VirtualBox_vsdworkshop_23_09_2026_22_21_47 changes_on_Fly_pinSetting_2" src="https://github.com/user-attachments/assets/bf43cc97-a9ee-4cfa-8756-190d9f78b3b9" />

2. exploring with set :: env(SYNTH_   )  
