# RuyiSDK双周进展汇报  第037期·2025年01月14日

## 卷首语

## 包管理器

## IDE
RuyiSDK IDE V0.0.3 版本发布，下载地址为：https://mirror.iscas.ac.cn/ruyisdk/ide/0.0.3/ 请按照设备环境选择合适的安装包。
V0.0.3 主要修改和更新了 RuyiSDK IDE 的 Welcome 中的 RuyiSDK 相关引导信息，更新为 RuyiSDK 官网和 RuyiSDK IDE 用户指南两部分。

在文档方面，本期重点完成的针对 Milk-V Duo example 示例在 RuyiSDK IDE 中的使用进行说明：
1. 增加了 Run as Remote Application 方式的运行；
2. 增加了 Debug 示例和基于 Terminal 和 Debug as Remote Application 方式调试说明；
3. 进一步明确和优化了编译参数。
4. 整理 milkv duo sdk 改进需求：milkv duo镜像需要增加 sftp-server、gdbserver 程序，方便在开发时进行文件传输和调试支持。

## GCC
更新了Profiles实现规则，在GLIBC中添加了IFUNC符号用于调用，更新了新32位的GDB支持，开始启动GDB SIM的调试工作。

## V8
1. Refactor Relocation支持部分的代码。
2. 修复 strict 模式下的构建错误问题。

## 操作系统支持矩阵

- [Duo/Buildroot: Bump to v1.1.4](https://github.com/ruyisdk/support-matrix/pull/127)
- [CI: Add NixOS and DietPi in system parser matadata](https://github.com/ruyisdk/support-matrix/pull/128)
- [CI: Fix: bump Python version](https://github.com/ruyisdk/support-matrix/pull/130)
- [Licheepi4A/openKylin: Bump version to v2.0-sp1](https://github.com/ruyisdk/support-matrix/pull/131)
- [LicheePi4A/RevyOS(main): update revyos 20241229](https://github.com/ruyisdk/support-matrix/pull/133)
- [LicheePi4A/openKylin: fix broken link](https://github.com/ruyisdk/support-matrix/pull/135)
- [LicheePi 4A/openEuler: Bump version to 24.03 LTS-SP1](https://github.com/ruyisdk/support-matrix/pull/136)
- [LicheePi4A/RevyOS: bump to 20250110](https://github.com/ruyisdk/support-matrix/pull/137)
- [DuoS/Buildroot: Bump version to v2.0.0, change repo url](https://github.com/ruyisdk/support-matrix/pull/138)
