# RuyiSDK双周进展汇报  第026期·2024年07月23日

## 卷首语

## 包管理器

## IDE

## GCC
Gprofng的RISC-V后端支持已被上游合并，将作为binutils 2.43的新特性
更新了P扩展的binutils支持，正在开发P扩展的draft草案支持中

## LLVM

尝试使用该 LLVM 编译器，对 OpenCV 进行交叉编译，发现了如下缺失的 intrinsic，已经修复：

- 支持 Clang 内建函数 vssra/vssrl
- 支持 LLVM 内建函数 vssra/vssrl

## V8

## OpenJDK

## 官网

截止今日 7 月 23 日，订阅人数一共 38 人（增加 1 人）。RuyiSDK 网站访问人数 568 人（增加 62 人），访问页面 2710 次（增加 1286 次）。RuyiSDK 微信交流群 76 人（进群请微信加小助手 ruyisdk_helper）。

Ruyi 包管理器下载量达 7009 次。Youtube 出现 RuyiSDK 俄语视频： [Чё? Прошивать Milk-V Duo S за 2 минуты!
](https://youtu.be/ufkJaEtEi4A?si=JsCAHYT8i-tF3vdN)

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