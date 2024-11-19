# RuyiSDK双周进展汇报  第033期·2024年11月19日

## 卷首语

## 包管理器

## IDE

## GCC

## LLVM

## V8
1. 适配上游 硬编码实现JumpTableAssembler的 jit 功能。
2. 在 v8 模拟器中实现 js 堆栈切换。
3. 适配turboshaf中word32cmpare的指令选择并修复 turboshaf相关的错误。

## 官网

## 操作系统支持矩阵

- Duo/Duo 256M Alpine, FreeRTOS, openEuler, Fedora, Ubuntu: https://github.com/ruyisdk/support-matrix/pull/99
- Duo Fedora: https://github.com/ruyisdk/support-matrix/pull/100
- Duo OpenWrt/Yocto: https://github.com/ruyisdk/support-matrix/pull/102

丁丑小队本周完成了对 LPi4A & Pioneer Box Firefox 的可用性观测，以及 Milk-V Duo 系列的 RT-Thread / Smart 测试，计划后续一同加入支持矩阵中。

测试报告现已公开。

- Firefox 测试报告：https://github.com/QA-Team-lo/firefox_test
- RT-Thread / Smart 测试报告 Review：https://github.com/QA-Team-lo/rttest

## SDK
完成 Milkv Duo 官方SDK 的验证及缺陷总结，为后续SDK优化做准备。
- [Milkv Duo/Duo 256M/DuoS 缺陷更新](https://gitee.com/yunxiangluo/milkv-duo/blob/master/todo.md)
