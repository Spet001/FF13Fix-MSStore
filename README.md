# FF13Fix-MSStore — Modern GDK/UWP Frame Pacing, DXVK & Display Compatibility Layer

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Nexus Mods](https://img.shields.io/badge/Nexus_Mods-FF13_Mod_59-orange.svg)](https://www.nexusmods.com/finalfantasy13/mods/59)
[![Platform: Windows GDK](https://img.shields.io/badge/Platform-Microsoft_Store_|_Xbox_PC-0078D6.svg)]()
[![Target: Final Fantasy XIII](https://img.shields.io/badge/Target-Final_Fantasy_XIII_(GDK)-blueviolet.svg)]()
[![Status: Maintained on Nexus Mods](https://img.shields.io/badge/Status-Maintained_on_Nexus_Mods-success.svg)](https://www.nexusmods.com/finalfantasy13/mods/59)

> **Repository Archival Notice & Official Distribution Channels:**  
> The original source code repository was archived during an infrastructure migration. The official compiled release binaries, automated installers, and community support continue actively on **[Nexus Mods (Mod #59)](https://www.nexusmods.com/finalfantasy13/mods/59)**.  
> 
> For low-level systems engineering articles, GDK runtime analyses, and client-side web tools, visit **[Eduardo Gelain's Portfolio](https://spet01.dev/)**.

> [!NOTE]
> **Author's Note:**  
> This tool was created early in my development journey while I was first exploring modding and reverse engineering. The UI may be straightforward, setup can require patience, and minor edge bugs may arise—but it works, does exactly what it was designed to do, and remains a unique, tailored fix for Final Fantasy XIII players on the Xbox Game Pass / Microsoft Store ecosystem.

---

## Overview

**FF13Fix-MSStore** is an enhanced, all-in-one optimization suite and compatibility layer tailored specifically for the Microsoft Store and Xbox Game Pass PC editions of *Final Fantasy XIII*.

Unlike standard Steam community patches, this solution pairs the proven binary enhancements of **FF13Fix** with an integrated **DXVK Vulkan translation layer**, administered and coordinated through **Special K**. This combination resolves the notorious engine stutter, frame drops, and presentation bottlenecks inherent to the PC port when executed inside the Microsoft Gaming Development Kit (GDK / AppX) environment.

---

## Key Technical Features & Differences

### 1. Dual Integration: FF13Fix + DXVK (Managed by Special K)
* **The Architecture:** In addition to core FF13Fix binary patches, this package bundles a customized DXVK Direct3D 9 to Vulkan translation pipeline, managed via Special K's runtime hook framework.
* **The Impact:** Offloads Direct3D 9 command execution to native Vulkan hardware queues, stabilizing GPU utilization, eliminating draw-call micro-stutter, and delivering perfectly smooth frame pacing on modern graphics cards.

### 2. Controller Polling Decoupling & 1-Second Stutter Elimination
* **The Problem:** The vanilla engine performs blocking, synchronous input state queries on the main rendering loop once every second, triggering periodic 15–30 FPS drops regardless of hardware strength.
* **The Mitigation:** Decouples input polling from the primary render thread into asynchronous background routines, eliminating periodic frame drops completely.

### 3. GDK / UWP Packaging & Path Interoperability
* Tailored to hook cleanly into the Microsoft Gaming Services runtime environment without tripping container initialization faults or loader deadlocks.
* Resolves DLL injection hurdles unique to the Windows Store encrypted filesystem sandbox.

### 4. High-Definition Shadow Depth Matrix Allocation
* Overrides hardcoded low-resolution 512x512 and 1024x1024 shadow map allocations, expanding the shadow buffer to native 2048x2048 or 4096x4096 with hardware bilinear filtering.

### 5. 2D UI & Presentation Aspect Ratio Correction
* Corrects letterboxing and user interface scaling anomalies on 16:10, 21:9 ultrawide, and high-DPI displays.

---

## Official Releases & Download Links

Compiled release binaries, configuration `.ini` presets, and setup instructions are maintained on Nexus Mods:

* **Official Mod Page (FFXIII Mod #59):** [https://www.nexusmods.com/finalfantasy13/mods/59](https://www.nexusmods.com/finalfantasy13/mods/59)
* **Nexus Mods Profile:** [https://www.nexusmods.com/profile/Spet001/mods](https://www.nexusmods.com/profile/Spet001/mods)

---

## Developer Ecosystem & Web Tools Suite

Visit Eduardo Gelain's interactive web workbench featuring client-side binary analysis and asset inspection tools running 100% locally in your browser:

* **[Spet's Easy Online Decompiler](https://spet01.dev/tools/easy-decompiler/)**: WebAssembly-powered binary analyzer, disassembler, and dual C-like decompiler (Rizin + Ghidra Sleigh) for PE, ELF, and Mach-O files. Zero server uploads.
* **[Spet's Universal Game File Opener](https://spet01.dev/tools/universal-file/)**: Universal client-side game archive inspector and container extractor supporting 25+ game engine formats (WAD, PAK, PK3, FastFiles, BSA/BA2, RPF, RPA).
* **[Spet's Quick 3D Studio](https://spet01.dev/tools/image-to-3d/)**: Procedural 2D-to-3D mesh extrusion engine for converting 2D designs into 3D models with PBR materials.
* **[Technical Research Journal](https://spet01.dev/journal/)**: Deep-dives into systems engineering, memory patches, and legacy game optimization.
* **[Main Portfolio](https://spet01.dev/)**: Central developer portfolio and project showcase.
