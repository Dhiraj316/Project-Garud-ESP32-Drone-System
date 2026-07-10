# 🦅 Project Garud

**A robust, custom-built ESP32 flight controller and quadcopter.**

---

## 1. System Architecture Overview

Project Garud bypasses commercial flight controllers, utilizing an ESP32 as the primary processing brain operating on a distributed processing model.

* **Data Flow:**
    1. **Pilot Input:** The transmitter transmits 6 channels of AFHDS 2A telemetry.
    2. **Signal Reception:** The receiver outputs raw PWM signals.
    3. **Interrupt Processing:** The ESP32 triggers hardware interrupts to read PWM pulse widths without pausing the main flight loop.
    4. **Sensor Fusion:** The MPU6050 feeds raw gravity and angular momentum data via I2C (400kHz).
    5. **PID Calculation:** The ESP32 calculates the error between Pilot Input and Sensor Data.
    6. **Motor Output:** The ESP32 sends adjusted PWM signals to four 30A ESCs to spin the A2212 motors.

---

## 2. Components required for quadcopter

### Primary Flight Hardware
* **Microcontroller:** ESP32 Development Board (30-pin variant)
* **Custom PCB:** ESP32 FlightController (Custom EasyEDA design)
* **IMU Sensor:** MPU6050 (6-axis Gyroscope & Accelerometer)
* **Frame:** F450 Nylon/Glass Fiber Quadcopter Frame
* **Motors:** 4x A2212 1000KV Brushless DC Motors
* **ESCs:** 4x 30A Electronic Speed Controllers (with internal 5V BEC)
* **Propellers:** 1045 (10x4.5) CW and CCW Props
* **Power:** 3S 11.1V 2200mAh 80C LiPo Battery(above 35c is sufficient)

---

## 3. Master Circuit & Wiring Schema

**CRITICAL WARNING:** Never trust wire colors alone. Always verify connections against the physical PCB copper traces. 

### Power Distribution
The system strictly isolates voltage regulators to prevent ESC burnout. 
* **High Voltage (11.1V):** LiPo battery connects directly to the PDB, distributing raw 11.1V to the thick red/black wires of all 4 ESCs.
* **Logic Voltage (5V):** **ONLY Motor 1 ESC (MOT1ESC)** supplies 5V to the custom PCB. The 5V traces for MOT2, MOT3, and MOT4 are intentionally left disconnected on the board.


#### A. IMU Sensor (MPU6050)
Connected via the dedicated I2C rail on the PCB board.
* **VCC:** 3.3V / 5V
* **GND:** GND
* **SCL:** GPIO 22
* **SDA:** GPIO 21

#### B. Motor Outputs (ESC Signal Pins)
* **Motor 1 (Front Right - CCW):** *Check flight controller code for final GPIO assignment.*
* **Motor 2 (Rear Right - CW):** *Check flight controller code for final GPIO assignment.*
* **Motor 3 (Rear Left - CCW):** *Check flight controller code for final GPIO assignment.*
* **Motor 4 (Front Left - CW):** *Check flight controller code for final GPIO assignment.*


*Overall the circuit is attach in the folder for the reference and the circuit connection of all components with ESP32.
---
*Document maintained by the Project Garud Team.*
