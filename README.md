# Multi-Elevator Control System (Verilog HDL)

![Verilog](https://img.shields.io/badge/Language-Verilog-blue) ![Tool](https://img.shields.io/badge/Simulation-Xilinx%20Vivado-red) ![Status](https://img.shields.io/badge/Status-Completed-success)

> **A smart, modular multi-elevator controller designed for modern vertical transportation, featuring intelligent request scheduling and robust FSM-based logic.**

## 📖 Table of Contents
- [Project Overview](#project-overview)
- [Key Features](#key-features)
- [System Architecture](#system-architecture)
- [Design Methodology](#design-methodology)
  - [Finite State Machine](#finite-state-machine)
  - [Request Manager (Nearest Car Algorithm)](#request-manager-nearest-car-algorithm)
- [Simulation Results](#simulation-results)
- [Future Work](#future-work)
- [Team Members](#team-members)

---

## 🚀 Project Overview

Modern multi-story buildings require efficient elevator systems to minimize passenger wait times and energy consumption. [cite_start]This project implements a **Multi-Elevator Control System** using **Verilog HDL**, simulated in **Xilinx Vivado**[cite: 55, 57, 61].

The system controls **two elevators serving six floors**, handling internal cabin requests, external floor requests, and door operations simultaneously. [cite_start]Unlike traditional controllers, this system employs a centralized **Request Manager** that dynamically assigns floor requests to the optimal elevator based on proximity and direction[cite: 59, 60].

---

## ✨ Key Features

* [cite_start]**Scalable Architecture:** Modular design currently supporting 2 elevators and 6 floors, easily extendable to more[cite: 59, 146].
* [cite_start]**Intelligent Scheduling:** Implements the **Nearest Car Algorithm** to assign requests to the closest available elevator[cite: 58, 143].
* [cite_start]**Robust FSM Controller:** Each elevator operates on an independent Mealy-style Finite State Machine (FSM) handling movement, stopping, and door logic[cite: 107].
* [cite_start]**Realistic Timing:** Integrated timers for `MOVE_DELAY` (floor-to-floor travel) and `DOOR_OPEN_TIME` (passenger boarding) [cite: 130-133].
* [cite_start]**Conflict Resolution:** Efficiently handles simultaneous Up/Down requests and internal vs. external priority[cite: 66].

---

## 🏗 System Architecture

[cite_start]The design is divided into three major hierarchical modules [cite: 78-80]:

1.  **Elevator Controller:** The core logic unit for a single elevator car (Movement, Door, Display).
2.  **Request Manager:** The central "brain" that receives global hall buttons and assigns them to specific elevators.
3.  **Top-Level System:** Integrates the controllers and manager into a unified system.

![System Block Diagram](assets/block_diagram.png)
*(Note: Upload the block diagram from Page 4 of your report here)*

---

## ⚙️ Design Methodology

### Finite State Machine
[cite_start]Each elevator utilizes a **5-state Mealy FSM** to ensure safe and predictable operation[cite: 108]:

| State (Binary) | Description |
| :--- | :--- |
| **IDLE (000)** | [cite_start]No movement, waiting for requests[cite: 113, 120]. |
| **MOVING (001)** | [cite_start]Elevator is in transit (Up/Down)[cite: 115, 120]. |
| **DOOR_OPENING (010)** | [cite_start]Transition state from closed to open[cite: 117, 121]. |
| **DOOR_OPEN (011)** | [cite_start]Door is fully open for passengers[cite: 118, 122]. |
| **DOOR_CLOSING (100)** | [cite_start]Door closing after service is complete[cite: 118, 122]. |

### Request Manager (Nearest Car Algorithm)
The Request Manager acts as a dispatcher. It collects all `Up` and `Down` floor button presses and evaluates:
1.  **Distance:** How far is each elevator from the request?
2.  **Direction:** Is the elevator already moving toward the request?
3.  **Status:** Is the elevator IDLE?

[cite_start]It calculates a "Distance Score" and assigns the request to the elevator with the lowest score, optimizing wait times [cite: 143, 590-607].

---

## 📊 Simulation Results

The system was validated using **Xilinx Vivado**. The testbenches (`tb_single_elevator` and `tb_full_system`) verified:
* Correct state transitions.
* Accurate floor stops.
* Proper door opening/closing sequences.
* Successful assignment of simultaneous requests to different elevators.

![Simulation Waveform](assets/simulation_waveform.png)
*(Note: Upload the waveform screenshot from Page 18 of your report here)*

---

## 🔮 Future Work

[cite_start]To further enhance this system for real-world deployment, we plan to [cite: 988-990]:
* [ ] Implement Emergency Stop features.
* [ ] Add Load-Based logic (skipping stops if the car is full).
* [ ] Deploy the design on a physical **FPGA** board.
* [ ] Integrate a graphical floor display and voice-based input.

---

## 👥 Team Members

**Group Members:**
* [cite_start]**Asma Channa** (CMS: 133-22-0042) [cite: 9, 10]
* [cite_start]**Muhammad Usman** (CMS: 133-22-0016) [cite: 7, 8]

**Institution:**
[cite_start]Department of Computer Systems Engineering, **Sukkur IBA University**[cite: 14, 15].

**Supervisor:**
[cite_start]Dr. Kashif Hussain[cite: 12].

---

*This project was developed as part of the Digital System Design course requirements.*
