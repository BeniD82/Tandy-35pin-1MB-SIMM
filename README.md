# Tandy 35 Pin SIMM Module Module

<img src="https://github.com/BeniD82/Tandy-35pin-1MB-SIMM/blob/main/Images/Revision3_Front.PNG" width="60%"> 
<img src="https://github.com/BeniD82/Tandy-35pin-1MB-SIMM/blob/main/Images/Revision3_Back.PNG" width="60%"> 



## Introduction

Several vintage laptops designed by Panasonic, rebadged under a number of labels, leverage non-standard 35 pin SIMM modules for system memory expansion (to be used as additional EMS or XMS memory depending on the system). Due to the unusual nature and limited use of 35 pin SIMM modules, it is practically impossible source these today. To fill that gap I've recreated the SIMM and I am providing the design files so folks can create their own modules in order to upgrade their systems.  

I'd like to give a shoutout to James Folwer who still had one of these modules in his possession and who also pointed me to the Panasonic CF-270 technical service manual which greatly assisted with the recreation.

Devices known to use 35 pin SIMM modules (not an exhaustive list, there are probably more):

<b>Tandy:</b>
<br>1500HD
<br>2810HD
<br>3810HD 

<b>Panasonic Business Partner:</b>
<br>CF-170 
<br>CF-270 
<br>CF-370

<b>Grid:</b>
<br>Model 1755

## Supported DRAM Modules

DRAM chips should be 256Kx4 in size (128KB each) and should use the SOJ-20 (26) form factor (these are quite common FPM memory chips). Larger modules such as 1Mx4 are also supported since pin #5 for each DRAM footprint is pulled to ground on the PCB (see section about pin #5). A table of manufacturers and compatible modules that might work, barring they are using the SOJ-20 (26) form factor, can be found below:


| Manufacturer      | 256Kx4 (1M) | 1Mx4 (4M) |
| ----------------- | ----------- | --------- |
| Fujistu<br>MB     | 81C4256     | 814400    |
| Goldstar<br>GM    | 71C4256     | 71C4400   |
| Hitachi<br>HM     | 514256      | 514400    |
| Hyundai<br>HY     | 534256      | 514400    |
| Micron<br>MT      | 4C4256      | 4C4001    |
| Mitsubishi<br>M5M | 44256       | 44400     |
| Motorola<br>MCM   | 514256      | 514400    |
| NEC<br>µPD/D      | 424256      | 424400    |
| OKI<br>MSM        | 514256      | 514400    |
| Samsung<br>KM     | 44C256      | 44C1000   |
| TI<br>TMS         | 44C256      | 44400     |
| Toshiba<br>TC     | 514256      | TC514400  |


## Bill of Materials

| Location | Part | Case Code | Part number |
| --- | --- | --- | --- |
| U1, U2, U3, U4, U5, U6, U7, U8 | 256Kx4 or 1Mx4 DRAM Module | SOJ-20 (26) | See Above |
| C1, C2, C3, C4, C5, C6, C7, C8 | 0.047uF MLCC Capacitor 25V 5% Tolerance| 0805 | Kyrocera/AVX 08055C473JAT4A |

## PCB Manufacturing and Assembly

The Gerber files necessary for manufacturing the PCB were generated based on the parameters provided by JLCPCB as well as PCBWay. The board is a four layer board (layers top to bottom: F.Cu, In1.Cu, In2.Cu, B.Cu). I would recommend ENIG plating as I feel it makes soldering the chips somewhat easier (still a pain though, be warned). In addition, when specifying the board parameters, ensure to select a board width of <b><u>1.2mm</u></b>

## Using 1Mx4 DRAM Chips and Pin #5 Caveat

Pin #5 on each DRAM footprint is connected directly to ground to allow the SIMM module to be populated with larger than 256Kx4 memory chips if desired e.g. M5M44400CJ (1Mx4). On most 256Kx4 DRAM modules pin #5 is NC (not electrically connected) whereas on 1Mx4 chips pin 5 is assigned to address line A9. By permanently pulling A9 low we ensure data is always returned from the correct location in memory. On certain 256Kx4 chips this pin allows for a special diagnostic mode to be activated if pulled to ground (TI TMS44C256 specifically). If using DRAM which provides diagnostic function on pin #5, that pin cannot be pulled to ground but should be left floating. Pin can be isolated from ground by cutting the jumper JP1 on Rev3 PCBs (Rev2 is permanently pulled to ground).

## Image Gallery

| ![](https://github.com/BeniD82/Tandy-35pin-1MB-SIMM/blob/main/Images/1500HD.jpg) | ![](https://github.com/BeniD82/Tandy-35pin-1MB-SIMM/blob/main/Images/1500HD-2.jpg) |
| :---------------: | :---------------: |
![](https://github.com/BeniD82/Tandy-35pin-1MB-SIMM/blob/main/Images/2810HD.jpg)

## Version History:

*   Revision 3 (current)    
    + Added Jumper JP1 to allow pin #5 to be disconnected from GND if needed (to support DRAM that uses pin #5 for diagnostic mode)
*   Revision 2   
    + Tweaked IC leg pitch on footprints that were not properly aligned
*   Revision 1
    + Initial release (files not provided)
