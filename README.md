# ⚡ Barrel Jack to USB-C Charging Mod — Lenovo ThinkPad X121e

> Replacing the proprietary barrel jack charging port on a Lenovo ThinkPad X121e with a USB-C Power Delivery input, enabling charging via any standard USB-C PD charger.

---

## 📋 Overview

The ThinkPad X121e ships with a proprietary **65W barrel jack** connector for charging.  
This mod replaces it with a **USB-C PD decoy board**, allowing the laptop to be charged using any modern USB-C Power Delivery charger — with no modifications to the motherboard.

> ⚠️ This mod provides **charging only**. USB-C data transfer and video output are not supported, as the laptop's hardware does not include a USB-C controller.

---

## 🛠️ Components Used

| Component | Details |
|-----------|---------|
| Laptop | Lenovo ThinkPad X121e |
| Original connector | Barrel jack (proprietary, 65W) |
| USB-C Board | USB-C PD Decoy Board (Usb-Pwr) — supports 5V / 9V / 12V / 15V / 20V via jumper config |
| Output voltage set | **20V** (matching ThinkPad X121e requirement) |
| Connection method | Direct wire splice — VCC and GND pads |

---

## ⚙️ How It Works

The board acts as a **USB Power Delivery decoy**:
1. When a USB-C PD charger is connected, the board negotiates with the charger using the PD protocol
2. Based on the jumper configuration (S1/S2/S3), it requests a specific voltage — in this case **20V**
3. The board outputs that voltage on its VCC/GND pads, which are wired directly to the laptop's power rails

The laptop receives 20V as it would from the original barrel jack charger — no firmware or BIOS changes needed.

---

## 🔧 Build Steps

1. **Identify** the original barrel jack wires inside the laptop (positive VCC and GND)
2. **Cut** the barrel jack cable, leaving enough wire length to work with
3. **Configure** the jumpers on the PD board for **20V output** (S1=0, S2=0, S3=1 or per board datasheet)
4. **Solder** the original VCC wire to the VCC pad on the board
5. **Solder** the original GND wire to the GND pad on the board
6. **Insulate** all exposed solder joints with heat shrink tubing
7. **Mount** the board inside the laptop chassis in a secure position
8. **Test** with a USB-C PD charger before closing the case

---

## ✅ Result

- Laptop charges via any **USB-C Power Delivery** charger (minimum 20V PD support required)
- Clean internal installation — no visible external modifications beyond the new USB-C port
- Original barrel jack removed and replaced
- Charging-only functionality maintained reliably

---

## ⚠️ Important Notes

- **Verify your laptop's required voltage before configuring the jumpers** — incorrect voltage can damage the motherboard
- The ThinkPad X121e requires **20V** — do not use a lower voltage setting
- Use a USB-C charger that explicitly supports **USB PD at 20V** (most 65W+ GaN chargers do)
- Insulate all connections carefully — a short inside the chassis can cause serious damage
- This mod voids any remaining warranty

---

## 📌 Compatibility

This approach works on any laptop where:
- The charging circuit accepts a fixed DC voltage (no proprietary handshake required)
- There is physical space inside the chassis for the board
- The required voltage is supported by the PD board (5V / 9V / 12V / 15V / 20V)

---

*Project by [@falcoserves](https://github.com/falcoserves)*
