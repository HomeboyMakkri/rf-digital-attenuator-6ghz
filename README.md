# rf-digital-attenuator-6ghz 📡
![License](https://img.shields.io/badge/license-MIT-blue.svg)
![STM32](https://img.shields.io/badge/MCU-STM32F407-blue?logo=stmicroelectronics)
![Altium](https://img.shields.io/badge/PCB-Altium_Designer-orange)
![Frequency](https://img.shields.io/badge/RF-DC--6_GHz-red)
![Step](https://img.shields.io/badge/Resolution-0.5_dB-green)

A student open-source hardware project featuring a **6-bit Digital RF Attenuator** capable
of operating up to 6 GHz. Controlled by an **STM32F407VET6** and based on the **HMC624A**
(Analog Devices) silicon, this device provides precise signal level control via a simple 
USB-UART CLI or direct SPI interface.
The RF signal path features a grounded coplanar waveguide (GCPW) structure to ensure 50 Ohm impedance matching across the entire operating frequency range.

### Project Context & Disclaimer ⚠️

This project is my first deep dive into the world of embedded systems and RF design. The control logic is implemented using STM32F4 (developed via CubeMX + Keil with HAL libraries), communicating with the HMC624A attenuator via SPI. Serial communication is handled by an FT232RL bridge at a baud rate of 115200.

The hardware was designed from scratch in Altium Designer. Please note: this project is a learning experience. While it is fully functional, it should not be treated as a definitive reference or a textbook example. I am eager to learn and would sincerely appreciate any constructive criticism or suggestions for improvement!

💡 Quick Tip: Check the Project Structure section at the bottom of this file for easy navigation through the firmware and hardware source files.

---
## Control Command to set the attunuation level
Connect via any Serial Terminal (115200 8N1):
* `ATTEN XX.X` — Set attenuation (0 to 31.5)

## 🚀 Features

* **Wide Frequency Range:** Stable performance from 100 MHz to 6.0 GHz.
* **High Precision:** 6-bit attenuation with a fine 0.5 dB step resolution.
* **Robust RF Design:** 50 Ohm matched Coplanar Waveguides (CPW) optimized for 1.6mm FR4.
* **Dual Control:** Command-line interface (CLI) via FT232 USB-UART or high-speed SPI.
* **Plug-and-Play:** Powered and controlled through a single USB Type-C connector.

---

## 📊 Technical Specifications

| Parameter | Value | Notes |
| :--- | :--- | :--- |
| **Frequency Range** | 0.1 — 6.0 GHz | Optimized for 6 GHz |
| **Attenuation Range** | 0 — 31.5 dB | 6-bit control |
| **Step Size** | 0.5 dB | ±0.15 dB Typical Accuracy |
| **Insertion Loss** | ~2.2 dB | @ 2.0 GHz |
| **Input P1dB** | +24 dBm | 1dB Compression Point |
| **Control Interface** | UART (USB) / SPI | 115200 Baud |
| **Input Voltage** | 5.0 V | Via USB Type-C |

---

## 📸 Hardware Gallery

### PCB Overview
| Top View (MCU Side) | Bottom View (RF Side) |
| :---: | :---: |
| ![L1](docs/L1.png) | ![L2](docs/L2.png) |

### Key Components
| STM32F407VET6 | HMC624A Attenuator | FT232 UART Bridge |
| :---: | :---: | :---: |
| ![MCU](docs/STM32F407VET6/STM32F407VET6.png) | ![HMC624A](docs/HMC624A%20ATTUNUATOR/HMC624A%20ATTUNUATOR.png) | ![FT232](docs/FT232%20UART/FT232%20UART.png) |

---

## 📂 Project Structure

```text
├── hardware/          # Altium Designer project files
│   ├── PDF/           # Schematic exports in PDF format
│   └── Manufacturing/ # Production files (Gerber, BOM, Pick&Place)
├── firmware/          # STM32 Source Code (CubeIDE / Keil)
├── docs/              # Images and reference datasheets
└── README.md          # Project documentation
