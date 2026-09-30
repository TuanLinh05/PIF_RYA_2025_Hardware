# ⚡ PIF RYA 2025 – H-Bridge Motor Driver Hardware

![MCU](https://img.shields.io/badge/MCU-STM32F103RCT6-03234B?logo=stmicroelectronics&logoColor=white)
![Gate driver](https://img.shields.io/badge/Gate%20driver-IR2104-C62828)
![CAN](https://img.shields.io/badge/CAN-TJA1050-455A64)
![PCB](https://img.shields.io/badge/PCB-Altium%20Designer-A5915F)

Motor driver hardware designed for the **PIF RYA 2025** robot project (Pay It Forward). It has two boards that work together: an **STM32-based control board with CAN bus** and a **high-current MOSFET H-bridge** power board driven by **IR2104** gate drivers.

---

## 🧩 System overview

```text
            CAN bus (TJA1050)
                  │
┌─────────────────▼─────────────────┐    control    ┌─────────────────────────────┐        ┌───────┐
│ HBridgeMCU – control board        │ ────────────▶ │ HBridgeDriver – power board │ ─────▶ │ Motor │
│ STM32F103RCT6 · current sensing   │   signals     │ IR2104 + N-MOSFET H-bridge  │        └───────┘
│ protection · power                │               │ VDC 12–16 V                 │
└───────────────────────────────────┘               └─────────────────────────────┘
```

## ⚙️ Key specifications

| Item | Value |
| :-- | :-- |
| Microcontroller | **STM32F103RCT6**: ARM Cortex-M3, 72 MHz, 256 KB Flash |
| Communication | **CAN bus** through a **TJA1050** transceiver |
| Motor supply (VDC) | **12–16 V**, isolated from the control side |
| Power stage | N-MOSFET H-bridge with **IR2104** half-bridge gate drivers |
| Protection | Resettable fuse (over-current), VDC protection circuit, isolation between control and power stages |
| Feedback | Motor current sensing |

## 📂 Repository structure

Each board follows the same folder layout:

```text
PIF_RYA_2025_Hardware/
├── 1.HBridgeMCU/              # Control board
│   ├── 1.Project/             # Altium project (RYA_MotorMCU.PrjPcb)
│   ├── 2.Schematic/           # TopLevel, BlockDiagram, MCU, POWER, CAN_IC,
│   │                          # CurrentSense, Protect, VDCProtect, MotorDriverConnector
│   ├── 3.Layout/              # PCB layout + panel
│   ├── 4.Mechanic/            # 3D STEP model
│   ├── 5.Gerber/              # Manufacturing files
│   └── 6.BOM/                 # Bill of materials (.xlsx)
└── 2.HBridgeDriver/           # Power board
    ├── 2.Schematic/           # TopLevelDesign, MotorDriver
    ├── 3.Layout/              # RYA_MotorDriver PCB + panel
    ├── 4.Mechanic/ · 5.Gerber/ · 6.BOM/
    └── 1.Project/
```

## 🚀 Usage

- Open the `.PrjPcb` files in **Altium Designer** to view or edit the schematics and PCBs.
- Send the `5.Gerber` outputs to a PCB manufacturer, and use the `6.BOM` spreadsheets to order parts.

---

<p align="center">Made by <a href="https://github.com/TuanLinh05">Vu Tuan Linh</a> · HCMUT · Pay It Forward</p>
