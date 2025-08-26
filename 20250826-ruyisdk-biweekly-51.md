# RuyiSDK 双周进展汇报  第 051 期·2025 年 08 月 26 日

## 卷首语

## 包管理器

## IDE

## GCC

## LLVM

## V8
PLCT提交并合入的代码：

1. **[riscv] Optimize StackPointerGreaterThanOp Compare and Branch**  
   [RISC-V] 优化 StackPointerGreaterThanOp 的比较与分支操作  
   [chromium-review.googlesource.com/c/6862026](https://chromium-review.googlesource.com/c/6862026)
2. **[riscv] Optimize addi and signextend into addiw**  
   [RISC-V] 将 addi（立即数加法）与 signextend（符号扩展）优化合并为 addiw 指令  
   [chromium-review.googlesource.com/c/6861481](https://chromium-review.googlesource.com/c/6861481)
3. **[highway] fix compilation on riscv64**  
   [Highway 库] 修复在 riscv64 架构上的编译问题  
   [chromium-review.googlesource.com/c/6841716](https://chromium-review.googlesource.com/c/6841716)
4. **[riscv][turboshaft] Direct call for known functions**  
   [RISC-V][Turboshaft 编译器优化模块] 对已知函数采用直接调用方式  
   [chromium-review.googlesource.com/c/6838685](https://chromium-review.googlesource.com/c/6838685)

PLCT 审核并合入的代码：

1. **[risc-v] Only save clobbered registers when calling RecordWrite**  
   [RISC-V] 调用 RecordWrite 时仅保存被破坏的寄存器  
   [chromium-review.googlesource.com/c/6873602](https://chromium-review.googlesource.com/c/6873602)
2. **[riscv] Lower maximal code range size on riscv32 (2GB -> 256MB)**  
   [RISC-V] 降低 riscv32 上的最大代码范围大小（从 2GB 调整为 256MB）  
   [chromium-review.googlesource.com/c/6867912](https://chromium-review.googlesource.com/c/6867912)
3. **[riscv][liftoff] Block trampoline pool in OOL stack frame setup**  
   [RISC-V][Liftoff] 在 OOL 栈帧设置中阻塞蹦床池  
   [chromium-review.googlesource.com/c/6859316](https://chromium-review.googlesource.com/c/6859316)
4. **[riscv][wasm] Reverse order of spilled parameters in frame setup**  
   [RISC-V][WebAssembly] 在帧设置中反转溢出参数的顺序  
   [chromium-review.googlesource.com/c/6839045](https://chromium-review.googlesource.com/c/6839045)
5. **[riscv] Allow trampoline blocking to generate code in jump table tests**  
   [RISC-V] 允许蹦床阻塞在跳转表测试中生成代码  
   [chromium-review.googlesource.com/c/6842298](https://chromium-review.googlesource.com/c/6842298)
6. **[riscv] Fix alignment of jump table entries in assembler tests**  
    [RISC-V] 修复汇编测试中跳转表条目的对齐问题  
    [chromium-review.googlesource.com/c/6813493](https://chromium-review.googlesource.com/c/6813493)

## 操作系统支持矩阵

- [OrangePi RV2: Add Debian Trixie test report (basic).](https://github.com/ruyisdk/support-matrix/pull/357)
- [docs: Replace device names with placeholders](https://github.com/ruyisdk/support-matrix/pull/359)
- [docs: Correct sys_ver in LicheePi4A RevyOS README](https://github.com/ruyisdk/support-matrix/pull/360)
- [VF2: fix link typo](https://github.com/ruyisdk/support-matrix/pull/361)
- [Duo: Bump Buildroot to v2.0.1](https://github.com/ruyisdk/support-matrix/pull/363)
- [EIC7700X Board information supplement](https://github.com/ruyisdk/support-matrix/pull/364)
- [Add new boards, support status,test reports,documents and CI updates ](https://github.com/ruyisdk/support-matrix/pull/350)
