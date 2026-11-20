# Macropad

A custom 12-key macropad with **2 rotary encoders** and **per-key RGB LED lighting**, designed in KiCad as a compact USB HID device for shortcuts, media control, and creative workflows.

![Macropad render](images/macropad-hero.png)

---

## Features

- **12 mechanical key switches** in a 4x3 matrix ([hot-swap / solder])
- **2 rotary encoders** with push buttons (volume, scrolling, zoom, etc.)
- **RGB LED lighting** ([SK6812MINI-E / WS2812B], addressable)
- **USB-C** for power and data
- **[MCU]** microcontroller ([RP2040 / STM32 / ATmega32U4])
- **3D-printable [case / plate]** (`Macropad.stl`)
- Firmware: [QMK / KMK / CircuitPython]

---

## Schematic

![Schematic](images/schematic.png)

| Block | Description |
|---|---|
| MCU | [MCU], [clock details] |
| Key matrix | 4x3, one 1N4148W diode per switch |
| Encoders | 2x EC11, A/B/SW to GPIO |
| RGB | Single data line daisy-chained through all LEDs |
| USB | USB-C, 5.1k CC pull-downs |
| Power | [5V from USB, 3.3V LDO] |

---

## PCB

| Front | Back |
|---|---|
| ![PCB front](images/pcb-front.png) | ![PCB back](images/pcb-back.png) |

![PCB 3D render](images/pcb-3d.png)

- **Size:** [XX x XX mm]
- **Layers:** [2]
- **Thickness:** 1.6 mm
- **Tool:** KiCad [8 / 9]

---

## Pinout

| Function | GPIO |
|---|---|
| Matrix rows (R0-R2) | [GPx, GPy, GPz] |
| Matrix cols (C0-C3) | [GPa, GPb, GPc, GPd] |
| Encoder 1 (A / B / SW) | [GPx / GPy / GPz] |
| Encoder 2 (A / B / SW) | [GPx / GPy / GPz] |
| RGB data | [GPx] |

---

## Bill of Materials

| Qty | Part | Notes |
|---|---|---|
| 1 | [MCU] | [package] |
| 12 | MX-style switches | 3-pin or 5-pin |
| 12 | 1N4148W diodes | SOD-123 |
| 12 | [SK6812MINI-E] | per-key RGB |
| 2 | EC11 rotary encoder | with push switch |
| 1 | USB-C receptacle | 16-pin |
| - | [Passives, crystal, LDO] | [fill in] |

---

## Repository Files

| File | Description |
|---|---|
| `Macropad.kicad_pro` | KiCad project (open this one) |
| `Macropad.kicad_sch` | Schematic |
| `Macropad.kicad_pcb` | PCB layout |
| `Macropad.stl` | 3D-printable [case / plate] |

---

## Getting Started

1. Clone the repo: `git clone https://github.com/AndersonsDevlog/Macropad.git`
2. Open `Macropad.kicad_pro` in KiCad.
3. Export Gerbers: **File > Fabrication Outputs > Gerbers**, then upload to [JLCPCB / PCBWay].
4. Print `Macropad.stl` ([material], [layer height]).
5. Solder SMD parts first (diodes, LEDs, USB-C), test, then add switches and encoders.
6. Flash firmware (see below).

---

## Firmware

```bash
# [flash command here]
```

| Input | Action |
|---|---|
| K1-K12 | [Copy, Paste, Undo, Mute, ...] |
| Encoder 1 | Volume / Push = Mute |
| Encoder 2 | Scroll / Push = [Play/Pause] |

---

## Roadmap

- [ ] Add firmware
- [ ] Rev B: [improvement]
- [ ] Per-layer RGB effects

---

## License

[MIT / CERN-OHL-P-2.0 / CC BY-SA 4.0]

## Author

**Johnny Kwon** - [@AndersonsDevlog](https://github.com/AndersonsDevlog)
