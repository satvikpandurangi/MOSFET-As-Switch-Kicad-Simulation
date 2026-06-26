# MOSFET as a Switch: KiCad SPICE Simulation

## Overview

This repository contains a KiCad schematic and SPICE simulation demonstrating how an N-Channel Enhancement MOSFET operates as a voltage-controlled electronic switch. Using transient analysis in KiCad's integrated `ngspice` engine, the project verifies the device's behavior across its cut-off and saturation regions while driving a resistive load.

## Features

- Complete KiCad schematic of a MOSFET switching circuit
- Transient SPICE simulation (`.tran`) over a 20 ms window
- Clear visualization of the inverse relationship between gate control signal and drain output
- Tabulated input/output logic states for quick reference

## Circuit Description

The circuit uses a Pulse Voltage Source on the Gate to switch the MOSFET between cut-off (OFF) and saturation (ON):

- **Cut-off (Switch OFF):** When V_GS < V_th, the Drain–Source channel is open and no current flows through the load.
- **Saturation (Switch ON):** When V_GS > V_th (logic HIGH), the channel becomes conductive, pulling current from the 12 V supply through the load to ground.

## Components

| Type | Component | Value / Rating |
|------|-----------|-----------------|
| Active | N-Channel Enhancement MOSFET (VDMOS) | — |
| Passive | Resistor (Load) | 1 kΩ |
| Source | DC Voltage Source (Main Power) | 12 V |
| Source | Pulse Voltage Source (Gate Control) | 0–5 V, 10 ms period |
| Misc | Ground terminals | — |

## Simulation Setup

1. The 12 V DC source powers the Drain through the 1 kΩ load resistor.
2. The MOSFET's Source is tied to Ground.
3. A 0–5 V square-wave Pulse Source (10 ms period) drives the Gate.
4. Transient analysis is run as `.tran 0.1m 20m` over a 20 ms window.
5. Gate voltage (input) and Drain voltage (output) nets are probed to observe switching behavior.

## Results

| Gate Voltage (V_GS) | Input Logic | MOSFET State | Drain Voltage (V_Drain) | Load Status |
|----------------------|-------------|----------------|--------------------------|------------------------|
| 0.0 V | LOW (0) | OFF (Cut-off) | ~12.0 V | Unpowered (no current) |
| 5.0 V | HIGH (1) | ON (Conducting) | ~0.0 V | Powered (current flowing) |

The transient simulation confirms the MOSFET acts as a reliable voltage-controlled switch: a HIGH gate signal pulls the Drain voltage to near 0 V (switch closed), while a LOW gate signal leaves the Drain at the full 12 V supply (switch open).

## Repository Structure

```
.
├── MOSFET_As_Switch.kicad_pro   # Main KiCad project file
├── MOSFET_As_Switch.kicad_sch   # Schematic and SPICE directives
├── MOSFET_As_Switch.kicad_pcb   # PCB layout file
├── MOSFET_Schematic.png         # Circuit schematic
├── MOSFET_Output.png            # Simulation waveform output
└── README.md
```

## How to Run

1. Clone this repository:
   ```bash
   git clone https://github.com/satvikpandurangi/MOSFET-As-Switch-Kicad-Simulation.git
   ```
2. Open `MOSFET_As_Switch.kicad_pro` in the KiCad Project Manager.
3. Open the Schematic Editor to view the circuit layout.
4. Go to **Inspect > Simulator** in the menu bar.
5. Click **Run/Stop Simulation** to execute the transient analysis.
6. Probe the Gate and Drain nets to view the resulting switching waveforms.

## Screenshots

**Schematic:**

![Schematic](images/MOSFET_Schematic.png)

**Simulation Output:**

![Simulation Output](images/MOSFET_Output.png)

