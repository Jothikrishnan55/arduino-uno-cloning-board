Arduino Uno Compatible Custom PCB

A minimal, custom-designed Arduino Uno-compatible microcontroller board built from scratch in KiCad, based on the ATmega328P microcontroller.

Overview

This project is a bare-bones recreation of the core Arduino Uno circuit — the same microcontroller, clock, and power system used in the official board, designed as a standalone PCB from the schematic level up. Unlike the original Arduino Uno, this board does not include an onboard USB-to-serial chip; programming is done externally through an ICSP header using a USBasp (or similar) programmer.

Components Used

Component	Value / Part	Function

U1	ATmega328P	Main microcontroller (runs the program)
Y1	16MHz Crystal	Provides clock timing for the microcontroller
C1, C2	22pF Ceramic Capacitors	Crystal load capacitors
C3, C4	100nF Ceramic Capacitors	Decoupling capacitors (VCC / AVCC noise filtering)
R1	10kΩ Resistor	Reset pull-up
SW1	Push Button	Manual reset switch
D1	LED	Power indicator
R2	220Ω Resistor	LED current-limiting resistor
U2	7805 Voltage Regulator	Converts 9–12V input to a stable 5V supply
C5	10µF Electrolytic Capacitor	Regulator input filter capacitor
C6	100nF Ceramic Capacitor	Regulator output filter capacitor
J1	Barrel Jack	9–12V DC power input
J2	2x3 Pin Header (ICSP)	Programming interface (MOSI, MISO, SCK, RESET, VCC, GND)

How It Works

Power supply: A 9–12V DC adapter connects through the barrel jack (J1) into a 7805 linear regulator (U2), which steps the voltage down to a stable 5V. Filter capacitors on both the input (C5) and output (C6) sides keep the supply clean.

Microcontroller: The regulated 5V powers the ATmega328P (U1) on its VCC and AVCC pins, each backed by a decoupling capacitor (C3, C4) to suppress noise.

Clock: A 16MHz crystal (Y1), paired with two 22pF load capacitors (C1, C2), gives the microcontroller its operating clock speed.

Reset circuit: A 10kΩ pull-up resistor (R1) holds the RESET pin high during normal operation; pressing the push button (SW1) pulls it low, resetting the chip.

Programming: Since there's no onboard USB interface, code is uploaded using an external ISP programmer connected to the 6-pin ICSP header (J2), which exposes the SPI programming pins (MOSI, MISO, SCK) along with RESET, VCC, and GND.

Status indicator: A power LED (D1) with a current-limiting resistor (R2) lights up whenever the board is powered.

Design Process

Schematic captured in KiCad, starting from individual component placement through to full net connections.

Verified using KiCad's Electrical Rules Checker (ERC) — 0 errors, 0 warnings.

PCB layout completed with component placement, routing, and a ground pour.

Verified using KiCad's Design Rules Checker (DRC) before generating manufacturing files.
Gerber files generated for fabrication.

Files Included

.kicad_sch — Schematic source file
.kicad_pcb — PCB layout file
.kicad_pro — KiCad project file
Gerber files — Ready for PCB manufacturing
Tools Used
KiCad — schematic capture, PCB layout, and Gerber generation
Status
Design complete and DRC/ERC clean. Not yet fabricated/tested on physical hardware.


