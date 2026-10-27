# DC-DC Voltage Multiplier (±2 V → 10 V)

University project: a positive DC-DC voltage multiplier that produces a 10 V
output from a ±2 V supply, designed for a minimum load of 200 kΩ.

## How it works
The circuit uses an on-board transistor oscillator and driver stage that feed a
diode-capacitor ladder, which multiplies the input voltage.
The left-hand part of the circuit is an astable multivibrator (T3, T4) that generates the clock. I increased its base resistors R1 and R6 to 330 kΩ, and reduced C8 and C9 to 100 pF to keep the frequency at about 25 kHz. With the original 47 kΩ resistors, both transistors were deeply saturated in the symmetric DC state, so the simulator stayed in that state and the oscillator never started. With 330 kΩ they operate in the active region, where the symmetric state is unstable and the oscillation starts. The right-hand part is a three-stage Cockcroft–Walton voltage multiplier (D1–D6, C1–C6). Each diode drops about 0.5 V, so the three stages alone give only about 8.7 V. The divider formed by R5 (1 kΩ) and R4 (6.8 kΩ), decoupled by C7 (1 µF), sets a reference of about +1.5 V for the diode chain, so the ladder does not start from 0 V. This offset brings the output to about 10 V.

## Tools
- Schematic and PCB: OrCAD
- Simulation: TINA

## Simulation
Full transient simulation:

![TINA simulation, full curve](tina-simulation-full.png)

Zoom on the first 20 ms:

![Transient 0-20 ms](transient-0-20ms.png)

The output reaches 10 V in simulation. [Add what you observe: settling time,
ripple, behavior under load.]

## Files
- `DC-DC amplifier/` – OrCAD project (schematic)
- `Amplificator DC-DC(...).TSC` – TINA simulation file

## Status
- [x] Schematic (OrCAD)
- [x] Simulation (TINA)
- [ ] PCB layout
- [ ] Assembly and measurements
