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

| Designator | Footprint | Quantity | Value | LCSC Part # | Unit Price (USD) | Line Total (USD) |
| :--- | :--- | :---: | :--- | :--- | :---: | :---: |
| C1, C10, C14 | C_0402 | 3 | 1uF | C29266 | 0.0049 | 0.0147 |
| C11, C12, C13, C16, C17, C18, C2, C4, C5, C7, C8, C9 | C_0402 | 12 | 10uF | C315248 | 0.0257 | 0.3084 |
| C15, C19, C20, C22, C24, C28, C29, C30, C31, C32, C33, C34, C35, C36, C40, C41, C42 | C_0402 | 17 | 100nF | C1525 | 0.0025 | 0.0425 |
| C21 | C_0402 | 1 | 10nF | C15195 | 0.0037 | 0.0037 |
| C23 | C_0402 | 1 | 2.2uF | C444845 | 0.0094 | 0.0094 |
| C25, C26 | C_0603 | 2 | 4.7uF | C19666 | 0.0144 | 0.0288 |
| C3 | C_0402 | 1 | 47nF | C307434 | 0.0077 | 0.0077 |
| C37, C6 | C_0402 | 2 | 4.7uF | C23733 | 0.0077 | 0.0154 |
| C38, C39 | C_0402 | 2 | 15pF | C106997 | 0.0013 | 0.0026 |
| CARD1 | TF-SMD_TF-01A | 1 | TF-01A | C91145 | 0.1926 | 0.1926 |
| CN1 | CONN-TH_XT30UPB-M | 1 | XT30UPB-M | C428721 | 0.2630 | 0.2630 |
| D1 | SOT-23-6_L2.9-W1.6-P0.95-LS2.8-BL | 1 | USBLC6-2SC6 | C7519 | 0.1558 | 0.1558 |
| D2 | C19273150_LED0603-RD | 1 | LED | C19171390 | 0.0063 | 0.0063 |
| D4 | C22371297_LED0603-RD_GREEN | 1 | Signal LED1 | C22371297 | 0.0147 | 0.0147 |
| H5 | C2937625_HDR-TH_3P-P2_54-V-M_PZ254V-11-03P | 1 | SERVOH1 | C2937625 | 0.0193 | 0.0193 |
| H6 | C2937625_HDR-TH_3P-P2_54-V-M_PZ254V-11-03P | 1 | SERVOH2 | C2937625 | 0.0193 | 0.0193 |
| H7 | C2937625_HDR-TH_3P-P2_54-V-M_PZ254V-11-03P | 1 | SERVON1 | C2937625 | 0.0193 | 0.0193 |
| H8 | C2937625_HDR-TH_3P-P2_54-V-M_PZ254V-11-03P | 1 | SERVON2 | C2937625 | 0.0193 | 0.0193 |
| H9 | C2937625_HDR-TH_3P-P2_54-V-M_PZ254V-11-03P | 1 | DEBUG | C2937625 | 0.0193 | 0.0193 |
| L1 | C42455356_IND-SMD_APH252012C3R3MP01 | 1 | 1uH | C42455356 | 0.0364 | 0.0364 |
| L2 | C42411119_IND-SMD_L2_0-W1_6_AOTA-B201610S3R3-101-T | 1 | 3.3uH | C42411119 | 0.2955 | 0.2955 |
| R1, R2 | R0402 | 2 | 5.1K | C25905 | 0.0014 | 0.0028 |
| R10, R11, R18, R19, R20, R21, R22, R23, R24, R6, R8, R9, TH1 | R0402 | 13 | 10K | C25744 | 0.0015 | 0.0195 |
| R12 | R0402 | 1 | 75K | C2909383 | 0.0011 | 0.0011 |
| R13 | R0402 | 1 | 24K | C25769 | 0.0012 | 0.0012 |
| R14, R15 | R0402 | 2 | 100K | C25741 | 0.0009 | 0.0018 |
| R16 | R0402 | 1 | 105K | C25742 | 0.0021 | 0.0021 |
| R17 | R0402 | 1 | 20K | C25765 | 0.0010 | 0.0010 |
| R25, R26, R7 | R0402 | 3 | 1K | C11702 | 0.0011 | 0.0033 |
| R27 | R0402 | 1 | 33 | C25105 | 0.0010 | 0.0010 |
| R28, R29 | R0402 | 2 | 27 | C2909343 | 0.0012 | 0.0024 |
| R3 | R0402 | 1 | 5.23K | C2933105 | 0.0013 | 0.0013 |
| R30 | R0402 | 1 | 130 | C477610 | 0.0016 | 0.0016 |
| R4 | R0402 | 1 | 30.1K | C29402 | 0.0012 | 0.0012 |
| R5 | R0402 | 1 | 383 | C49653730 | 0.0008 | 0.0008 |
| SW1 | C720477_SW-SMD_L3_9-W3_0-P4_45 | 1 | SW_Push | C720477 | 0.0508 | 0.0508 |
| U1 | VFQFPN-24_L4.0-W4.0-P0.50-BL-EP2.8 | 1 | BQ25883RGER | C544362 | 5.3682 | 5.3682 |
| U2 | C41378174_QFN-60_L7_0-W7_0-P0_40-TL-EP3_4 | 1 | RP2354A | C41378174 | 1.2486 | 1.2486 |
| U3, U4 | C473914_USIP-8_L3_0-W2_8-P0_65-TL-EP | 2 | TPS82130SILR | C473914 | 3.1175 | 6.2350 |
| U5 | LGA-10_L2.0-W2.0-P0.50-TL_BMP581 | 1 | BMP581 | C5362283 | 2.3144 | 2.3144 |
| U6 | C1850418_LGA-14_L3_0-W2_5-P0_50-TL | 1 | ICM-42688-P | C1850418 | 24.5556 | 24.5556 |
| U7 | C20625731_CRYSTAL-SMD_4P-L3_2-W2_5-BL | 1 | Crystal | C20625731 | 0.3809 | 0.3809 |
| USB1 | USB-C-SMD_TYPE-C-16PIN-2MD-073 | 1 | TYPE-C 16PIN 2MD | C2765186 | 0.0738 | 0.0738 |
| | | | | **Total** | | **41.76** |

### Prices on JLCPCB:
NOTE: THESE PRICES DO NOT CONTAIN TAXES, AND ARE PRONE TO CHANGES

PCB (5x): $2.0 (if done without PCBA)

PCB (5x): $32.00

PCBA (2x): $194.03

Shipping on Global Standard Direct Line: $12.62
