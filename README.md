# barebones

**barebones** is a work-in-progress open-source laptop motherboard project built around the Rockchip RK3588 platform. It is designed as a high-performance, modular laptop mainboard with dual DDR4 memory slots, hierarchical subsystem schematics, and a full laptop-oriented power, I/O, audio, and control architecture.

> **Project status:** Work in progress. Many generated deliverables such as BOMs, fabrication outputs, and related assembly files do not exist yet.

## 📌 Project Overview

barebones is intended to be a complete laptop motherboard platform rather than a small breakout or development board. The design is organized into multiple schematic sheets that separate major functional blocks such as power delivery, memory, high-speed I/O, embedded control, audio, and peripheral connectors. This makes the project easier to review, extend, and maintain while keeping the electrical design understandable even as complexity grows.

The project currently centers on a laptop-class architecture with:

* a Rockchip RK3588-based compute core,
* an embedded controller for platform management,
* dual DDR4 memory slots,
* a dedicated power and charging subsystem,
* and high-speed external interfaces for peripherals and display output.

Because the design is still under active development, the repository should be treated as an evolving engineering workspace rather than a finished production-ready hardware release.

## 📌 Features

* **Main Processor / Core:** Rockchip RK3588-class laptop platform
* **Embedded Controller:** STM32-based controller for power sequencing, input handling, and system management
* **Memory:** 16GB LPDDR4x RAM
* **Power System:** Laptop battery charging and system power distribution architecture
* **Interfaces:** High-speed USB, display, audio, and peripheral connectivity
* **Schematic Organization:** Hierarchical KiCad project with multiple subsystem sheets
* **Project Type:** Open-source laptop motherboard / mainboard
* **License:** AGPL 3.0
* **Development State:** Work in progress

## 🛠️ Hardware Specifications

The exact manufacturing stackup and sign-off values may still evolve as the board is refined. The following items are the core hardware targets currently associated with the project:

* **PCB Thickness:** To be finalized
* **Minimum Trace Width:** To be finalized
* **Minimum Clearance:** To be finalized
* **Copper Weight:** To be finalized
* **Layer Count:** To be finalized
* **Memory Topology:** LPDDR4x RAM
* **Board Category:** Laptop motherboard / high-complexity mixed-signal design

## 🧩 Major Subsystems

### Compute Subsystem

The compute section defines the main processing architecture of the laptop motherboard. It is intended to host the RK3588 platform and the supporting high-speed routing required for a modern laptop-class board.

### Memory Subsystem

The memory architecture uses **LPDDR4x RAM**, which is useful for high speeds, low-power environment. The memory-related schematic is separated into its own sheet to keep the signal groupings and placement intent easier to review.

### Power Subsystem

The power section handles battery input, system rails, and the sequencing necessary for a laptop motherboard. A complex platform like this typically requires careful regulation, protection, and startup order management.

### Embedded Controller and Internal Audio

This sheet groups the system-management logic and the internal audio path. Keeping embedded control and audio-related circuitry organized separately helps with debugging and future revisions.

### High-Speed I/O

The high-speed I/O section covers data interfaces and other external connectivity that must respect signal integrity constraints. This is where ESD protection, connector handling, and differential routing considerations are typically concentrated.

### Peripheral I/O Connectors

The peripheral connector sheet holds external ports and board-edge interfaces intended for system expansion and user connectivity.

## 📂 Repository Structure

The project currently uses the following folder and file structure:

* `/` : Main KiCad project directory containing the project files and schematic sheets.
* `/barebones.kicad_pro` : KiCad project manager file.
* `/barebones.kicad_pcb` : PCB layout file.
* `/barebones.kicad_prl` : KiCad project local configuration file.
* `/barebones.kicad_symdir/` : Symbol directory used by the project.
* `/barebones.pretty/` : Footprint library folder.
* `/barebones.3dshapes/` : Custom 3D shape models folder.
* `/barebones-backups/` : Backup copies created during design work.
* `/barebones.kicad_sch` : Top-level schematic sheet.
* `/barebones_chip.kicad_sch` : Main chip / compute subsystem schematic.
* `/barebones_power.kicad_sch` : Power delivery subsystem schematic.
* `/barebones_io.kicad_sch` : Input/output and high-speed connectivity schematic.
* `/barebones_mems.kicad_sch` : Memory subsystem schematic.
* `/barebones_mem.kicad_sch` : Additional memory-related schematic sheet.
* `/barebones_audio.kicad_sch` : Audio subsystem schematic.
* `/barebones_GPIO.kicad_sch` : GPIO / general-purpose expansion schematic.
* `/sym-lib-table` : Symbol library table.
* `/fp-lib-table` : Footprint library table.
* `~barebones.kicad_sch.lck` : KiCad lock file.
* `~barebones.kicad_pro.lck` : KiCad project lock file.

### Notes on repository contents

At the moment, many folders commonly found in completed hardware repositories are not present yet. In particular, BOM exports, fabrication outputs, assembly coordinate files, and other generated release artifacts may be missing until the design reaches a later stage.

## 🚀 How to Use / Build

1. Clone or download the repository locally.
2. Install a compatible version of [KiCad](https://www.kicad.org).
3. Open the `barebones.kicad_pro` project manager file.
4. Inspect the hierarchical schematics, starting from the top-level `barebones.kicad_sch` sheet.
5. Review the subsystem sheets individually to understand the design intent and implementation status.
6. Use KiCad ERC and DRC tools regularly during development.
7. When the design is ready, generate fabrication outputs such as Gerbers, drill files, and BOMs.

## 📋 Bill of Materials (BOM)

A complete bill of materials is **not available yet**. Since the project is still in progress, the BOM and related export files may not exist or may be incomplete.

Current repository state:

* BOM exports: not yet finalized
* Assembly files: not yet finalized
* Fabrication package: not yet finalized
* Interactive documentation: may be incomplete or absent

Once the design stabilizes, this section can be expanded with a complete component table, reference designators, values, footprints, manufacturers, and part numbers.

### Example BOM layout for future use

| Reference | Qty | Subsystem | Value / Part Name | Manufacturer       | Package |
| --------- | --- | --------- | ----------------- | ------------------ | ------- |
| U1        | 1   | Compute   | RK3588-class SoC  | Rockchip           | BGA     |
| U2        | 1   | Power     | PMIC / charger    | TBD                | TBD     |
| U3        | 1   | Control   | STM32 EC          | STMicroelectronics | TBD     |
| J1, J2    | 2   | Memory    | DDR4 slots        | TBD                | Slot    |

## 🧠 Design Intent

Barebones is structured to support a laptop-style product architecture with clear separation between high-speed digital routing, power delivery, and user-facing I/O. The use of a top-level schematic plus dedicated subsystem sheets suggests a design flow aimed at:

* simplifying debugging,
* reducing schematic clutter,
* allowing subsystem-level review,
* and making future iteration easier.

The dual DDR4 slots are a key architectural choice because they improve configurability and serviceability compared with soldered-only memory designs.

## 🔧 Development Notes

Because the project is still evolving, some files may be placeholders, partial drafts, or absent entirely. That is normal for an active hardware project. Future revisions may introduce:

* completed BOM exports,
* annotated fabrication outputs,
* versioned release folders,
* assembly drawings,
* mechanical documentation,
* and manufacturing notes.

## 📄 License

This hardware and associated project documentation are licensed under the **AGPL 3.0**.

## ⚠️ Disclaimer

This repository is provided as-is for development and educational purposes. It is a work in progress, and the design may contain incomplete sections, missing files, and unverified assumptions. Always review the schematics, footprints, net classes, ERC results, and DRC results in KiCad before attempting fabrication or assembly.

High-speed laptop motherboards are complex mixed-signal systems. Electrical, thermal, mechanical, and manufacturing validation should be performed before any production attempt.
