# Project-Garud-ESP32-Drone-System
custom-built ESP32 flight controller and quadcopter system. Designed hardware, flight control firmware, and mobile ground control station.

This repository contains the complete hardware schematics, flight control firmware, and mobile ground control station code developed by a four-person B.Tech Electronics and Telecommunication Engineering (ENTC) team at R. C. Patel Institute of Technology (RCPIT), Shirpur.

---

## 🚀 System Architecture overview

Project Garud is built from the ground up, bypassing commercial flight controllers to utilize an ESP32 as the primary processing brain. The system is split into three core domains:

### 1. Hardware & Propulsion
* **Flight Controller:** Custom-designed PCB housing an ESP32 (30-pin) microcontroller.
* **Inertial Measurement Unit (IMU):** MPU6050 Gyroscope/Accelerometer for real-time PID stabilization.
* **Frame & Motors:** F450 Quadcopter Frame equipped with A2212 1000KV brushless motors and 1045 propellers.
* **Power Delivery:** 30A Electronic Speed Controllers (ESCs) powered by a high-discharge 3S 2200mAh 80C LiPo battery (Optimized for ~7-8 minutes of active flight time).

### 2. Mobile Ground Control Station
* **Application:** Custom Android application serving as the pilot interface.
* **Tech Stack:** Modern Android development utilizing **Kotlin** and **Jetpack Compose** for a highly responsive, low-latency UI.
* **Features:** Live telemetry monitoring and mission parameter configuration.

---

## 📂 Repository Structure

To maintain a clean and collaborative environment for the engineering team, this repository is divided into specific subsystems:

* `📁 Flight_Controller/`
  * Contains the core C++ ESP32 firmware, including the MPU6050 balancing math, PID loops, custom PWM deadband logic, and receiver interrupts.
* `📁 Hardware_Drone/`
  * Contains the Reasearch and assembling of the Quadcopter components according to their specification required.
* `📁 Communication_System/`
  * Contains the Communication with TX and RX or source code for the Android mobile application.
* `📁 Hardware_Design/`
  * Contains the EasyEDA schematics, PCB layout files, and Gerber ZIPs for the custom Banana-1.4 board.
* `📁 Docs/`
  * Contains circuit wiring diagrams, component datasheets, project roadmaps, and presentation materials.

---
*Developed by Dhiraj Tribhuvan and Team | B.Tech Major Project*
