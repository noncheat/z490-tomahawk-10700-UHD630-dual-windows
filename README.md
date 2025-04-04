Windows dual macOS

## Specs:
- Mainboard MSI Z490 Tomahawk
  + 1x Realtek® RTL8125B 2.5G LAN
  + 1x Intel I219V 1G LAN
- Cpu Intel® Core™ i7-10700
- Monitor 1 Gigabyte G27Q System > Other Settings > Input Auto Switch: ON
- IGPU Intel UHD 630
  + Mainboard HDMI connect to Monitor 1 HDMI (if want use DisplayPort maybe need frame patch framebuffer-con1 in config.plist? Not test yet)
- Nvidia Galax RTX 2060 12GB
  + DisplayPort connect to Monitor 1 DisplayPort (for FreeSync)
  + HDMI connect to Monitor 2 (Secondary monitor)
- 4 x 16 GB Ram Kingston Fury HyperX DDR4 3200 (XMP)
- SSD Samsung 980 1TB
  + Install Windows
- SSD Samsung 860 EVO 500GB
  + Install macOS
- HDD HGST HTS725050A7E635  OPAL 500GB
- Wifi AX200

## BIOS (version 7C80v1D):
- MSI Fast Boot: Disabled
- Fast Boot: Disabled
- OC > CPU Futures > CFG Lock: Disabled
- OC > CPU Futures > Intel VT-d: Enabled (Optional, DisableIoMapper already enabled)
- Secure Boot: Disabled (After install, recommend sign OpenCore efi to enable Secure Boot for working with Windows)
- Advanced > PCIe > Above 4G memory/Crypto Currency mining: Enabled (Default)
- Advanced > PCIe > ResizebleBar: Enabled (Default)
- Initiate Graphic Adapter = IGD
  + External gpu Nvidia is Windows primary, igpu still working as macOS primary
- Internal Graphics: Enabled
- IGD Multi-Monitor: Enabled
- iGPU Memory: 64MB
- Legacy USB Support: Auto (if Disabled then can't boot from USB)

## Notes
- ~~To switch os, Press F11 at boot to enter Boot Menu, select hard drive, after boot few seconds switch Monitor 1 sources.~~
- Monitor 1 Input Auto Switch: ON so do not need do anything when change OS

## After install:
- Recommend sign OpenCore efi to enable Secure Boot for working with Windows [OpenCore-and-UEFI-Secure-Boot](https://github.com/perez987/OpenCore-and-UEFI-Secure-Boot)

  https://github.com/perez987/OpenCore-and-UEFI-Secure-Boot/blob/main/guide/WSL%20Ubuntu%20VM%20on%20Windows.md

  https://github.com/perez987/OpenCore-and-UEFI-Secure-Boot/blob/main/guide/Insert%20keys%20into%20the%20firmware.md#keytool

  https://archlinux.org/packages/extra/x86_64/efitools/download/

  Copy KeyTool.efi with the name BOOTx64.efi into the EFI folder of the EFI partition of an USB stick formatted as FAT32 and GUID

  the EFI folder on the USB device must also include the files db.auth, kek.auth and pk.auth
- config.plist
  ```
  HideAuxiliary: <true/>
  ScanPolicy: <integer>17760515</integer>
  SecureBootModel: <string>Default</string>
  boot-args: <string>-wegnoegpu</string>
  ```

## When update MacOS:
> If has problems:
- Secure Boot: Disabled
- Initiate Graphic Adapter: IGD
- Boot Order: OpenCore
- SecureBootModel: <string>Disabled</string>
