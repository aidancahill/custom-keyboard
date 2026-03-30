# Bill of Materials

## Electronics

| Qty | Component | Package | Part Number | Source | Est. Price |
|-----|-----------|---------|-------------|--------|------------|
| 54 | Kailh Choc V1 hotswap sockets | — | — | LowproKB | $10.50 |
| 60 | Ambients Silent Twilight switches (or any Choc V1) | PG1350 | — | LowproKB | $78.00 |
| 54 | MBK 1u keycaps | Choc V1 | — | LowproKB | $21.00 × 6 |
| 2 | MBK homing keycaps | Choc V1 | — | LowproKB | $1.10 |
| 54 | 1N4148W diodes | SOD-123 | 1N4148W-13-F | DigiKey | ~$5 |
| 3 | 74HC595 shift registers | SOIC-16 | SN74HC595DR | DigiKey | ~$3 |
| 1 | 74HC165 shift register | SOIC-16 | SN74HC165DR | DigiKey | ~$1 |
| 7 | 10kΩ resistors | 0805 SMD | — | Amazon | $5 |
| 1 | Seeeduino XIAO nRF52840 BLE (pre-soldered) | — | 102010631-FA | Amazon | $18 |
| 2 | COM-09032 joysticks | — | COM-09032 | SparkFun | ~$10 |
| 1 | TL3342 reset button | SMD | — | DigiKey | ~$1 |
| 2 | 7-pin 2.54mm female header sockets | Through-hole | — | Amazon | $9 (25-pack) |

## Hardware

| Qty | Component | Spec | Source | Est. Price |
|-----|-----------|------|--------|------------|
| 8+ | M2 heat-set brass inserts | M2 × 4mm | Amazon (ruthex) | ~$8 (70-pack) |
| 8 | M2 socket head cap screws | M2 × 5mm | Amazon | ~$8 |

## PCB

| Item | Spec |
|------|------|
| Layers | 2 |
| Thickness | 1.6mm |
| Surface finish | HASL or ENIG |
| Solder mask | Any color (black recommended) |
| Silkscreen | White |
| Min track/spacing | 6/6 mil |
| Min hole size | 0.3mm |

Order from JLCPCB or PCBWay. Upload the gerber zip from `pcb/gerbers/`. Minimum order is usually 5 boards.

## 3D Printed Case

| Item | File | Material | Settings |
|------|------|----------|----------|
| Case (with integrated 3mm bottom) | `case/stl/case_3mm_bottom.stl` | PETG or PLA | 50% infill, 0.2mm layer height |

Print yourself or order from PCBWay's 3D printing service.

## Tools Required

- Soldering iron with fine tip (conical or chisel)
- Tweezers (angled tip preferred)
- Flux (pen or paste)
- Solder wire (0.5-0.8mm diameter, leaded recommended for beginners)
- Solder wick (for fixing mistakes)
- Isopropyl alcohol 91%+ (for cleaning flux)
- Toothbrush (for scrubbing flux)
- Soldering iron (for heat-set inserts)

## Estimated Total Cost

| Category | Cost |
|----------|------|
| Switches + keycaps | ~$115 |
| Electronics (diodes, ICs, MCU, headers) | ~$45 |
| PCB (5 pcs) | ~$15-25 |
| 3D printed case | ~$10-30 |
| Hardware (screws, inserts) | ~$16 |
| **Total** | **~$200-230** |
