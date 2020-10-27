# Hackintosh OpenCore config for Lenovo Qitian M420-D046(C)
[中文版](./README.cn.md)

## Repo Resources

- `Codecs` ALC235 codecs.
- `EFI` OC config, you have to fill your own MLB, SN, UUID.
- `VBIOS` for Sparkle RX560.

## Hardwares:

| Component      | Model                                             | Remarks |
| -------------- | ------------------------------------------------- | ------- |
| CPU            | Intel i5-8500                                     |         |
| Motherboard    | B360                                              |         |
| RAM            | DDR4 2666 16G x2                                  |         |
| Graphics       | Intel UHD630^1^ + Sparkle RX560 4GB LP 4x mDP ^2^ |         |
| WiFi&BlueTooth | BCM943602CS                                       |         |
| Storage        | WD SN550 1TB                                      |         |

> 1. If you only use iGPU, just delete `config.plist` and rename `config-iGPU.plist` to `config.plist`.
> 2. Sparkle RX560 default VBIOS does not support UEFI GOP, so you will only see black screen before OS boot. You can patch VBIOS GOP by yourself and it will work properly(Maybe have glitches when machine poweron or poweroff but no other glitches). You can find patched VBIOS in `VBIOS` folder.


## Features:
Everything is working now. 

- [x] Tested macOS version:
  - [x] macOS 11 Big Sur Beta 10
  - [x] macOS 10.15.7 Catalina
  - [x] macOS 10.15.6 Catalina
- [x] CPU
  - [x] 800MHz~4.1GHz
- [x] Graphics
  - [x] Intel UHD630
  - [x] Sparkle RX560
- [x] Audio
  - [x] ALC235 (device-id is 10ec0235 but display as ALC233) with my custom layout-id 35. 
  - [x] UHD630 HDMI Audio and RX560 DisplayPort Audio
  - [x] You can also enable OpenCore Audio with port `0` (download audio resources by yourself).
- [x] LAN
- [x] WiFi & Bluetooth
  - [x] AirDrop
  - [x] Handoff
  - [x] Sidecar
  - [x] Headphone
- [x] USB
  - [x] All USB port, and enable USB fast charge.
- [x] Sleep & Wake

  
## Note
1. when using macOS 11, you have to set `SecureBootModel` to `Disabled`.


