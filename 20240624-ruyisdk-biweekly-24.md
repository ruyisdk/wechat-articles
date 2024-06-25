# RuyiSDK双周进展汇报  第024期·2024年06月24日

## 卷首语


## 包管理器

RuyiSDK 0.13 对应的包管理器版本也为 0.13.0，已于今日发布。您可移步
[GitHub Releases][ruyi-0.13.0-gh] 或 [ISCAS 镜像源][ruyi-0.13.0-iscas]下载体验。

[ruyi-0.13.0-gh]: https://github.com/ruyisdk/ruyi/releases/tag/0.13.0
[ruyi-0.13.0-iscas]: https://mirror.iscas.ac.cn/ruyisdk/ruyi/releases/0.13.0/

本次 RuyiSDK 包管理器的更新主要包含了以下内容：

* 修复了 [issue #158](https://github.com/ruyisdk/ruyi/issues/158): `coremark` 包的两个版本，解压后的目录布局不统一。现在都会在当前工作目录下“摊开”了。
* 修复了 [issue #159](https://github.com/ruyisdk/ruyi/issues/159): 对“预发布版本”判断方式的不统一。
* 随着 Python 3.12 的正式发布，官方 `ruyi` 二进制也在 Python 3.12 环境构建了。
* 为引入插件架构做好准备：引入了 Starlark 语言支持，并支持在 CI 自动化构建。[Starlark]
  是一种极度简化的 Python 方言，被 Bazel、BUCK 等构建系统广泛采用；这是为了让所有了解
  Python 语言的开发者都可使用熟悉的语法撰写 RuyiSDK 包管理器插件。

[Starlark]: https://github.com/bazelbuild/starlark

为了支持刷写方式复杂、需要夹杂人工干预、镜像文件需要手工下载等复杂情况下的设备初始化，我们正在将设备安装器重构为基于插件架构的形式，预计将于下个版本付诸测试。届时旧版
`ruyi` 的设备安装器功能将不可用，请先升级再进行体验。

欢迎试用或来上游围观；您的需求是我们迭代开发的目标和动力。

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
