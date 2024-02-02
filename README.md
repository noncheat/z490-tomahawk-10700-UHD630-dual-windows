Windows dual macOS, when change os just switch Monitor 1 sources from DisplayPort to HDMI

## Specs:
- Mainboard MSI Z490 Tomahawk
  + 1x Realtek® RTL8125B 2.5G LAN
  + 1x Intel I219V 1G LAN
- Cpu Intel® Core™ i7-10700
- IGPU Intel UHD 630
  + Mainboard HDMI connect to Monitor 1 HDMI (if want use DisplayPort maybe need frame patch framebuffer-con1 in config.plist? Not test yet)
- Nvidia Galax RTX 2060 12GB
  + DisplayPort connect to Monitor 1 DisplayPort (for FreeSync)
  + DVI connect to Monitor 2 (Secondary monitor)
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
- Secure Boot: Disabled (After install, recommend sign OpenCore efi to enable Secure Boot for working with Windows)
- Above 4G memory/Crypto Currency mining: Enabled (Default)
- ResizebleBar: Enabled (Default)
- Initiate Graphic Adapter = FEG (Default)
  + External gpu Nvidia is Windows primary, no need set IGD, igpu still working as macOS primary
- Internal Graphics: Enabled
- IGD Multi-Monitor: Enabled
- iGPU Memory: 64MB
- Legacy USB Support: Auto (if Disabled then can't boot from USB)

## Notes
- To switch os, Press F11 at boot to enter Boot Menu, select hard drive, after boot few seconds switch Monitor 1 sources.

## After install:
- Recommend sign OpenCore efi to enable Secure Boot for working with Windows [OpenCore-and-UEFI-Secure-Boot](https://github.com/perez987/OpenCore-and-UEFI-Secure-Boot)
- config.plist
  ```
  HideAuxiliary: <true/>
  ScanPolicy: <integer>17760515</integer>
  boot-args: <string></string>
  ```