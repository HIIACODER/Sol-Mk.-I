# Sol Mk. I: A simple rocket flight controller
This project aims to create a flight controller for TVC, airbrakes, and fin control, that can charge and run off a 2 cell lipo battery and connect to it using an XT-30 connector. It uses a BMP581 barometer and an 
My goal with this project was to learn how to route properly and effectively on a PCB including how to manage decoupling caps and general power routing because that is what I struggle with. I also wanted a flight computer to use for my projects and test + learn C on.
I spent above 70 hours making this, and even more uncounted hours of research and thought, so I welcome any feedback.

This project should:
- help me develop a base to apply to future projects
- be a flight controller that I can reliably put in rockets


## PCB
Here is my PCB! This PCB was designed in KiCAD.

### General PCB design images

Schematic:

<img width="3508" height="2480" alt="image" src="https://github.com/user-attachments/assets/7dd0c605-c366-4a94-9c74-cea02f5d6d1d" />

Top View (3d render):

<img width="562" height="582" alt="image" src="https://github.com/user-attachments/assets/e36d27a2-5ac2-4095-b526-1fc7dd34bf98" />

Bottom View (3d render):

<img width="598" height="596" alt="image" src="https://github.com/user-attachments/assets/9c4dd236-d2da-4052-b6d5-1894cbeb4c42" />

PCB Design:

<img width="832" height="870" alt="image" src="https://github.com/user-attachments/assets/c99aa2f6-5e37-4e13-ade3-791ec1a67f69" />

First Layer: 

<img width="852" height="886" alt="image" src="https://github.com/user-attachments/assets/6b5f12bd-bdea-4d57-b88d-115503c1a9a2" />

Second Layer:

<img width="854" height="890" alt="image" src="https://github.com/user-attachments/assets/bf4da11f-c86e-4d0b-8ffd-88ca5f30dc9d" />

Third Layer: 

<img width="870" height="876" alt="image" src="https://github.com/user-attachments/assets/9b267dca-309f-4815-bfa1-3fa5bee36cde" />

Fourth Layer: 

<img width="888" height="948" alt="image" src="https://github.com/user-attachments/assets/6e843784-c247-40f6-88b5-237b76c85cb1" />

Fifth Layer:

<img width="930" height="954" alt="image" src="https://github.com/user-attachments/assets/c11ddeb6-716b-4b12-896a-de950f720a23" />

Sixth Layer:

<img width="882" height="916" alt="image" src="https://github.com/user-attachments/assets/a5ae0d89-2dba-49f7-ae38-f8c3b1da8a66" />

### Layer Stackup
The board contains 6 layers. The purpose of all layers listed below.

| Layer | Description |
| :--- | :--- |
| 1 | Main routing layer |
| 2 | First ground layer for reference and signal separation |
| 3 | Second ground layer for reference and signal separation |
| 4 | Main Power Routing Layer |
| 5 | Third ground layer for reference and signal separation |
| 6 | Overflow routing layer |
### Flashing Instructions
Here are steps to flash a file to the MCU! 
1. Hold down the BOOTSEL button (the only button on the board) while plugging the board into your computer via USBC
2. The board will show up as a USB mass storage device
3. Compile your .uf2 binary file through external methods (C/C++ SDK, MicroPython, CircuitPython, etc)
4. Drag your compiled .uf2 file onto the drive. The board should automatically reboot and run the newly uploaded firmware!

## BOM

All SMD parts utilize 0402 passives, with 2 0603 for the MCU power to minimize board surface area. JLCPCB / LCSC part numbers are included below for reference.

| Item | Component / Description | Qty | Designators | Footprint | JLCPCB Part # | Unit Price (USD) |
| :--- | :--- | :---: | :--- | :--- | :--- | :---: |
| 1 | 1uF Capacitor | 3 | `C1, C10, C14` | `C_0402` | `C29266` | $0.0049 |
| 2 | 10uF Capacitor | 12 | `C11, C12, C13, C16, C17, C18, C2, C4, C5, C7, C8, C9` | `C_0402` | `C315248` | $0.0269 |
| 3 | 100nF Capacitor | 17 | `C15, C19, C20, C22, C24, C28, C29, C30, C31, C32, C33, C34, C35, C36, C40, C41, C42` | `C_0402` | `C1525` | $0.0029 |
| 4 | 10nF Capacitor | 1 | `C21` | `C_0402` | `C15195` | $0.0037 |
| 5 | 2.2uF Capacitor | 1 | `C23` | `C_0402` | `C444845` | $0.0094 |
| 6 | 4.7uF Capacitor | 2 | `C25, C26` | `C_0603` | `C19666` | $0.0150 |
| 7 | 47nF Capacitor | 1 | `C3` | `C_0402` | `C307434` | $0.0077 |
| 8 | 4.7uF Capacitor | 2 | `C37, C6` | `C_0402` | `C23733` | $0.0113 |
| 9 | 15pF Capacitor | 2 | `C38, C39` | `C_0402` | `C106997` | $0.0013 |
| 10 | TF-01A MicroSD Card Socket | 1 | `CARD1` | `TF-SMD_TF-01A` | `C91145` | $0.1931 |
| 11 | XT30UPB-M Power Connector | 1 | `CN1` | `CONN-TH_XT30UPB-M` | `C428721` | $0.2635 |
| 12 | USBLC6-2SC6 USB Protection IC | 1 | `D1` | `SOT-23-6_L2.9-W1.6-P0.95-LS2.8-BL` | `C7519` | $0.1559 |
| 13 | LED | 1 | `D2` | `LED0603-RD` | `C19273150` | $0.0114 |
| 14 | Green Signal LED | 1 | `D4` | `LED0603-GREEN` | `C22371297` | $0.0147 |
| 15 | 3-Pin Male Header | 5 | `H5, H6, H7, H8, H9` | `HDR-TH_3P-P2.54mm` | `C2937625` | $0.0200 |
| 16 | 1uH Inductor | 1 | `L1` | `APH252012C3R3MP01` | `C42455356` | $0.0365 |
| 17 | 3.3uH Inductor | 1 | `L2` | `B201610S3R3-101-T` | `C42411119` | $0.3377 |
| 18 | 5.1kΩ Resistor | 2 | `R1, R2` | `R0402` | `C25905` | $0.0014 |
| 19 | 10kΩ Resistor | 12 | `R6, R8, R9, R10, R11, R18, R19, R20, R21, R22, R23, R24` | `R0402` | `C25744` | $0.0010 |
| 20 | 10kΩ Thermistor | 1 | `TH1` | `R0402` | `C25744` | $0.0010 |
| 21 | 75kΩ Resistor | 1 | `R12` | `R0402` | `C2909383` | $0.0011 |
| 22 | 24kΩ Resistor | 1 | `R13` | `R0402` | `C25769` | $0.0012 |
| 23 | 100kΩ Resistor | 2 | `R14, R15` | `R0402` | `C25741` | $0.0011 |
| 24 | 105kΩ Resistor | 1 | `R16` | `R0402` | `C25742` | $0.0021 |
| 25 | 20kΩ Resistor | 1 | `R17` | `R0402` | `C25765` | $0.0011 |
| 26 | 1kΩ Resistor | 3 | `R7, R25, R26` | `R0402` | `C11702` | $0.0013 |
| 27 | 33Ω Resistor | 1 | `R27` | `R0402` | `C25105` | $0.0011 |
| 28 | 27Ω Resistor | 2 | `R28, R29` | `R0402` | `C2909343` | $0.0012 |
| 29 | 5.23kΩ Resistor | 1 | `R3` | `R0402` | `C2933105` | $0.0013 |
| 30 | 130Ω Resistor | 1 | `R30` | `R0402` | `C477610` | $0.0038 |
| 31 | 30.1kΩ Resistor | 1 | `R4` | `R0402` | `C29402` | $0.0012 |
| 32 | 383Ω Resistor | 1 | `R5` | `R0402` | `C49653730` | $0.0008 |
| 33 | TS-1088 Tactile Switch | 1 | `SW1` | `SW-SMD_L3.9-W3.0-P4.45` | `C720477` | $0.0516 |
| 34 | BQ25883RGER Battery Charger IC | 1 | `U1` | `VFQFPN-24_L4.0-W4.0-P0.50-BL-EP2.8` | `C544362` | $4.2249 |
| 35 | RP2354A Microcontroller | 1 | `U2` | `QFN-60_L7.0-W7.0-P0.40` | `C41378174` | $1.2562 |
| 36 | TPS82130SILR 3.3V Buck Converter | 2 | `U3, U4` | `USIP-8_L3.0-W2.8-P0.65` | `C473914` | $3.3384 |
| 37 | BMP581 Barometric Pressure Sensor | 1 | `U5` | `LGA-10_L2.0-W2.0-P0.50` | `C5362283` | $2.2539 |
| 38 | ICM-42688-P IMU Sensor | 1 | `U6` | `LGA-14_L3.0-W2.5-P0.50` | `C1850418` | $20.8264 |
| 39 | 12MHz Crystal | 1 | `U7` | `CRYSTAL-SMD_4P-L3.2-W2.5` | `C20625731` | $0.3817 |
| 40 | USB-C 16-Pin Connector | 1 | `USB1` | `USB-C-SMD_TYPE-C-16PIN-2MD-073` | `C2765186` | $0.0728 |

### Prices on JLCPCB:
NOTE: THESE PRICES DO NOT CONTAIN TAXES, AND ARE PRONE TO CHANGES
Parts Price (for 2): $96.3767

PCB (5x): $2.0 (if done without PCBA)

PCB (5x): $32.00

PCBA (2x): $194.03

Shipping on Global Standard Direct Line: $12.62
