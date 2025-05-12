# RuyiSDK 双周进展汇报  第 044 期·2025 年 05 月 13 日

## 卷首语

## 包管理器

## IDE

## GCC
更新了RUYISDK仓库中的gcc版本到gcc16, binutils版本到binutils-2.45。支持了Profiles特性，包括RV20/22/23A|B, 使用-march=Profiles可直接使能Profiles规定的强制支持扩展
支持了`Sha`扩展组合，该扩展为RVA23S64中针对RISC-V虚拟化特性提出的最新扩展组合，用于高效实现虚拟化特性。修复回归测试中发现的gcc错误，限制了错误测试case中
`-mgeneral-regs-only`选项对应的架构范围，已被上游接收

## LLVM

## V8

## 操作系统支持矩阵

## 官网
