# HackDucky

RP2040-based open-source USB BadUSB with PicoDucky support.

[![](https://img.shields.io/github/stars/souptik-samanta/Hackducky?style=flat-square)](https://github.com/souptik-samanta/Hackducky)
[![](https://img.shields.io/github/forks/souptik-samanta/Hackducky?style=flat-square)](https://github.com/souptik-samanta/Hackducky)
[![](https://img.shields.io/badge/license-MIT-blue?style=flat-square)](LICENSE)
[![](https://img.shields.io/badge/Hack%20Club-supported-ec3750?style=flat-square)](https://hackclub.com)

![HackDucky Device](./img/sm_black_top%20(1).png)

## What is HackDucky

HackDucky is a compact, fully open-source USB device based on the RP2040 microcontroller. It emulates a USB keyboard, enabling automated input on any host system that accepts standard HID devices. The project includes everything needed to build your own: KiCad source files, production gerbers, and compatible firmware examples. With 16MB of flash storage, dual USB interfaces (USB-A and USB-C), a micro SD card slot, and an RGB Neopixel for status indication, HackDucky is a practical platform for exploring USB security concepts, automation scripting, and open hardware design.

## Gallery

<p align="center">
  <img src="./img/sm_black_top (1).png" width="45%" />
  <img src="./img/sm_black_bottom (1).png" width="45%" />
</p>

<p align="center">
  <img src="./gallery/render_top.png" width="45%" />
  <img src="./gallery/render_bottom.png" width="45%" />
</p>

## Features

- RP2040 dual-core ARM Cortex-M0+ @ 133MHz
- 16MB external QSPI flash
- USB 2.0 High-Speed (USB-C and USB-A connectors)
- Micro SD card slot for payload storage
- RGB Neopixel (SK6812-EC20) for visual feedback
- Custom designed open-source PCB
- All design files available in KiCad format

## BadUSB and PicoDucky

BadUSB refers to a class of devices that emulate standard USB human interface devices—typically keyboards—to inject keystrokes into a host computer. The host treats the device as a legitimate keyboard and executes the commands automatically, enabling rapid automation or security testing scenarios. HackDucky implements this capability by using the RP2040's USB peripheral to present itself as a HID keyboard device.

PicoDucky is a popular firmware project that makes this practical. It reads a "DuckyScript" from storage and plays back the keystrokes as if typed by a user. DuckyScript is a simple scripting language that maps to keyboard actions. Here is an example payload that opens a notepad and types a message:

```
DELAY 500
GUI r
DELAY 300
STRING notepad
ENTER
DELAY 1000
STRING Hello from HackDucky!
```

This script waits, opens the Run dialog, types "notepad", presses Enter, waits for the application to load, and then types a message. PicoDucky firmware on HackDucky can execute such scripts when triggered, either automatically on boot or via specific conditions.

## Getting Started

1. **Obtain or build a HackDucky board.** Clone the repository and send the gerber files in the `production/` folder to a PCB manufacturer, or assemble one using the provided components list.

2. **Flash the RP2040.** Connect the board via USB-C to your computer and hold the BOOTSEL button while connecting. The device will appear as mass storage. Download a compatible firmware (CircuitPython, PicoDucky, or a custom RP2040 image) and drag it to the drive.

3. **Prepare your payloads.** Create DuckyScript files and copy them to a micro SD card formatted as FAT32, or embed payloads directly in the firmware.

4. **Connect and execute.** Use the USB-A port to connect to your target device. The RGB LED provides visual feedback during operation.

### RGB LED Status Reference

| Color | Meaning |
|-------|---------|
| Blue  | Idle / Ready |
| Green | Payload executing |
| Red   | Error or invalid payload |
| Yellow| SD card detected |

## Repository Structure

```
HackDucky/
├── src/           # KiCad schematic, PCB layout, and 3D models
├── production/    # Gerber files and manufacturing assets
├── gallery/       # Device photos and PCB renders
├── firmware/      # Example firmware configurations
├── payloads/      # Sample DuckyScript payloads
└── README.md
```

## PCB Design

The HackDucky schematic and board layout are designed in KiCad and are fully open-source. View the interactive design with the KiCad Web viewer:

https://kicanvas.org/?github=https://github.com/souptik-samanta/Hackducky/tree/main/src

Gerber files in the `production/` directory are ready for manufacturing through any standard PCB service.


## Disclaimer

HackDucky is an educational and open-source hardware project. Users are responsible for complying with all applicable laws and regulations in their jurisdiction when building or using this device. Unauthorized access to computer systems or networks is illegal. This project is intended for legitimate security research, automation testing, and educational purposes only.

## Built with support from

Souptik
Aarav
Some1

Funded by [Hack Club](https://hackclub.com)

## Disclaimer 2

This device is for **educational and ethical purposes only**. Use responsibly. The creators is not responsible for any misuse.

---

## Connect

Built by Souptik Samanta & Arav Jhamb
 

