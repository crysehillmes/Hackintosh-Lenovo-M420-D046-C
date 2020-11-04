# 联想启天 M420-D046(C) 黑苹果 OpenCore 配置
[英文版](./README.md)

## Repo 资源

- `Codecs` 提取的 ALC235 Codecs 及相关资料.
- `EFI` OC 配置，已清除了 MLB, SN, UUID 需要添加后使用.
- `VBIOS` 用于旌宇 RX560 的 VBIOS, 分为原版和打过 GOP 补丁支持 UEFI 引导的版本.

## 笔记

- [解锁 CFG Lock](/CFGLock.cn.md)

## 硬件:

| 组件      | 型号                                             | 备注    |
| --------- | ------------------------------------------------ | ------- |
| CPU       | Intel i5-8500                                    |         |
| 主板      | B360                                             |         |
| 内存      | DDR4 2666 16G x2                                 |         |
| 显卡      | Intel UHD630 + 旌宇 RX560 4GB 4x mDP 半高        |         |
| WiFi&蓝牙 | BCM943602CS                                      |         |
| 硬盘      | 西数 SN550 1TB                                   |         |


> 1. 如果使用核显 UHD630, 删除 `config.plist` 然后重命名 `config-iGPU.plist` 为 `config.plist`.
> 2. 旌宇 RX560 默认的 VBIOS 不支持 UEFI GOP, 因此在开启 UEFI 时除非系统引导完成，这之前只能看到黑屏. 可以自己给 VBIOS 打 GOP 补丁, 打完后可以正常使用，仅在开机通电或者关机断电的瞬间会花一下，其他时候使用完全正常. 打过补丁的 VBIOS 放在了 `VBIOS` 路径下.


## 功能:
所有功能都能完美正常使用

- [x] 已测试系统版本
  - [x] macOS 11.0.1 Big Sur Beta
  - [x] macOS 11 Big Sur Beta 10
  - [x] macOS 10.15.7 Catalina
  - [x] macOS 10.15.6 Catalina
- [x] CPU
  - [x] 800MHz~4.1GHz 变频
- [x] 显卡
  - [x] Intel UHD630
  - [x] Sparkle RX560
- [x] 声卡
  - [x] ALC235 (`device-id` 为 `10ec0235` 但显示为 ALC233), 我在 AppleALC 里添加了 `layout-id` 35. 
  - [x] UHD630 HDMI 和 RX560 DisplayPort 输出均正常
  - [x] 可以启用 OpenCore 的声音, 按照 OpenCore 教程配置即可, 输出端口为 0,  资源需要自行添加.
- [x] 有线网卡
- [x] WiFi & Bluetooth
  - [x] AirDrop
  - [x] Handoff 接力
  - [x] Sidecar 随航
  - [x] 蓝牙耳机
- [x] USB
  - [x] 所有 USB 端口正确 Map, 支持快充的端口也启用了快充.
- [x] 睡眠 & 唤醒

## 注意:

1. 使用 macOS 11 时需要把 `config.plist` 中的 `SecureBootModel` 设为 `Disabled`.
2. 安装 macOS 11 或者使用 macOS 11 Recovery 时需要设置 `prev-lang:kbd`为 `en-US:0`, 使用 `zh-Hans:252` 会出现灰屏问题. 安装完成后可以改回 `zh-Hans:252`.


## Changelog

- 2020-11-05
  - 升级 OpenCore 0.6.3
  - 添加 NVMeFix
  - 添加 CFGLock 相关
  - 升级 Lilu, WhatEverGreen, AppleALC, VirtualSMC

- 2020-10-28
  - 基于 OpenCore 0.6.2, 所有功能正常
