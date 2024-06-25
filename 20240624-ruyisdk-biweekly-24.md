# RuyiSDK双周进展汇报  第024期·2024年06月24日

## 卷首语


## 包管理器


## IDE


## GCC
- 发布了新的rv64ilp32 release版本，修复了gdb在rv64ilp32调试时的问题。
- 完成了P扩展在GCC14上的Rebase工作，已合入RUYISDK GCC14分支。
- 添加了Sm/scsrind扩展的支持。
- 正在添加Ssccft/Smcdeleg扩展的支持中。

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
1. Proposed JDK-mainline PRs:
- https://github.com/openjdk/jdk/pull/19448 (8333154: RISC-V: Add support for primitive array C1 clone intrinsic)
- https://github.com/openjdk/jdk/pull/19481 (8333276: RISC-V: client VM build failure after JDK-8241503)
- https://github.com/openjdk/jdk/pull/19564 (8333652: RISC-V: compiler/vectorapi/VectorGatherMaskFoldingTest.java fails when using RVV)
- https://github.com/openjdk/jdk/pull/19473 (8333248: VectorGatherMaskFoldingTest.java failed when maximum vector bits is 64)

2. Reviewed JDK-mainline PRs:
- https://github.com/openjdk/jdk/pull/18226 (8327964: Simplify BigInteger.implMultiplyToLen intrinsic)
- https://github.com/openjdk/jdk/pull/18967 (8330685: ZGC: share barrier spilling logic)
- https://github.com/openjdk/jdk/pull/19026 (8331418: ZGC: generalize barrier liveness logic)
- https://github.com/openjdk/jdk/pull/19011 (8331393: AArch64: u32 _partial_subtype_ctr loaded/stored as 64)
- https://github.com/openjdk/jdk/pull/18919 (8321008: RISC-V: C2 MulAddVS2VI)
- https://github.com/openjdk/jdk/pull/18942 (8326306: RISC-V: Re-structure MASM calls and jumps)
- https://github.com/openjdk/jdk/pull/19246 (8332265: RISC-V: Materialize pointers faster by using a temp register)
- https://github.com/openjdk/jdk/pull/19010 (8331360: RISCV: u32 _partial_subtype_ctr loaded/stored as 64)
- https://github.com/openjdk/jdk/pull/19014 (8331399: RISC-V: Don't us mv instead of la)
- https://github.com/openjdk/jdk/pull/19065 (8320995: RISC-V: C2 PopCountVI)
- https://github.com/openjdk/jdk/pull/19153 (8331577: RISC-V: C2 CountLeadingZerosV)
- https://github.com/openjdk/jdk/pull/19325 (8320999: RISC-V: C2 RotateLeftV)


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
