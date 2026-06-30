# Pop & Push | 8-Bit Arcade Game written in SM83 Assembly

<p align="center">



  
  <img src="https://img.shields.io/badge/Language-SM83%20%2F%20Z80%20Assembly-red.svg?style=for-the-badge" alt="SM83 Assembly">
  <img src="https://img.shields.io/badge/Platform-Nintendo%20Game%20Boy-green.svg?style=for-the-badge&logo=nintendo" alt="Game Boy">
  <img src="https://img.shields.io/badge/Tools-RGBDS-blue.svg?style=for-the-badge" alt="RGBDS">
</p>

## 🕹️ Overview
Pop & Push is an authentic 8-bit arcade game engineered completely in **SM83 Assembly from scratch** for the original 1989 Nintendo Game Boy hardware. Developed within strict retro constraints (4MHz CPU, 8KB VRAM), the project showcases custom low-level physics, tile-based collision pipelines, and persistent cartridge save-state management without any high-level engine support.

---

## 📸 Gameplay & Media
  <img width="45%" alt="image" src="https://github.com/user-attachments/assets/04990abb-a3e2-49ea-81c0-772950ede5a6" alt="Gameplay 0" />
  <img width="45%" alt="image" src="https://github.com/user-attachments/assets/b5ebedbc-93e7-4acb-ad98-c8b31f40c784" alt="Main Menu"/>

---

## 🛠️ Technical Achievements & Low-Level Architecture

### 💾 Persistent Save-State Engineering (SRAM)
Implementing a save system on bare metal requires direct memory banking manipulation:
*   **MBC1 Controller Interface:** Programmed manual switching of Cartridge RAM banks via specialized hardware registers to enable external SRAM access.
*   **Data Integrity:** Designed a custom serialization layout to write high scores, player progress, and game states directly into volatile RAM chips, locking the banks safely afterward to prevent memory corruption.

### 🍎 Custom Physics & Gravity on Bare Metal
Implementing realistic physics without floating-point units (FPU) or high-level multiplication required custom mathematical hacks:
*   **Fixed-Point Arithmetic:** Engineered sub-pixel precision systems using fractional math (splitting 16-bit registers into integer and fractional parts) to simulate smooth gravity vectors and acceleration.
*   **Advanced Tile Collisions:** Developed a pixel-perfect collision routine that samples the background tilemap coordinates in real-time, handling vertical velocity grounding and horizontal wall bounces smoothly within the v-blank interval.

### 🎨 VRAM Optimization & Tile Mirroring
With only 8KB of video memory, every single byte mattered:
*   **Hardware Mirroring:** Optimized the asset pipeline by utilizing the Game Boy's hardware-level sprite mirroring attributes (`OAM` flags for X/Y flip). This cut sprite memory usage in half, allowing for complex character animations within strict hardware budgets.
*   **Dynamic V-Blank DMA Transfers:** Wrote optimized routines during the ultra-short Vertical Blanking period to push sprite data into Object Attribute Memory (OAM) via DMA transfers without causing visual tearing.

---

## ⚡ The Engineering Challenge: Cycle Counting Optimization
**The Problem:** The Game Boy's SM83 processor runs at a massive... 4.19 MHz. Running real-time fixed-point gravity calculations, checking matrix-based tile collisions for multiple active entities, and updating the UI could easily overflow the 60 FPS frame budget, causing massive frame drops.

**The Solution:** 
*   Replaced costly loops with unrolled assembly instructions where memory permitted.
*   Optimized collision checks by implementing early-out branching (bounding box pre-filtering) before running fine tile lookups.
*   Utilized 8-bit registers (`H`, `L`, `D`, `E`) efficiently to keep calculations entirely within the CPU cache, minimizing heavy RAM read/write cycles (`ld [hl], a` optimizations).
*   **Result:** A locked, butter-smooth 60Hz gameplay experience running perfectly on real legacy hardware.

---

## 📂 Project Structure
*   **Language:** SM83 / Z80 Assembly
*   **Assembler/Linker:** RGBDS (Rednex Game Boy Development System)
*   **Target Hardware:** Game Boy DMG-01 (or modern accurate emulators like BGB/SameBoy)

## 🕹️ Play the Game
**The latest stable build is available on itch.io:** 👉 [**Play Pop&Push on itch.io**](https://javierrhp.itch.io/pop-push)
---
