# RuyiSDK双周进展汇报  第032期·2024年11月05日

## 卷首语

## 包管理器

## IDE
从零开始开发VSCode插件与Ruyi IDE插件 第3课已经上线B站。视频可以在[此](https://www.bilibili.com/video/BV1dxSXYzE6L/?share_source=copy_web&vd_source=ec7b3fbeca3203e5c990a2be1cbdeb2e)观看。欢迎点赞关注一键三连！

Eclipse插件部分完成了基于 eclipse-embed-cdt [eclipse-plugins](https://github.com/eclipse-embed-cdt/eclipse-plugins) 开发环境的搭建。

## GCC
继续推进P扩展在binutils上的草案支持，尝试更新新32位在glibc上的支持工作

## LLVM
本期暂无ruyisdk相关更新。

## V8
1. 修复和完善TurboShaft IR、Maglev JIT 的RISC-V架构相关部分。
2. 继续移植LeapTiering特性。
3. 实现wasm JSPI特性。

## 官网

## 操作系统支持矩阵

本期支持矩阵有大量更新，包括：测试报告元数据、首页表格 CI、issue 模板、测试报告更新等等。

<details>
<summary> 点击展开 </summary>

- CI Table gen [PR #49](https://github.com/ruyisdk/support-matrix/pull/49)
- VisionFive2/Ubuntu Ubuntu 24.10 & Ubuntu 24.04.1 LTS [PR #50](https://github.com/ruyisdk/support-matrix/pull/50)
- VisionFive2/Openkylin Openkylin 2.0，VisionFive2/Alpine [PR #51](https://github.com/ruyisdk/support-matrix/pull/51)
- PIC64GX/Ubuntu Ubuntu 24.10 [PR #52](https://github.com/ruyisdk/support-matrix/pull/52)
- CI Push Error fix [PR #53](https://github.com/ruyisdk/support-matrix/pull/53)
- BPI-F3 Bianbu v2.0：[PR #54](https://github.com/ruyisdk/support-matrix/pull/54)
- NeZha-D1s/Ubuntu: update test report for Ubuntu 24.10 and Ubuntu 24.04.1 LTS [PR #55](https://github.com/ruyisdk/support-matrix/pull/55)
- Metadata: Refactor and add sys variant [PR #56](https://github.com/ruyisdk/support-matrix/pull/56)
- VisionFive/Alpine: add test report, VisionFive2/Alpine: fix typo [PR #57](https://github.com/ruyisdk/support-matrix/pull/57)
- Icicle/Ubuntu: update test report for Ubuntu 24.10 and Ubuntu 24.04.1 LTS：[PR #58](https://github.com/ruyisdk/support-matrix/pull/58)
- Mars/Ubuntu: update test report for Ubuntu 24.10 and Ubuntu 24.04.1 LTS：[PR #59](https://github.com/ruyisdk/support-matrix/pull/59)
- Unmatched/Ubuntu: update test report for Ubuntu 24.10 and Ubuntu 24.04.1 LTS：[PR #60](https://github.com/ruyisdk/support-matrix/pull/60)
- D1_LicheeRV/Ubuntu: update test report for Ubuntu 24.10 and Ubuntu 24.04.1 LTS：[PR #61](https://github.com/ruyisdk/support-matrix/pull/61)
- LPi4a: Update RevyOS to 20240720：[PR #62](https://github.com/ruyisdk/support-matrix/pull/62)
- LPi4a/openKylin: Update to 2.0：[PR #63](https://github.com/ruyisdk/support-matrix/pull/63)
- CI: Modify table to pages：[PR #64](https://github.com/ruyisdk/support-matrix/pull/64)
- README: Remove all svgs and use pages from ci：[PR #65](https://github.com/ruyisdk/support-matrix/pull/65)
- VisionFive2/Archlinux: update archlinux to cwt23：[PR #66](https://github.com/ruyisdk/support-matrix/pull/66)
- VisionFive2/DietPi: add test report：[PR #67](https://github.com/ruyisdk/support-matrix/pull/67)
- VisionFive2/openSUSE: update openSUSE test report：[PR #68](https://github.com/ruyisdk/support-matrix/pull/68)
- PIC64GX/Ubuntu: fix typo：[PR #69](https://github.com/ruyisdk/support-matrix/pull/69)
- duo: Add uniproton basic support：[PR #70](https://github.com/ruyisdk/support-matrix/pull/70)
- README: Add desc for tools：[PR #71](https://github.com/ruyisdk/support-matrix/pull/71)
- CI: Tables gen CI redesign：[PR #72](https://github.com/ruyisdk/support-matrix/pull/72)
- Template: Add new templates：[PR #74](https://github.com/ruyisdk/support-matrix/pull/74)
- CI: Add debug mode and pr target：[PR #76](https://github.com/ruyisdk/support-matrix/pull/76)
- Metadata: fix and tweaks：[PR #89](https://github.com/ruyisdk/support-matrix/pull/89)
- BPI-F3: Added Fedora test report：[PR #90](https://github.com/ruyisdk/support-matrix/pull/90)
- duo256m/openeuler: Add openEuler support for duo256：[PR #91](https://github.com/ruyisdk/support-matrix/pull/91)
- BPI-F3: Added OpenWrt test report：[PR #93](https://github.com/ruyisdk/support-matrix/pull/93)
- Metadata: sync metadata and test report：[PR #94](https://github.com/ruyisdk/support-matrix/pull/94)
- LPi4a/deepin: Update to 20240815 [PR #95](https://github.com/ruyisdk/support-matrix/pull/95)
- Metadata: Add multi-language support [PR #96](https://github.com/ruyisdk/support-matrix/pull/96)
- Duo/BuildRoot: Update to v1.1.3 [PR #98](https://github.com/ruyisdk/support-matrix/pull/98)
</details>