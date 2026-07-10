# 🛠️ Project Garud: Master Hardware & Assembly Guide

**A complete engineering manual for the physical construction, electronic design, and high-current power routing of the Garud ESP32 autonomous quadcopter.**

---

## 1. Comprehensive Bill of Materials (BOM)

### Primary Flight Hardware
* **Microcontroller:** ESP32 Development Board (30-pin variant)
* **Custom PCB:** Drone FC ESP32 (Custom EasyEDA design)
* **IMU Sensor:** MPU6050 (6-axis Gyroscope & Accelerometer)
* **Frame:** F450 Nylon/Glass Fiber Quadcopter Frame
* **Motors:** 4x A2212 1000KV Brushless DC Motors
* **ESCs:** 4x 30A Electronic Speed Controllers (with internal 5V BEC)
* **Propellers:** 1045 (10x4.5) CW and CCW Props
* **Power:** 3S 11.1V 2200mAh 80C LiPo Battery

---

* **Isolated Power Delivery:** The ESC logic power (5V) is strategically isolated to draw from a single BEC (Motor 1). The 5V traces for MOT2, MOT3, and MOT4 are intentionally left disconnected to prevent voltage regulator conflicts and thermal overload.
* **Dedicated I2C Bus:** Clean traces routed directly for the MPU6050 IMU to ensure stable 400kHz sensor polling.
* **PWM Signal Matrix:** 6-channel receiver input block and 4-channel ESC output block cleanly broken out for plug-and-play assembly.

*(Note: Gerber ZIP files, EasyEDA schematics, and 2D PDFs for fabrication are located in the `Hardware_Design/` directory).*

---

## 3. System Wiring & Pinout Map

**NOTE:** Never trust wire colors alone. Always verify connections against the physical PCB copper traces. 


### B. IMU Sensor (MPU6050)
Connected via the dedicated I2C rail on the Garud FC board.
* **SCL:** GPIO 22
* **SDA:** GPIO 21

---

## 4. Power System & High-Current Soldering
**WARNING:** The 3S LiPo battery can discharge over 100 Amps instantaneously. A short circuit on the Power Distribution Board (PDB) can result in catastrophic failure or fire. 

### Step 1: PDB Soldering
1. **Tin the Pads:** Apply flux and melt a smooth dome of 60/40 rosin core solder onto all main `+` and `-` pads on the F450 PDB.
2. **Main Battery Lead:** Solder the XT60 pigtail (Red to `+`, Black to `-`). Ensure joints are shiny and smooth.
3. **ESC High-Voltage Wires:** Cut the thick red and black wires of all four ESCs to length. Solder Red to PDB `+` and Black to PDB `-`.

### Step 2: Motor to ESC Connections
1. Solder 3.5mm gold bullet connectors to the three wires on the A2212 motors and the three output wires on the ESCs. Cover female ends in heat shrink.
2. Plug the three motor wires into the ESC in **any random order**. 
3. *Direction Reversal:* If a motor spins the wrong direction during testing, simply unplug ANY TWO of the three bullet connectors and swap them to reverse the magnetic phasing.

---

## 5. Physical Assembly & Pre-Flight Checks

1. **The "Smoke Test" (Crucial):** Before plugging in the battery, use a Multimeter in Continuity Mode across the XT60 connector. If it beeps continuously, you have a short circuit on the PDB. DO NOT plug in the battery until the short is fixed.
2. **Vibration Isolation:** The Garud FC PCB must be mounted using rubber standoffs or thick double-sided foam tape. Hard-mounting the board will transfer motor vibrations directly into the MPU6050 gyroscope, causing erratic flight.
3. **Propeller Configuration:** Ensure the 1045 CW (Clockwise) and CCW (Counter-Clockwise) propellers are mounted on the correct diagonal axes based on the final flight controller motor mapping.