# A WBAN-ECG & Pulse Oximetry Approach for Real-time Long Distance Monitoring

## 📋 Project Overview

This project implements a **Wireless Body Area Network (WBAN)** system for **real-time vital signs monitoring**. By integrating an Electrocardiogram (ECG) sensor and a Pulse Oximeter, the system captures crucial physiological data and transmits it **wirelessly via Bluetooth** to a **mobile device** for immediate display and patient diagnosis.

The system is designed for mobility and convenience, leveraging the **ESP32's integrated Bluetooth** capabilities for a local, short-range monitoring solution.



---
## ✨ Features

* **Real-time Monitoring:** Continuous acquisition and display of vital signs.
* **Dual Vital Sign Capture:** Measures both cardiac electrical activity (**ECG**) and blood oxygen/pulse rate (**%SpO2 and PRbpm**).
* **Wireless Communication:** Utilizes **Bluetooth Serial** for reliable, short-range data transmission to a paired mobile application (Smartphone/Tablet).
* **Local Data Display:** Features an on-device **1.8" TFT LCD** for immediate, visual feedback of the readings.

---
## 🛠️ Hardware Requirements

| Component | Description |
| :--- | :--- |
| **Microcontroller (Gateway)** | **ESP32** (ESP-WROOM-32s Module) for processing sensor data and handling **Bluetooth** communication. |
| **ECG Sensor** | **AD8232** Heart Rate Monitor (3-Lead) for measuring the electrical activity of the heart. |
| **Pulse Oximeter** | **MAX30102** for measuring Blood Oxygen Saturation (SpO2) and Heart Rate (PRbpm). |
| **Display** | **1.8" TFT LCD Module** (IC: ST7735, 128x160 resolution) for on-device display. |
| **Electrodes/Cables** | ECG Electrodes and necessary wiring (e.g., jumper wires). |



---
## 📌 Wiring and Setup (High-Level)

### 1. Sensor Connections
* **AD8232 (ECG)**: Analog Output connects to an Analog Pin on the ESP32.
* **MAX30102 (SpO2)**: Connects to the ESP32 via the **I2C** interface (SDA, SCL).
* **1.8" TFT LCD (ST7735)**: Connects to the ESP32 via the **SPI** interface (SCL, SDA, CS, DC, RST).

### 2. Bluetooth Communication
* The ESP32 is programmed to act as a **Bluetooth Serial Server**.
* A **Mobile Application** is used to pair and connect to the ESP32's Bluetooth device.
* Processed vital sign data is continuously streamed over the **Bluetooth Serial connection** to the mobile app for remote visualization.
  
---
## 💻 Software and Libraries

The project is typically developed using the **Arduino IDE** or **VS Code with PlatformIO**. Key software components include:

1.  **Microcontroller Code (ESP32):** Utilizes the `BluetoothSerial.h` library for communication.
2.  **Mobile Application:** A custom Android/iOS application (or a generic serial terminal app) is required to receive and interpret the data stream.

Essential libraries for the ESP32 sketch:
* `BluetoothSerial.h`
* `AD8232 Library` (for ECG signal processing)
* `MAX30102 Library` (for SpO2 and Heart Rate calculation)
* `Adafruit GFX` and `Adafruit ST7735` (for TFT display control)

---
## ▶️ Output Data

The mobile application and the on-device display present the following vital signs:

| Parameter | Unit/Format | Source | Display/Transmission |
| :--- | :--- | :--- | :--- |
| **Electrocardiogram (ECG)** | Raw or Processed Waveform | AD8232 | **Mobile App** (Waveform Plot) |
| **Blood Oxygen Saturation** | **%SpO2** (Percentage) | MAX30102 | **Local TFT LCD** and **Mobile App** |
| **Heart Rate** | **PRbpm** (Beats Per Minute) | MAX30102 | **Local TFT LCD** and **Mobile App** |
