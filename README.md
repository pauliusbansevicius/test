# ZVS Induction Heater Manual

[cite_start]This repository contains the documentation and technical specifications for a **Zero Voltage Switching (ZVS)** induction heater[cite: 1].

---

## [cite_start]Bill of Materials (B.O.M) [cite: 2]

| Component | Specification | Description |
| :--- | :--- | :--- |
| **V1** | [cite_start]12V DC [cite: 11, 15] | [cite_start]Power supply (PC PSU or car battery)[cite: 22]. |
| **M1, M2** | [cite_start]IRFP250N [cite: 8] | [cite_start]NMOSFETs for circuit switching[cite: 33]. |
| **L1** | [cite_start]2-3µH [cite: 7] | [cite_start]Air wound coil: 10AWG wire, 5cm diameter, 8-10 turns[cite: 7]. |
| **L2, L3** | [cite_start]100µH [cite: 3] | [cite_start]20A toroidal inductors (choke) to protect the PSU[cite: 3, 20]. |
| **C1 - C6** | [cite_start]1µF [cite: 6] | [cite_start]MKP10 polypropylene capacitors for high frequencies[cite: 26]. |
| **D1, D2** | [cite_start]12V Zener [cite: 10] | [cite_start]Limits NMOSFET gate voltage to 12V[cite: 30]. |
| **D3, D4** | [cite_start]MUR460 [cite: 4] | [cite_start]UltraFast diodes with ~75ns recovery time[cite: 28, 29]. |
| **R1, R2** | [cite_start]10kΩ 1W [cite: 9] | [cite_start]Pull-down resistors to clear gate charge[cite: 32]. |
| **R3, R4** | [cite_start]470Ω 1W [cite: 5] | [cite_start]Resistors to limit current to the NMOSFET gates[cite: 31]. |

---

## Circuit Schematic & Analysis

![ZVS Driver Schematic](path/to/your/schematic_image.png)
[cite_start]*Figure 1: ZVS driver and induction heater schematic with FFT analysis[cite: 1].*

### [cite_start]Performance Parameters [cite: 14]
* [cite_start]**Efficiency:** Approximately 90%[cite: 18].
* [cite_start]**Idle Current:** 1-1.5A[cite: 16].
* [cite_start]**Heating Current:** Up to 20A[cite: 16].
* [cite_start]**Output:** AC voltage through the L1 coil heats the metal[cite: 13].

![Output Waveform](path/to/your/output_waveform_image.png)
[cite_start]*Figure 2: AC voltage waveform running through the L1 coil[cite: 12].*

---

## How it Works

The ZVS induction heater is a **self-oscillating parallel resonant inverter**.

* [cite_start]**Resonance:** Capacitors C1-C6 (6µF bank) and inductor L1 form a parallel resonant circuit[cite: 23, 25]. [cite_start]This stores energy and boosts current up to 40A[cite: 24].
* [cite_start]**Zero Voltage Switching (ZVS):** The MOSFETs (M1, M2) switch sides of the resonant circuit to ground[cite: 33]. [cite_start]By switching when voltage is near zero, the circuit maintains oscillations and minimizes energy loss[cite: 33, 34].
* [cite_start]**Feedback:** UltraFast diodes (D3, D4) trigger the MOSFET on the opposite side when voltage jumps, keeping the timing in sync[cite: 28].
* [cite_start]**Protection:** Choke inductors (L2, L3) lower startup current and isolate the 12V supply from 36V peaks to prevent frying the power source[cite: 20].
* [cite_start]**Heating:** The high-frequency AC current in coil L1 creates a magnetic field that induces heat in metal objects placed inside[cite: 13].
