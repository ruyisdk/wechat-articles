# RuyiSDK双周进展汇报  第028期·2024年09月03日

## 卷首语

## 包管理器

## IDE

本期暂无进展。

## GCC

- 支持了Zimop扩展
- 修复了部分回归测试中发现的错误

## LLVM

- 支持了对 tuple type 的 vget/vset/vcreate 操作。
- 修复在指定 XTHeadVector 拓展时，编译器未定义 `__riscv_vector` 的问题，现在编译器行为与 GCC 一致。

## V8

1. 提交patch，使V8 for Android RISCV64在 NDK r27 版本获得标准构建支持（无需在手工配置NDK toolchain）。
2. 继续实现TurboShaft SIMD IR 到RVV的指令选择。
3. 移植central stack switches特性。

## 官网

截止今日9月3日，RuyiSDK 网站访问人数986人，新增152人，访问页面7622次，新增2755次。RuyiSDK 微信交流群132人，新增49人（进群请加微信小助手 ruyisdk_helper）。

官网新增 algolia search，现在可以搜索网站上的任何内容啦！

[RuyiSDK 亮相 elexcon 2024深圳国际电子展](https://mp.weixin.qq.com/s/Rr04my4SxRPfTT7-wvKriw)

## 操作系统支持矩阵
