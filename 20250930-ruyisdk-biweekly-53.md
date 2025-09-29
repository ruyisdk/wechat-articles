# RuyiSDK 双周进展汇报  第 053 期·2025 年 09 月 30 日

## 卷首语

## 包管理器

## IDE

## GCC

## LLVM

upstream:
- [[LLDB] Fix GetIndexOfChildMemberWithName to handle anonymous struct in base classes](https://github.com/llvm/llvm-project/pull/158256)

xtheadvector:
- [[LLVM][XTHeadVector] fix vwcvt, vwcvtu](https://github.com/ruyisdk/llvm-project/pull/163)

## V8
**PLCT提交并合入的patch：**
1. **[riscv] Fix SimdCrossCompilerDeterminismTest.TestTernOp failed.**  
   [RISC-V] 修复 SimdCrossCompilerDeterminismTest.TestTernOp 测试失败问题  
   [chromium-review.googlesource.com/c/6965545](https://chromium-review.googlesource.com/c/6965545)
2. **[riscv] Add Extension Zimop**  
   [RISC-V] 添加 Zimop 扩展  
   [chromium-review.googlesource.com/c/6955146](https://chromium-review.googlesource.com/c/6955146)
3. **[riscv] Fix build for v8_enable_external_code_space**  
   [RISC-V] 修复 v8_enable_external_code_space 的构建问题  
   [chromium-review.googlesource.com/c/6934203](https://chromium-review.googlesource.com/c/6934203)
4. **[riscv][wasmfx][jspi] Allow JSPI to suspend multiple stacks at once**  
   [RISC-V][wasmfx][JSPI] 允许 JSPI 同时挂起多个栈  
   [chromium-review.googlesource.com/c/6937846](https://chromium-review.googlesource.com/c/6937846)
5. **[riscv] Fix custom-descriptors-inlining.js failed**  
   [RISC-V] 修复 custom-descriptors-inlining.js 执行失败问题  
   [chromium-review.googlesource.com/c/6928701](https://chromium-review.googlesource.com/c/6928701)
**审阅并合入的patch：**
1. **[riscv] Only compile vlen intrinsic for RVV targets**  
   [RISC-V] 仅为 RVV 目标编译 vlen 内在函数  
   [chromium-review.googlesource.com/c/6959231](https://chromium-review.googlesource.com/c/6959231)
2. **[riscv] Fix IsNodeUnsigned bug**  
   [RISC-V] 修复 IsNodeUnsigned 函数的漏洞  
   [chromium-review.googlesource.com/c/6958729](https://chromium-review.googlesource.com/c/6958729)
3. **[riscv] Support architectures with 256-bit vector units**  
   [RISC-V] 支持带有 256 位向量单元的架构  
   [chromium-review.googlesource.com/c/6948289](https://chromium-review.googlesource.com/c/6948289)
4. **[riscv] Replace more auipc+jalr into addi+jal**  
   [RISC-V] 将更多 auipc+jalr 指令组合替换为 addi+jal  
   [chromium-review.googlesource.com/c/6874383](https://chromium-review.googlesource.com/c/6874383)
5. **[riscv] Refactor WASM Simd128 operations**  
   [RISC-V] 重构 WebAssembly 的 Simd128 操作  
   [chromium-review.googlesource.com/c/6948067](https://chromium-review.googlesource.com/c/6948067)
6. **[riscv] Add more checks in IsNodeUnsigned to eliminate slli instructions**  
   [RISC-V] 在 IsNodeUnsigned 中添加更多检查以消除 slli 指令  
   [chromium-review.googlesource.com/c/6933681](https://chromium-review.googlesource.com/c/6933681)
7. **[riscv] Fix compilation error and disassembling error when enabling the RISC-V C extension**  
   [RISC-V] 修复启用 RISC-V C 扩展时的编译错误和反汇编错误  
   [chromium-review.googlesource.com/c/6934163](https://chromium-review.googlesource.com/c/6934163)

## 操作系统支持矩阵

- [Mars: debian: add trixie (mainline version)](https://github.com/ruyisdk/support-matrix/pull/367)
- [Add Tizen](https://github.com/ruyisdk/support-matrix/pull/368)
- [Bit-Brick_K1,LicheePi4A@OpenKylin 2.0 SP2](https://github.com/ruyisdk/support-matrix/pull/369)
- [Test LicheePi4A/Tizen](https://github.com/ruyisdk/support-matrix/pull/370)
- [Update mangopi_mq](https://github.com/ruyisdk/support-matrix/pull/371)
- [test LicheePi3A: Bianbu Desktop/Desktop Lite](https://github.com/ruyisdk/support-matrix/pull/372)
- Opennovation.org 工程软件在 RISC-V 上的测试验证：https://github.com/QA-Team-lo/engineering-riscv

## 版本测试及遗留问题
