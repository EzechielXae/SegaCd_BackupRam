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
  - **Clean controls**: CE#/OE#/WE# driven through a **74LVC07A non-inverting open-drain buffer**, with pull-ups to VccRam. Its partial-power-down / Ioff behavior prevents back-powering the console logic when the console is off.
- Designed in **EasyEDA** (schematic JSON in repo).

---

## Revision 1.0

Rev 1.0 was the first hardware revision using the AS6C4008 low-power SRAM with battery backup.
CE#/OE#/WE# were isolated from the console logic using a 74HCT04 + NPN open-collector interface to prevent backfeed when the console was powered off.

---

## Revision 1.2

In Rev1.0 : The memory architecture and address decoding were functional, but this control stage introduced excessive delay on the SRAM control signals, causing the Mega-CD to reset when accessing cartridge memory.

Rev 1.2 replaces the previous 74HCT04 + NPN open-collector
CE#/OE#/WE# interface with a 74LVC07A non-inverting open-drain buffer.

Direct CE#/OE#/WE# wiring was validated on real hardware for detection,
formatting, read and write operations.
The 74LVC07A restores battery-domain isolation while preserving fast bus timing.

---

## Battery Life (rule-of-thumb)

| Standby current | **CR2032 (220 mAh)** | **CR2450 (600 mAh)** |
|---|---:|---:|
| 2 µA | ~12.6 years theoretical | ~34 years theoretical |
| 4 µA | ~6.3 years theoretical | ~17 years theoretical |


In practice, coin-cell self-discharge and leakage currents will reduce these figures.
A realistic target is roughly **5 years with a CR2032**.

---

## Build & Files

Minimum track widths, clearances and via sizes are within the standard offering of modern PCB fabricators. Development was done using EasyEDA/JLCPCB and as such the Gerber files are provided to their specification.

The design is verified to work as a 2-layer PCB.
I recommend getting ENIG and Gold, but HASL will work also

---

## Bill of Materials

- **[PDF BOM](./Bom/BOM_SEGA-BackUp-Ram_rev1.2.pdf)**

- **[Interractive BOM](./Bom/PCB_SEGA-BackUp-Ram_rev1.2.html)**


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

