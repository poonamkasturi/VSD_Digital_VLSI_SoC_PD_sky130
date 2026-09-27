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

### 1. FLOORPLAN COMMAND EXECUTED

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
