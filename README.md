# MOSFET as a Switch: KiCad SPICE Simulation

## 📌 Overview
This repository contains a fully functional KiCad schematic and SPICE simulation demonstrating how an N-Channel MOSFET operates as an electronic switch. It visualizes the transition between the cut-off (OFF) and saturation (ON) regions using an integrated transient analysis.

This project is ideal for students and hobbyists looking to understand basic solid-state switching, load control, and how to configure internal SPICE models within the KiCad EDA environment.

## ⚙️ Circuit Architecture
* **Active Component:** N-Channel MOSFET
* **Load:** Standard resistive load connected to the Drain.
* **Control Signal:** A high-frequency Pulse Voltage Source applied to the Gate.
* **Power Supply:** DC Voltage Source across the Drain-Source path.

## 📊 Simulation Details
The project utilizes KiCad's integrated `ngspice` engine. The simulation is configured for a **Transient Analysis** to plot the time-domain waveforms. 

**Key Observations:**
* **Gate Voltage ($V_{GS}$):** The input digital control pulse.
* **Drain Voltage ($V_{DS}$):** Drops to near 0V when the MOSFET conducts (switch closed), and rises to the supply voltage when the MOSFET blocks current (switch open).
* **Drain Current ($I_D$):** Demonstrates the flow of current through the load when the threshold voltage ($V_{TH}$) is exceeded.

## 🛠️ Software Requirements
* **KiCad EDA** (v6.0 or higher recommended)
* Integrated `ngspice` simulator (included by default in KiCad)

## 🚀 How to Run the Simulation
1. Clone this repository to your local machine:
   ```bash
   git clone [https://github.com/satvikpandurangi/MOSFET-As-Switch-Kicad-Simulation.git](https://github.com/satvikpandurangi/MOSFET-As-Switch-Kicad-Simulation.git)
Open the .kicad_pro project file in the KiCad Project Manager.

Open the Schematic Editor to view the circuit layout.

Go to Inspect > Simulator in the top menu.

Click the Run/Stop Simulation (Play) button.

Probe the Gate and Drain nets on the schematic to view the resulting logic waveforms in the simulator window.

📂 Repository Contents
.kicad_pro - Main project file

.kicad_sch - The schematic wiring and SPICE directives

.kicad_pcb - Blank PCB layout file (ready for physical routing if desired)

Created for educational purposes and open-source hardware exploration.
