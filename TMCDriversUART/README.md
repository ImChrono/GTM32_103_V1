# Geeetech A30T GTM32_103_V1 UART Conversion

## ⚠️ Attention: Proceed with Caution! ⚠️
This modification involves delicate hardware changes that require precision and attention to detail. Mistakes in wiring or soldering can permanently damage your **GTM32_103_V1 board**. 

- **Double-check connections** before applying power.
- Use proper tools and follow best practices for soldering.
- If you are not confident in your skills, seek assistance from an experienced individual or professional.

**You proceed at your own risk.**

## Overview
This guide details the process of modifying the **GTM32_103_V1** 3D printer controller board to enable UART capabilities. The GTM32_103_V1 board features 7 **TMC2208 drivers** operating in standalone mode by default. This modification involves **removing the SD card slot** and repurposing its pinouts for UART communication.

---

## Features of the Modification
- **UART Capability**: Enables communication with TMC2208 drivers via UART repurposing the SDCard slot
---

## Hardware Changes

### Components Modified
- **SD Card Slot**: Removed entirely to free up pinouts for UART.
- **Repurposed Pins**: SD card slot pins are reassigned as per the following table:

| TCM2208 Driver | SD Card Pin | STM32 Pin |
|-------------|-------------|-----------|
| Motor0   | 9           | PC7       |
| Motor1   | 8           | PC9       |
| Motor2   | 7           | PC8       |
| Motor3   | 5           | PC12      |
| Motor4   | 3           | PD2       |
| Motor5   | 2           | PC11      |
| Motor6   | 1           | PC10      |

### Procedure
1. **Remove Pull down resistor from each driver**:
   - Desolder the SMD 1kΩ resistor carefully to avoid damaging the surrounding components.

| TMCDriver | PCB Code |
|----------|---------------|
| Motor0   | R53           |
| Motor1   | R57           |
| Motor2   | R62           |
| Motor3   | R120          |
| Motor4   | R71           |
| Motor5   | R95           |
| Motor6   | R105          |

2. **Remove the SD Card Slot**:
   - Desolder the SD card slot carefully to avoid damaging the surrounding components.
3. **Repurpose the Pinouts**:
   - Rewire the SD card pins according to the table above.
   - Connect each pin to its corresponding UART connection for the TMC2208 drivers.

---

## Testing and Validation
After completing the hardware changes:
1. Connect the board to your 3D printer and power it on.
2. Use your firmware to verify UART communication with each TMC2208 driver.
3. Check for successful responses from the drivers using a terminal or debugging tool.

---

## Photos
Add your photos here to demonstrate the modification process and results:
- Close-up of the TMC driver
![WIN_20241111_22_06_27_Pro](https://github.com/user-attachments/assets/4087cb87-09ce-43fb-89e6-a46cbd3ec37b)

-Close-up of the TMC driver with resistor removed (solder the uart pint to the red signed pin)
![WIN_20241111_22_15_44_Pro](https://github.com/user-attachments/assets/93e99aad-5389-4c93-af6b-74d5a9548cf5)

- Close-up of the SD card:
![WIN_20241111_22_05_02_Pro](https://github.com/user-attachments/assets/35ce51f2-bd2b-458f-81bd-13cbf3f81ff3)

- Rewired pins with labels.
![WIN_20241116_22_14_33_Pro](https://github.com/user-attachments/assets/3f5f9d90-09a0-4491-9dab-4a77afd2b4ca)
