# CMOS Circuit Design – SPICE Simulation

This repository contains my work from the **cloud workshop on CMOS Circuit Design with SPICE Simulation (10 days, SKY130 node)**.

It includes my **daily lab reports, simulation results, and analysis**, documenting a step-by-step journey from transistor-level fundamentals to advanced CMOS reliability assessment.

---

## Workshop Overview

- **Duration:** 10 days
- **Technology Node:** SKY130 (open source)
- **Mode:** Cloud-based hands-on experiments
- **Organizer:** VSD (VLSI System Design)

### Key Topics
- Fundamentals of CMOS device physics and SPICE modeling
- Behavior of NMOS and CMOS inverters in operating ranges
- Determining switching thresholds and voltage transfer characteristics
- Analysis and optimization methods for noise margin
- Resilience to supply voltage variations and process technology variations
- Study of speed saturation, dynamic power, and propagation delay
- Full SPICE platform setup and parameter analysis
- Connecting SPICE-level data to OpenLane and VSDFlow design schematics

---

## Purpose and Significance

- **Importance for Semiconductors:** The SKY130 PDK has become a cornerstone of open-source IC design in academia and startups.
- **Hands-on Learning:** Each lesson combined theory with simulation-based verification using real transistor models.
- **Practical Usage:** The provided SPICE files and results can be integrated into broader RTL-GDS design workflows.

This repository serves as a **detailed description of my learning process**, combining theoretical knowledge with practical simulation results to demonstrate the behavior of CMOS circuits at the transistor level.

## Repo Structure  

```plaintext
├── Day 1/ # MOSFET Basics, Introduction to SPICE, Id-Vds Plots
├── Day 2/ # Long and Short Channel, Speed ​​Saturation, CMOS Basics
├── Day 3/ # CMOS Inverter Switching Threshold and Delay Analysis
├── Day 4/ # Noise Margin Theory and SPICE Lab Results
├── Day 5/ # Power Scaling, Etch Variations, Reliability Tests
├── ...
└── README.md # Main Project Overview (this file)
In each folder:

1,2,...png/ → Lab screenshots, VTC curves, transient response plots, etc.

SPICE Decks (if enabled)

🧪 Labs and Hands-on Activities
SPICE simulation with parameter tuning using SKY130 models

Switching threshold extraction (Vm)

Noise margin calculation (NMH, NML)

Delay (rise/fall) analysis considering transistor size

The impact of supply voltage scaling on inverter speed and gain

Reliability analysis with process technology changes and impact on manufacturing

🎯 Results
✅ Mastered transistor-level CMOS circuit design using SPICE
✅ Developed a reproducible simulation workflow for SKY130 assemblies
✅ Learned to link device physics → circuit behavior → design reliability
✅ Generated daily structured reports (available in this repository)
✅ Received an industry-recognized certificate of completion

🏁 Conclusion
This repository serves as both my personal journal and a knowledge base for anyone learning CMOS circuit design with SPICE. Freely browse daily reports, check SPICE results, and adapt workflows for your own research or prototyping.

✨ From device physics to reliable digital design – powered by SPICE and SKY130! ✨
