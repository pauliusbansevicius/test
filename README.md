# ZVS Induction Heater Manual

This repository contains the documentation and technical specifications for a **Zero Voltage Switching (ZVS)** induction heater.

---

## [cite_start]Bill of Materials (B.O.M) [cite: 2]

| Component | Specification | Description |
| :--- | :--- | :--- |
| **V1** | 12V DC | [cite_start]Power supply (PC PSU or car battery)[cite: 11, 22]. |
| **M1, M2** | IRFP250N | [cite_start]NMOSFETs for switching the resonant circuit[cite: 8, 33]. |
| **L1** | 2-3µH | [cite_start]Air wound coil: 10AWG wire, 5cm diameter, 8-10 turns[cite: 7]. |
| **L2, L3** | 100µH | [cite_start]20A toroidal inductors (choke) to protect the PSU[cite: 3, 20]. |
| **C1 - C6** | 1µF (6µF total) | [cite_start]MKP10 polypropylene capacitors for high frequencies[cite: 6, 25, 26]. |
| **D1, D2** | 12V Zener | [cite_start]Limits NMOSFET gate voltage to 12V[cite: 10, 30]. |
| **D3, D4** | MUR460 / UF4007 | [cite_start]UltraFast diodes with ~75ns recovery time[cite: 4, 28, 29]. |
| **R1, R2** | 10kΩ 1W | [cite_start]Pull-down resistors to clear gate charge[cite: 9, 32]. |
| **R3, R4** | 470Ω 1W | [cite_start]Resistors to limit current to the NMOSFET gates[cite: 5, 31]. |

---

## Circuit Schematic & Analysis

![ZVS Driver Schematic](ZVS_driver_schematic.png)
[cite_start]*Figure 1: ZVS driver and induction heater schematic with FFT analysis[cite: 1].*

### [cite_start]Performance Parameters [cite: 14]
* [cite_start]**Efficiency:** Approximately 90%[cite: 18].
* [cite_start]**Idle Current:** 1-1.5A[cite: 16].
* [cite_start]**Heating Current:** Up to 20A[cite: 16].
* [cite_start]**Output:** AC voltage through the L1 coil heats the metal[cite: 13].

![Output Waveform](Output_signals.png)
[cite_start]*Figure 2: AC voltage waveform running through the L1 coil[cite: 12].*

---

## How it Works

The ZVS induction heater is a **self-oscillating parallel resonant inverter**.

* [cite_start]**Resonance:** Capacitors C1-C6 and inductor L1 form a parallel resonant circuit[cite: 23]. [cite_start]This stores energy and boosts current up to 40A[cite: 24].
* [cite_start]**Zero Voltage Switching (ZVS):** MOSFETs (M1, M2) switch sides of the resonant circuit to ground and the power supply to keep oscillations going[cite: 33]. [cite_start]This replaces energy lost to resistance in the components[cite: 34].
* [cite_start]**Feedback:** UltraFast diodes (D3, D4) trigger the MOSFET on the opposite side when the cathode voltage jumps, ensuring synchronization[cite: 28].
* [cite_start]**Protection:** Choke inductors (L2, L3) lower startup current and isolate the 12V supply from ~36V peaks to prevent damaging the power source[cite: 20].
* [cite_start]**Induction:** The high-frequency AC voltage in coil L1 creates a magnetic field that induces heat in metal objects placed inside[cite: 13].
