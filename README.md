##1. Overview
This repository contains the firmware for the bee venom collector devices
It Supports Firmware Over The Air (FOTA) updates allowing devices to be updated after deployment without physical access.


##2. Hardware Platform
- ESP WROOM-32 (Espressif ESP32 Dev Module)
- Freq: 240MHz
- RAM: 320KB
- Flash: 4MB
- Power: External regulated supply
- Output: Controlling simulation stage (handled by HW safety limits)

##3. Developmernt Enviroment
-IDE: Visual Studio Code.
-Build System: PlatformIO
-Framework: Arduino
Toolchain:Espressif32

##4. Firmware Architecture
Bootloader
├── Application (Running Firmware)
├── OTA Slot A
├── OTA Slot B
├── NVS (Configuration & Version Info)


##5. FOTA Update Flow
1. Device powered up.
2. Device try to Connect to Wifi.
3. If Connected, check FOTA updates.
4. Device downloads latest firmware.bin
5. Writes to inactive OTA partition
6. Reboots and switches partition
7. Rollback if boot fail.



##6. Versioning Strategy.
vMAJOR.MINOR.PATCH
MAJOR -> Incompatable changes/ partition layout
MINOR -> New features
PATCH -> Bug fixes/ Stablitiy improvements.
Example:
v1.2.1


## 7. Critical safety Rules
 **VERY IMPORTANT – DO NOT IGNORE**

- OTA updates **must never** disable or bypass hardware safety limits
- OTA must always support **rollback**
- Do NOT change stimulation parameters remotely without validation
- Failed OTA update must **never brick the device**
- Always test OTA on real hardware before release




