# RuyiSDK 双周进展汇报  第 048 期·2025 年 07 月 08 日

## 卷首语

## 包管理器

## IDE
- 实验性新增：添加新的插件projectcreator来为特定的开发板导入示例演示，并自动配置工具链和定制编译配置。提供了新建项目向导，预置开发板项目模板和自定义构建器用于一键在ruyi虚拟环境内构建项目。

## GCC
- 更新了P扩展的Binutils实现，rebase到2.44版本
https://github.com/ruyisdk/riscv-binutils/commits/p-dev/

- Rebase了 0.9.11 版本的P扩展支持到gcc 15.1,正在review中
https://github.com/ruyisdk/riscv-gcc/pull/5

- Porting了RVA23特性到revyos-gcc 14.3
https://github.com/pz9115/revyos-gcc/tree/14.3

## LLVM

- xtheadvector: [Clang][XTHeadVector] implement zvlsseg indexed load/store: https://github.com/ruyisdk/llvm-project/pull/160
- xtheadvector: [Clang][XTHeadVector] make zvlsseg indexed load/store compatible with RVV1.0: https://github.com/ruyisdk/llvm-project/pull/161

## V8
- PLCT合入代码
  - maglev中实现优化 [6656979: [riscv][maglev] Add some peephole optimisations](https://chromium-review.googlesource.com/c/v8/v8/+/6656979)
  - 开启wasm deopt测试用例 [6652018: [riscv][deoptimizer][wasm] Enable wasm deopt tests](https://chromium-review.googlesource.com/c/v8/v8/+/6652018)

- 审阅合入
  - 重构lane-size编码方式，直接在opcode中实现 [6699489: [riscv] Refactor lane-size encoding](https://chromium-review.googlesource.com/c/v8/v8/+/6699489)
  - 正确记录Call函数的pc_offset 
  [6652837: [riscv] Use pc_offset_for_safepoint instead of blocking trampolines](https://chromium-review.googlesource.com/c/v8/v8/+/6652837)

2.3 为了避免DEBUG模式下，向量寄存器检查失败的问题，重构部分向量IR实现方式
6668634: [riscv] Move F32x4 comp functions to code generator | https://chromium-review.googlesource.com/c/v8/v8/+/6668634

## 操作系统支持矩阵

- [Add test for booting from SATA on Megrez](https://github.com/ruyisdk/support-matrix/pull/331)
- [Jupiter/openKylin: Fix wrong `sys_ver`](https://github.com/ruyisdk/support-matrix/pull/337)
- [Duo S: Dump BuildRoot](https://github.com/ruyisdk/support-matrix/pull/339)
- [LiP4A: Fix broken download links](https://github.com/ruyisdk/support-matrix/pull/340)

RuyiSDK GNU 工具链测试（GCC 16）：https://github.com/QA-Team-lo/ruyisdk-gnu-tests
