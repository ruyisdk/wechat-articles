# RuyiSDK双周进展汇报  第024期·2024年06月24日

## 卷首语


## 包管理器


## IDE


## GCC


## LLVM

修复了如下问题：

- 支持了 `vlmul_trunc` 和 `vlmul_ext` 等 bitcast 操作
- 支持 `vreinterpret` 在向量布尔值和整数之间的转换
- LLVM 对向量 Mask 操作支持使用 `nvx1i1/nvx2i1/nvx4i1` 类型的操作数
- Clang 对向量 Mask 操作支持了 `vbool16/32/64_t` 类型的操作数
- 修复了 `RISCVInsertVSETVLI` 中对 `handleAVLImm` 的处理
- 修复了对 XTHeadVector 中支持的 `VSETIVLI` 指令的模拟的过程


## V8


## OpenJDK


## 官网


## 操作系统支持矩阵

操作系统支持矩阵本次更新：

- Ubuntu
  - Nezha D1: 更新至 24.04 版本
  - Lichee RV D1: 更新至 24.04 版本
- Arch Linux
  -  D1h（新增）

以及最重要的：我们终于有 i18n / 英文翻译啦🎉

共计 448 个文件修改，数十次 Review，这可能是支持矩阵创立以来最大的一次修改，在此感谢各位贡献者的参与~
