# RuyiSDK双周进展汇报  第035期·2024年12月17日

## 卷首语
RuyiSDK包管理器 V0.24 版本已于今日发布。RuyiSDK IDE V0.0.1版本发布，本版本面向RuyiSDK测试人员，提供Linux系统 x86_64、riscv64、aarch64 三架构的安装程序，欢迎下载试用和反馈建议。

RuyiSDK软件源正在新增openjdk、opencv、v8包，同时计划更新gcc、llvm、qemu的版本；构建和发布正在进行中，预计本周内会陆续完成。

GCC向上游重新发送了Profiles支持，目前正在讨论实现的规范细节中，并开始支持Zilsd/Zclsd扩展。v8部分也有较多性能优化、安全性优化相关的更新。

RuyiSDK更多进展细节详见下方详情，欢迎大家试用并提供反馈和建议 ，下一个开发版本 RuyiSDK V0.25 版本将在 12 月 31 日发布。

## 包管理器

## IDE
RuyiSDK IDE V0.0.1版本发布，本版本面向RuyiSDK测试人员，提供Linux系统 x86_64、riscv64、aarch64三架构的安装程序。本版本在Eclipse开源IDE基础上进行定制开发，目前除了继承了项目管理、编辑器、构建、调试等常用功能，能够支持创建、构建、调试 RISC-V 项目等。

RuyiSDK IDE V0.0.1 下载地址为：https://mirror.iscas.ac.cn/ruyisdk/ide/0.0.1/  请按照设备环境选择合适的安装包。

## GCC
向GCC上游重新发送了Profiles支持，目前正在讨论实现的规范细节中，开始支持Zilsd/Zclsd扩展

## V8
1. 移植Growable stack到RISC-V的Wasm liftoff baseline compiler和turbofan compiler
2. 修复ICache flush在多核芯片上的bug，将flush范围从local harts改为包括remo特harts
3. 移植和实现MutableInt32 to ScriptContext slots优化
4. 在正则表达式编译器中添加压栈后栈内存边界检测，加强安全性
5. 继续实现Leap tiering功能

## 操作系统支持矩阵
1. 继续推进 packages-index 元数据同步 CI [#107](https://github.com/ruyisdk/support-matrix/pull/107)
2. 分离 LicheeRV 和 Nezha 测试报告 [#115](https://github.com/ruyisdk/support-matrix/pull/115)
3. 添加 BPI-F3 Alpine 测试报告 [#116](https://github.com/ruyisdk/support-matrix/pull/116)
4. 添加 BeagleV-Ahead RevyOS 和 openSUSE 测试报告 [#117](https://github.com/ruyisdk/support-matrix/pull/117)
5. 添加/更新 LicheeRV Nano Alpine/Buildroot/Fedora 测试报告 [#119](https://github.com/ruyisdk/support-matrix/pull/119)

## SDK

基于之前的验证和测试整理 Milkv Duo 重构需求：

- [Milkv Duo 重构需求](https://gitee.com/yunxiangluo/milkv-duo/blob/master/%E9%87%8D%E6%9E%84%E9%9C%80%E6%B1%82.md)

Milkv Duo SDK todo（缺陷）持续更新：

- [Milkv Duo SDK todo](https://gitee.com/yunxiangluo/milkv-duo/blob/master/todo.md)
