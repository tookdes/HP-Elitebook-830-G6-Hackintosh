# HP Elitebook 830 G6 Hackintosh

OpenCore EFI for HP Elitebook 830-G6 with Catalina(10.15.6)

Clover doesn't boot for some reason.

## Basic Information

- Bios: 01.05.03 Rev.A (Can not downgrade anymore so lower Rev. not tested)
- Intel i7-8565U with UHD 620
- Western Digital SN730 NVMe SSD
- Broadcom Wi-Fi / BlueTooth Chip BCM94352Z (DW1560)

## What Works

- CPU and iGPU
- Speakers /  Headphones output / Mic input (With some noise)
- Trackpad (Keys don't work)
- USB Ports (Including USB-C Port)
- LAN/Ethernet
- Fn keys
- WebCam
- Battery Status (If battery removed the performace will be bad)
- Sleep / Wake-up
- Wi-Fi / Bluetooth

## To Fix

- Mic (ALC215 Not Supported even with AppleALC 1.5.1 and Layout-ID 18 injected)
- HDMI output

## Not tested

- Dock
- Thunderbolt 3

## Won't Fix

- Joystick Mouse
- WWAN LTE Module
- FingerPrint Sensor / TouchID
