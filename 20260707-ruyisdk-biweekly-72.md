# RuyiSDK 双周进展汇报 第 072 期·2026 年 07 月 07 日

## 卷首语

## 基础开发环境

### 包管理器

### RuyiSDK VSCode 插件

### RuyiSDK Eclipse 插件

### 版本测试及遗留问题

## 基础组件

### 基础C库

### GCC
- 完成了ruyisdk-gcc 16.1，ruyisdk-binutils 2.46的整合工作，支持多种新扩展及全面的RV Profiles
  - https://github.com/ruyisdk/riscv-gcc
  - https://github.com/ruyisdk/riscv-binutils
- Rebase了Zcmt的Binutils支持，重新设计了link relaxation实现
  - https://sourceware.org/pipermail/binutils/2026-June/149842.html
- 提交了Zama16b和Ziccamoc扩展的支持patch
  - https://sourceware.org/pipermail/binutils/2026-June/149847.html
  - https://sourceware.org/pipermail/binutils/2026-June/149848.html
- 修复了Zvdota扩展的altfmt识别问题，已合入上游
  - https://sourceware.org/git/?p=binutils-gdb.git;a=commit;h=cd28fb866379c5dbbe431feb24aa62d369554f80
- 正在推进P扩展的intrinsic支持更新中
  - https://github.com/ruyisdk/riscv-gcc/pull/12
### LLVM

### V8

本期提交patch如下：
1. **[riscv] sandbox: Replace CPT with TPT**
   [RISC-V][沙箱] 将代码指针表（CPT）替换为可信指针表（TPT）（https://chromium-review.googlesource.com/c/7983344）

2. **[riscv] Add RISC-V ZVFH extension to CPU feature list**
   [RISC-V] 将ZVFH向量半精度浮点扩展添加至CPU特性标识列表（https://chromium-review.googlesource.com/c/7980709）

3. **[riscv][maglev] Sign extend index register in DataView bounds check**
   [RISC-V][Maglev] 在DataView边界校验逻辑中对索引寄存器执行符号扩展（https://chromium-review.googlesource.com/c/7980016）

4. **[Revert "[riscv][maglev] Sign extend index register in DataView bounds check"]**
   [回退提交] 撤销上一条Maglev索引寄存器符号扩展修改（https://chromium-review.googlesource.com/c/7992036）

5. **[Reland [riscv][maglev] Sign extend index register in DataView bounds check]**
   [重提提交] 重新合入Maglev索引寄存器符号扩展修复（https://chromium-review.googlesource.com/c/7992037）

6. **[riscv] Enable ZVFH support for Liftoff WebAssembly SIMD**
   [RISC-V] 为Liftoff WebAssembly SIMD开启ZVFH向量半精度浮点扩展支持（https://chromium-review.googlesource.com/c/7980710）

7. **[riscv][wasm][jspi] Initialize suspend builtin return value**
   [RISC-V][WASM][JSPI] 初始化线程挂起内置函数的返回值（https://chromium-review.googlesource.com/c/8017623）

8. **[riscv]Implement fp16 rounding operations for RISCV**
   [RISC-V] 实现半精度浮点（fp16）舍入运算指令（https://chromium-review.googlesource.com/c/8017624）

9. **[riscv] Unify floating-point rounding ops to support fp16**
   [RISC-V] 统一浮点舍入运算底层逻辑，新增fp16半精度浮点适配（https://chromium-review.googlesource.com/c/8028101）

10. **[riscv][compiler] Scheduler resource allocation table**
    [RISC-V][编译器] 新增指令调度器资源分配表（https://chromium-review.googlesource.com/c/8037086）
### OpenJDK

### Go

### QEMU模拟器
