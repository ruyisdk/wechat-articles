# RuyiSDK双周进展汇报  第026期·2024年07月23日

## 卷首语

## 包管理器

## IDE

## GCC

## LLVM

尝试使用该 LLVM 编译器，对 OpenCV 进行交叉编译，发现了如下缺失的 intrinsic，已经修复：

- 支持 Clang 内建函数 vssra/vssrl
- 支持 LLVM 内建函数 vssra/vssrl

## V8

## OpenJDK

## 官网

## 操作系统支持矩阵

本期更新：

- Deepin RISC-V
    - StarFive VisionFive
    - StarFive VisionFive 2
    - Sipeed Lichee Pi 4A
- openKylin RISC-V 2.0 RC
    - StarFive VisionFive 2
- Bianbu
    - Milk-V Jupiter (CFT)
- Debian
    - Milk-V Duo S 更新至最新版 v1.4.0
- 一些小的 Typo Fix

内容请详见：[ruyisdk/support-matrix](https://github.com/ruyisdk/support-matrix)