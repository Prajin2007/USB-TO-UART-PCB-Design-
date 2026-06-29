# 🔌 USB to UART Converter PCB

A compact USB Type-C to UART converter designed in KiCad, built around the **CP2102N** USB-to-UART bridge IC. Features ESD protection, TX/RX indicator LEDs, and a 5-pin header output.

---

##  Overview

This PCB provides a reliable USB to UART serial interface using Silicon Labs CP2102N. It accepts USB Type-C input and exposes UART signals (TX, RX, RST, VBUS, GND) via a 5-pin header — useful for programming and debugging microcontrollers like STM32, ESP32, and Arduino.

---

## 🔧 Specifications

| Parameter | Value |
|:----------|:------|
| USB Interface | USB Type-C (USB 2.0) |
| Bridge IC | CP2102N-Axx-xQFN28 |
| Output Header | 5-pin (GND, VBUS, RX, TX, RST) |
| ESD Protection | LESD5D5.0CT1G on D+/D- lines |
| TX/RX Indicators | Dual LEDs (D1, D2) |
| CC Resistors | 5.1k (R1, R2) for Type-C detection |
| Decoupling | 100nF caps on VBUS and VDD |
| RST Pull-up | 10k (R3) |
| EDA Tool | KiCad |

---

## 🧠 How It Works

```
USB Type-C Input (J1)
        │
        ├── CC1, CC2 → R1, R2 (5.1k) — USB-C orientation detection
        ├── D+, D-   → ESD diodes (D3, D4, D5) — protection
        │
        ▼
   CP2102N (U1)
   USB-to-UART Bridge IC
        │
        ├── TXD → LED (D1) → TX pin on J2
        ├── RXD → LED (D2) → RX pin on J2
        ├── RST → R3 (10k pull-up) → RST pin on J2
        ├── VBUS → VBUS pin on J2
        └── GND  → GND pin on J2
        │
        ▼
  5-pin Header (J2)
  GND | VBUS | RX | TX | RST
```

1. **USB Type-C receptacle** — modern reversible connector, CC resistors handle orientation
2. **ESD protection** — guards the D+/D- data lines from electrostatic discharge
3. **CP2102N** — handles all USB enumeration and converts USB packets to UART signals
4. **TX/RX LEDs** — blink during data transfer, useful for debugging
5. **5-pin header** — plug directly into target microcontroller UART pins

---

## 🧩 Bill of Materials

| Ref | Component | Value | Package |
|:----|:----------|:------|:--------|
| U1 | USB-UART Bridge | CP2102N-Axx-xQFN28 | QFN-28 |
| J1 | USB Type-C Receptacle | USB2.0 16P | SMD |
| J2 | Pin Header | 5-pin | Conn_01x05 |
| D1, D2 | LED | TX/RX Indicator | SMD |
| D3, D4, D5 | ESD Diode | LESD5D5.0CT1G | SOT-23 |
| R1, R2 | Resistor | 5.1k | 0402 |
| R3 | Resistor | 10k | 0402 |
| R4, R5, R6, R7 | Resistor | Current limit | 0402 |
| C1, C2 | Capacitor | 100nF | 0402 |
| C3, C4 | Capacitor | Decoupling | 0402 |

---

## 🖼️ Screenshots

### Schematic
<img width="1482" height="810" alt="Screenshot 2026-06-29 141354" src="https://github.com/user-attachments/assets/838fb826-1e81-43e3-b13f-44b2297c9181" />


### PCB Layout
<img width="1295" height="592" alt="Screenshot 2026-06-29 141412" src="https://github.com/user-attachments/assets/eef3b4c3-5a4a-42f6-890f-516f6cbc060f" />


---

## 🔌 Pinout — Output Header (J2)

| Pin | Signal | Description |
|:---:|:-------|:------------|
| 1 | GND | Ground |
| 2 | VBUS | 5V USB Power |
| 3 | RX | UART Receive |
| 4 | TX | UART Transmit |
| 5 | RST | Reset |

---

## 🛠️ Tools Used

![KiCad](https://img.shields.io/badge/KiCad-314CB0?style=flat-square&logo=kicad&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white)

---

## 📚 What I Learned

- USB Type-C connector wiring and CC resistor configuration
- CP2102N IC integration and decoupling best practices
- ESD protection placement on high-speed USB data lines
- Compact PCB layout with SMD components
- LED indicator circuit design for TX/RX activity

---

## 👤 Author

**Prajin S**
B.Tech Electronics and Instrumentation Engineering, VIT Vellore

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Prajin%20S-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/prajin-s-5880b3328/)
[![GitHub](https://img.shields.io/badge/GitHub-Prajin2007-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/Prajin2007)

---

*Designed as part of my PCB design learning journey — EIE, VIT Vellore.*
