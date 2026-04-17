# Game Boy Retro Development - SM83 Assembly Project

A low-level arcade game developed for the original **Nintendo Game Boy**. This project showcases high-performance 8-bit programming, custom physics, and an entity management system written entirely in **SM83 Assembly**.

## 🛠️ Technical Stack
* **Language:** SM83 Assembly (Game Boy CPU).
* **Toolchain:** GBTelera / RGBDS.
* **Architecture:** Custom System-based architecture (Physics, Collision, Rendering, and Animation systems).
* **Audio:** GBT Player integration for background music and SFX.

## 🚀 Engineering Highlights
* **Entity Management:** Implementation of a robust entity manager (`man_entity.asm`) to handle life cycles, states, and properties of in-game objects.
* **Advanced Physics System:** Custom gravity and movement logic (`sys_physics.asm`) optimized for the Game Boy's limited CPU cycles.
* **Tile-Based Collisions:** Efficient collision detection (`sys_collision.asm`) between entities and the background map.
* **Modular Codebase:** Highly organized structure using include files and separate systems to manage rendering and animations.

## ✍️ My Contributions
In this collaborative project, I was responsible for:
* Developing the **Physics and Collision systems** from scratch.
* Designing the **Entity Management** logic to handle dynamic objects.
* Implementing game-specific systems like **spikes and environmental hazards** (`sys_spikes.asm`).
* Optimizing the rendering loop to maintain a stable frame rate.

## ⚠️ Compilation Note
This repository is a **code showcase**. Building the project requires the GBTelera toolchain and specific environment variables. It is provided as a portfolio piece to demonstrate Assembly proficiency and hardware understanding.

---
*Developed for academic purposes at University of Alicante.*