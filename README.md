# HP Elitebook 830 G6 Hackintosh

OpenCore EFI for HP Elitebook 830-G6.

## Ventura / Sonoma

Please see to:
https://www.tonymacx86.com/members/canuckcam.2601912/

![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gi2agfk1frj31hc0u013g.jpg)

830 G6 is very similar to 840 G6.
You can directly use his work :) Thx to him.

## Catalina (This part is OLD)

### Basic Information

- Bios Version: R70 Ver. 01.05.03  04/27/2020 (Can not downgrade anymore so lower Rev. not tested)
- ME Firmware Version: 12.0.64.1551 (Can not disable ME in BIOS but doesn't matter)
- Intel i7-8565U with UHD 620
- 16 GB Hynix/Hyundai 2666MHz DDR4
- Western Digital SN730 NVMe SSD (PM981/PM981a may not supported)
- Broadcom Wi-Fi / BlueTooth Chip BCM94352Z (Aka DW1560, If you use Intel Wi-Fi please use itlwm.kext)

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

## Not tested

- Dock
- Thunderbolt 3

## Won't Fix

- Joystick Mouse
- WWAN LTE Module (Fibocomm XMM7276 L830 EB 4G LTE CAT6, recognized, but even not supported in Linux)
- FingerPrint Sensor / TouchID (Not recognized)
- Build-in Mic (ALC215 Not Supported even with AppleALC 1.5.1 and Layout-ID 18 injected)
- HDMI output
- Hibernation

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

## About DW1560 in Windows

Your Windows 10 might be frozen after start. Solve it by follow steps:

1. Boot to **safe mode**
2. Go to **power plan settings**
3. Go to the **advanced settings**
4. Got to **PCI Express**
5. Deactivate the **Link State Power Management**

(See to: https://www.tonymacx86.com/threads/bcm94352z-dw1560-causes-windows-10-lockup-freeze.256456/)

If you don't have the driver, go to Dell website, search for "1560", sort by date to get the newest driver (whatever the model is), **extract** it and manually install it by choose .inf file.

For example, right now the newest driver is `M3800_Network_Driver_2JRDK_WN32_7.35.333.0_A01.EXE`. Google it.
