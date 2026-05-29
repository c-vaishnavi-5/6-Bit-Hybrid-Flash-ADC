# 6-Bit Hybrid Flash ADC — VLSI Design

VLSI implementation of a two-step hybrid Flash Analog-to-Digital Converter for high-frequency applications, designed using Cadence Virtuoso (180nm CMOS) and verified with MATLAB Simulink.

---

## Project Overview

This project presents the design and simulation of a **6-bit Two-Step Flash ADC** (also known as a Half Flash ADC). The architecture splits conversion into two 3-bit stages — a coarse ADC and a fine ADC — reducing hardware complexity while maintaining high conversion speed suitable for high-frequency applications.

Designed and submitted as part of the B.Tech program at the **School of Electronics Engineering, Vellore Institute of Technology, Chennai** (November 2024).

---


---

## Key Specifications

| Parameter | Value |
|---|---|
| Resolution | 6-bit |
| Sampling Frequency | ~2 MHz |
| Technology Node | 180nm CMOS |
| Supply Voltage | 1.8 V |
| INL / DNL | < 1 LSB |
| Power Dissipation | < 40 mW |

---

## Architecture

The 6-bit ADC uses a **Two-Step Flash** approach with the following sub-blocks:

- **Sample and Hold (S/H)** — Captures and freezes the analog input for stable conversion
- **Coarse ADC (3-bit Flash)** — Produces the Most Significant Bits (MSBs) via parallel comparison
- **DAC (R-2R Ladder)** — Reconstructs the coarse analog equivalent from MSBs
- **Subtractor** — Computes the residue (difference between original input and DAC output)
- **Fine ADC (3-bit Flash)** — Converts the residue to produce the Least Significant Bits (LSBs)
- **Comparator** — Core decision element comparing input against reference voltages
- **2:1 MUX** — Routes signals between stages

---

## Tools Used

- **Cadence Virtuoso** — Schematic design and circuit simulation (180nm PDK)
- **MATLAB Simulink** — Behavioral-level modeling and verification

---

## Results Summary

All sub-blocks were individually simulated and verified before integration into the full 6-bit ADC:

- **Sample and Hold** — Output correctly freezes the sampled analog voltage during the hold phase
- **Comparator** — Produces clean digital switching based on input vs. reference voltage
- **2:1 MUX** — Correctly routes inputs based on the select line
- **3-bit Flash ADC** — Transitions through 8 binary codes as input voltage sweeps 0–4V
- **DAC** — Outputs a staircase analog waveform corresponding to digital input codes
- **6-bit Flash ADC** — Transitions through 64 discrete binary levels across the full input range

---

## Conclusion

The 6-bit two-step flash ADC successfully demonstrated high-speed analog-to-digital conversion with low latency using a parallel comparator structure. The design is well-suited for applications prioritising conversion speed, such as digital oscilloscopes, communication systems, and video processing.

Future work may explore power optimisation techniques like interpolation or time-interleaved architectures to reduce comparator count while preserving speed.

---

## References

1. S. P. Senapati, "Design of a simple digital ADC using only digital blocks and delay element circuit," IEEE RTEICT, 2016.
2. Z. Tan et al., "Incremental Delta Sigma ADCs: A Tutorial Review," IEEE Trans. Circuits Syst. I, vol. 67, no. 12, 2020.
3. R. H. Walden, "Analog-to-digital converter survey and analysis," IEEE J. Sel. Areas Commun., vol. 17, no. 4, 1999.
4. G. Palmisano et al., "Design procedure for two-stage CMOS transconductance operational amplifiers," Analog Integrated Circuits and Signal Processing, vol. 27, 2001.
5. J. Mahattanakul and J. Chutichatuporn, "Design procedure for two stage CMOS opamp," IEEE Trans. Circuits Syst. I, vol. 52, no. 8, 2005.
