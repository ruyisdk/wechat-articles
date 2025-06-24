# RuyiSDK 双周进展汇报  第 047 期·2025 年 06 月 24 日

## 卷首语

## 包管理器

## IDE

## GCC

## LLVM

- xtheadvector: [Clang][XTHeadVector] fix zvlsseg strided load/store: https://github.com/ruyisdk/llvm-project/pull/158
- xtheadvector: [Clang][XTHeadVector] make zvlsseg compatible with RVV1.0: https://github.com/ruyisdk/llvm-project/pull/159


## V8
- 实现struct/array.atomic.rmw.xchg的原子交换操作 
  - [6633523: [riscv][wasm][shared] Implement struct/array.atomic.rmw.xchg](https://chromium-review.googlesource.com/c/v8/v8/+/6633523)
- 将 suspender 对象迁移到可信空间
  - [6637888: [riscv][wasm][jspi] Move suspender object to trusted space](https://chromium-review.googlesource.com/c/v8/v8/+/6637888)
- 引入简单的截断优化pass
  - [6638821: [riscv][maglev] Simple truncation pass](https://chromium-review.googlesource.com/c/v8/v8/+/6638821)
- 在release模式中在常量池前增加检查
  - [6653368: [riscv] Check trampoline before Constant pool in Release mode](https://chromium-review.googlesource.com/c/v8/v8/+/6653368)
- 避免在JSPI内置函数中进行可信写入
  - [6656978: [riscv] [wasm][sandbox] Avoid a trusted write in a JSPI builtin](https://chromium-review.googlesource.com/c/v8/v8/+/6656978)
- 在Maglev中加入额外的peephole优化
  - [6656979: [riscv][maglev] Add some peephole optimisations](https://chromium-review.googlesource.com/c/v8/v8/+/6656979)

## 操作系统支持矩阵

- [Bit-Brick_K1: add test for bianbu 2.2 minimal](https://github.com/ruyisdk/support-matrix/pull/323)
- [LiP4A: merge 8+32G and 16+128G](https://github.com/ruyisdk/support-matrix/pull/324)
- [LPi4A/RevyOS: Bump to 20250526](https://github.com/ruyisdk/support-matrix/pull/325)
- [LicheePi4A: Add irradium test report (good).](https://github.com/ruyisdk/support-matrix/pull/327)
