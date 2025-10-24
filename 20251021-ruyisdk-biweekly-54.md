# RuyiSDK 双周进展汇报  第 054 期·2025 年 10 月 21 日

## 卷首语

## 包管理器

## IDE

## GCC

## LLVM

## V8

## 操作系统支持矩阵

## 版本测试及遗留问题

RuyiSDK 0.42.0 版本已通过[发版测试](https://gitee.com/yunxiangluo/ruyisdk-test/blob/master/20251020/README.md)。该
版本测试是基于 0.42.0-alpha.20251013、 0.42.0-beta.20251015 和 0.42.0-beta.20251017 三个测试版本开展的，预期 0.42.0
 版本将基于 0.42.0-beta.20251017 版本代码发版。下面的表格记录了 0.42.0-beta.20251017 版本新增未修复缺陷：

| 缺陷      | 问题等级 |判定依据 |
| ----------- | ----------- | --- |
| [A large number of old revyos images were deleted #116](https://github.com/ruyisdk/packages-index/issues/116) | 一般 | 软件自带修复功能，预期将在 0.43.0 版本前修复 |

由于 RevyOS 删除大量历史版本镜像，导致 RevyOS 上游、操作系统支持矩阵和 Ruyi 包管理器软件源两两均不对应。
已经确认修复细节，并定于 0.43.0 版本前修复。

同时可以参考下面的表格来跟踪历史遗留问题的修复进度：

| 缺陷      | 问题等级 | 备注 |
| ----------- | ----------- | --- |
| [关于 fastboot 的文档提示 #95](https://github.com/ruyisdk/docs/issues/95)   | 严重 | 建立新的 [issue](https://github.com/ruyisdk/ruyisdk/issues/52) 进行更新，且已拟订相关修复版本号为 0.43.0 版本  |
| [关于使用 pip 安装 ruyi 的文档提示 #96](https://github.com/ruyisdk/docs/issues/96)   | 严重 | 已有文档整体更新计划，已有具体时间节点和时间表安排  |
| [有一部分包无法下载 #37](https://github.com/ruyisdk/packages-index/issues/37)     | 一般 | 已有相关 issue 回复且已经在修复中 |
| [BananaPi BPI-F3 eMMC storage variant did not refer to any combo #101](https://github.com/ruyisdk/packages-index/issues/101)     | 一般 | 软件自带修复功能，且已有相关 issue 回复 |

这些遗留问题并不会影响 Ruyi 包管理器核心功能的实现，但可能影响用户体验，故建议在下载和更新您的 Ruyi 包管理器版本前了
解。其中 packages-index 相关问题将主要影响 ``ruyi device provision`` 功能，请不要使用 ``BananaPi BPI-F3`` 开发板的
 ``BananaPi BPI-F3 (eMMC storage)`` 镜像和 ``Pine64 Star64`` 开发板的 ``Armbian for Pine64 Star64`` 镜像，相关缺陷修
复后可以通过 ``ruyi update`` 解决。
