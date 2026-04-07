# RuyiSDK 双周进展汇报 第 066 期·2026 年 04 月 07 日

## 卷首语

## 包管理器

## IDE

### VSCode 插件

### Eclipse 插件

## GCC
更新了P扩展的工具链实现到草案0.20版本,开始进行gcc-precommit-ci的维护工作，更新了zibi扩展的binutils patch.

## LLVM

## V8
本期提交的patch：
1.  **[riscv] Fix SIMD lane load source register**
    [RISC-V] 修复SIMD通道加载的源寄存器问题（https://chromium-review.googlesource.com/c/7695806）
2.  **[riscv][turboshaft] Direct call for known functions**
    [RISC-V][Turboshaft] 对已知函数实现直接调用（https://chromium-review.googlesource.com/c/7695807）
3.  **[riscv] Add simd in LiftoffAssembler::Push/Pop**
    [RISC-V] 在Liftoff汇编器的Push/Pop中增加SIMD支持（https://chromium-review.googlesource.com/c/7695091）
4.  **[riscv][wasm][wasmfx] Implement switch instruction**
    [RISC-V][WASM][WasmFX] 实现switch指令（https://chromium-review.googlesource.com/c/7699360）
5.  **[riscv] Fix build for cross compile**
    [RISC-V] 修复交叉编译构建问题（https://chromium-review.googlesource.com/c/7699576）
6.  **[riscv][base] Refactor EmbeddedVector: decouple from Vector**
    [RISC-V][基础库] 重构EmbeddedVector，使其与Vector解耦（https://chromium-review.googlesource.com/c/7707695）
7.  **[riscv][liftoff] Separate floating-point and simd registers**
    [RISC-V][Liftoff] 分离浮点寄存器与SIMD寄存器（https://chromium-review.googlesource.com/c/7658971）
8.  **[riscv] Fix lmul calculation in SetSimd128Half for VLEN 256/512**
    [RISC-V] 修复VLEN为256/512时SetSimd128Half中的lmul计算问题（https://chromium-review.googlesource.com/c/7676638）
9.  **[riscv] Fix Segment fault in native**
    [RISC-V] 修复原生代码中的段错误（https://chromium-review.googlesource.com/c/7720660）
10. **[riscv] Enable kWord64Select**
    [RISC-V] 启用kWord64Select特性（https://chromium-review.googlesource.com/c/7699088）
11. **[riscv] Fix segment fault in SimulatorTrapHandlerTestWithCodegen.ProbeMemory_MultiStruct**
    [RISC-V] 修复SimulatorTrapHandlerTestWithCodegen.ProbeMemory_MultiStruct测试中的段错误（https://chromium-review.googlesource.com/c/7722697）

## 版本测试及遗留问题

