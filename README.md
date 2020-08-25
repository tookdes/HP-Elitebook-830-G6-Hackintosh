# HP Elitebook 830 G6 Hackintosh

![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gi2agfk1frj31hc0u013g.jpg)

OpenCore EFI for HP Elitebook 830-G6 with Catalina(10.15.6)

Clover doesn't boot for some reason.

## Basic Information

- Bios Version: R70 Ver. 01.05.03  04/27/2020 (Can not downgrade anymore so lower Rev. not tested)
- ME Firmware Version: 12.0.64.1551 (Can not disable ME in BIOS but doesn't matter)
- Intel i7-8565U with UHD 620
- 16 GB Hynix/Hyundai 2666MHz DDR4
- Western Digital SN730 NVMe SSD (PM981/PM981a may not supported)
- Broadcom Wi-Fi / BlueTooth Chip BCM94352Z (Aka DW1560, AX200 not supported)

## What Works

- CPU and iGPU
- Speakers /  Headphones output / Mic input (With some noise)
- Trackpad (Keys don't work)
- USB Ports (Including USB-C Port)
- LAN / Ethernet
- Fn keys
- WebCam
- Battery Status (If battery removed the performace will be bad)
- Wi-Fi / Bluetooth (AirDrop Tested)

## To Fix

- Mic (ALC215 Not Supported even with AppleALC 1.5.1 and Layout-ID 18 injected)
- HDMI output
- Hibernation

## Not tested

- Dock
- Thunderbolt 3

## Won't Fix

- Joystick Mouse
- WWAN LTE Module (Fibocomm XMM7276 L830 EB 4G LTE CAT6, recognized, but even not supported in Linux)
- FingerPrint Sensor / TouchID (Not recognized)

## BIOS Settings

- You can enable Fastboot, VTd and VTx

- Disable Legacy boot and Secure boot

- iGPU Memory set to 64MB

## About Sleeping and Hibernation

Sleeping works well but you cannot enable hibernation. It will freeze up when macOS try to hibernate.

You can disable hibernation by follow steps:

```bash
sudo pmset -a hibernatemode 0
sudo rm /var/vm/sleepimage
sudo mkdir /var/vm/sleepimage
sudo pmset -a standby 0
sudo pmset -a autopoweroff 0
```

