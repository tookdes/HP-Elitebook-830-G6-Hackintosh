# HP EliteBook 830 G6 Hackintosh (macOS 15 Ready)

OpenCore EFI for HP Elitebook 830 G6, now aligned for macOS 15 (Sequoia) only.

## 目标与范围

- 仅支持 macOS 15（Sequoia）启动与安装。
- 不再维护 Ventura / Sonoma / Catalina 启动兼容说明。
- 采用 OpenCore + 830G6 的 8th Gen Intel 硬件配置：i7-8565U / UHD 620 / BCM94352Z（DW1560）。

## 立即可用（上手步骤）

1. 准备工作
   - BIOS 关闭 `Legacy Boot` 与 `Secure Boot`
   - BIOS 打开 `VT-d`、`VT-x`（按你当前配置需求）
   - 设置 iGPU Memory 至 64MB
2. 写入 EFI
   - 将仓库中的 `EFI` 目录完整复制到启动盘根目录 `EFI` 分区的根路径下（`/Volumes/EFI/EFI`）
   - 注意：根目录应包含 `EFI/BOOT`、`EFI/OC`、`EFI/BOOT/BOOTx64.efi` 与 `EFI/OC/OpenCore.efi` 等文件
3. 插入安装盘（或使用现有 macOS 分区引导）
   - 使用 OpenCore 引导选择 macOS 15 安装项
4. 首次启动完成后
   - 若出现 Wi-Fi 相关问题，检查 `EFI/OC/config.plist` 中 Wi-Fi 项是否保留启用（Sequoia 下已按项目默认启用）
   - 生成唯一的 SMBIOS（不要沿用仓库里的示例序列号，避免苹果服务冲突）

## 当前配置特性（Sequoia）

- 已开启并启用 Broadcom legacy Wi‑Fi 补丁链：
  - `AMFIPass.kext`
  - `IOSkywalkFamily.kext`
  - `IO80211FamilyLegacy.kext`
  - `IO80211FamilyLegacy.kext/Contents/PlugIns/AirPortBrcmNIC.kext`
- `Kernel -> Block` 中保留 `com.apple.iokit.IOSkywalkFamily` 阻断项，限定 macOS 15+
- `NVRAM` boot-args 使用 `-amfipassbeta`

## 来源与取件清单（你要可追溯）

- `AMFIPass.kext`：来自 bluppus20/AMFIPass 官方发布
  - https://github.com/bluppus20/AMFIPass/releases
- OCLP Wi‑Fi 兼容链（`IOSkywalkFamily.kext`、`IO80211FamilyLegacy.kext`）  
  - https://github.com/dortania/OpenCore-Legacy-Patcher/tree/main/payloads/Kexts/Wifi
- 830 G6 机型历史/基础参考（仅用于机型验证与参数对齐）  
  - https://www.tonymacx86.com/members/canuckcam.2601912/

## 机型信息

- BIOS: R70 Ver. 01.05.03（04/27/2020）
- ME Firmware: 12.0.64.1551
- CPU: Intel i7-8565U
- RAM: 16 GB DDR4 2666
- SSD: WD SN730 NVMe（PM981/PM981a 仍建议避开）
- Wi-Fi / Bluetooth: Broadcom BCM94352Z (DW1560)

## 说明

- README 里原有 Ventura / Sonoma / Catalina 历史内容已清理为 Sequoia 专用版本。
- `EFI/SSDT/*.aml` 与 `EFI/OC/ACPI/*.aml` 仍按项目当前配置共同使用。

## 旧版本说明（仅存档）

- 15 以外的系统版本（Ventura/Sonoma/Catalina）不再作为本分支目标，不保证可用。
