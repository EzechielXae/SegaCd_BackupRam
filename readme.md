# MegaCD / SegaCD Backup RAM (4 Mbit)

A drop-in Backup RAM cartridge for the SegaCD/Mega-CD using a **low-power 4 Mbit SRAM (AS6C4008)** and a **battery-backed rail** designed to preserve saves for years on a CR2032 or CR2450.  
Focus: **ultra-low standby current**, **no backfeed**, **clean bus interface**, and **simple assembly**.

> **Hardware License:** CERN-OHL-S-2.0  
> **SPDX**: `SPDX-License-Identifier: CERN-OHL-S-2.0`  
> **Source Location:** https://github.com/EzechielXae/SegaCd_BackupRam

---

## Highlights

- **True battery retention**: AS6C4008 (512K×8) with ~**2–4 µA** typical data-retention current.  
- **Years of autonomy** (limited by coin cell self-discharge): see table below.
- **Battery OR-ing** with **P-MOSFET “ideal diode”** (AO3407 ×2) — zero recharge of the coin cell, zero backfeed to console.
- **Two power rails**:
  - `+5V`: console/logic only.
  - `3V Battery`: battery-backed rail for **SRAM only**.
- **Clean controls**: CE#/OE#/WE# driven **open-drain (NPN)** via **74HCT04** (inversion) → **no leakage** when console is off.
- Designed in **EasyEDA** (schematic JSON in repo).

---

## Battery Life (rule-of-thumb)

|      | **CR2032 (220 mAh)**                                             | **CR2450 (600 mAh)**                       |
|------|------------------------------------------------------------|-------------------------------------|
| 2 µA | ~**12.6 years** (realistic: **~5–10 years** due to self-discharge) | ~**34 years** (realistic: **~10–15 years**) |

---

## Build & Files

- **EasyEDA** schematic JSON: includes description with SPDX line:
SPDX-License-Identifier: CERN-OHL-S-2.0
Source Location: https://github.com/EzechielXae/SegaCd_BackupRam

- **Gerbers**: generate from PCB project (once routed).
- **BOM** (key parts):
- AS6C4008-55 (512K×8 SRAM)
- AO3407 (P-MOSFET, SOT-23) ×2
- MMBT2222A or MMBT3904 (NPN, SOT-23) ×3 (CE#/OE#/WE#)
- 74HCT04, 74HCT138, 74HCT30, 74HCT32, 74HCT245 (ONLY Package SOIC 14, 16 and 20)
- Coin-cell holder **CR2032** or **CR2450**
- Caps: 100 nF per IC, **10 µF MLCC** near SRAM, **47–68 µF** bulk on +5V_SYS
- Resistors: **10 kΩ** (NPN base), **100 kΩ** (base-to-GND), **470 kΩ** (pull-ups to VCC_SRAM)

---

## Licensing

This hardware project is licensed under **CERN Open Hardware Licence Version 2 – Strongly Reciprocal (CERN-OHL-S-2.0)**.

- **SPDX**: `SPDX-License-Identifier: CERN-OHL-S-2.0`  
- **Complete Design Materials** (schematics, PCB sources, BOM, fabrication files) are provided in this repository.  
- **Source Location:** https://github.com/EzechielXae/SegaCd_BackupRam

If you add firmware/scripts, you may license them under **MIT** or **GPL-3.0-or-later**. Documentation/images can use **CC-BY-4.0**.

**Disclaimer:** No affiliation with SEGA. SEGA and Mega Drive/Genesis/SegaCD/Mega-CD are trademarks of their respective owners.

---

## Contributing

Issues and PRs welcome. Please keep modifications under **CERN-OHL-S-2.0** and update the **Source Location** if you redistribute derivatives.

