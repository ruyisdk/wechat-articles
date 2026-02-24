# RuyiSDK 双周进展汇报 第 063 期·2026 年 02 月 24 日

## 卷首语

## 包管理器

## IDE

### VSCode 插件

### Eclipse 插件

## GCC
  更新了Binutils模块至2.46版本，Glibc模块至2.43版本，正在修复回归测试中发现的错误。

## LLVM

upstream 进展：

- [RISCV] Add riscv_simd.h for P extension intrinsics https://github.com/llvm/llvm-project/pull/181115

## V8
本期提交的patch：
1. **[riscv][ic] Introduce CallNamedInterceptorGetter builtin**  
   [RISC-V][内联缓存] 新增 CallNamedInterceptorGetter 内置函数（https://chromium-review.googlesource.com/c/7557490）
2. **[riscv][wasm][shared] Add waitqueue type and get/set**  
   [RISC-V][WASM][共享内存] 添加 waitqueue 类型及对应的获取/设置方法（https://chromium-review.googlesource.com/c/7561255）
3. **[riscv] Refactor popcnt implementation in Turbofan**  
   [RISC-V] 重构 Turbofan 编译器中 popcnt（位计数）功能的实现（https://chromium-review.googlesource.com/c/7567282）
4. **[riscv][wasmfx] Implement resume_throw_ref**  
   [RISC-V][wasmfx] 实现 resume_throw_ref 功能（https://chromium-review.googlesource.com/c/7573930）
5. **[riscv] Reland "[wasm][turboshaft] Optimize code generator for unconditional traps"**  
   [RISC-V][wasm][turboshaft] 优化无条件陷阱的代码生成器（https://chromium-review.googlesource.com/c/7599841）
6. **[riscv][wasm] Improve write-barrier treatment**  
   [RISC-V][WASM] 优化写屏障（write-barrier）的处理逻辑（https://chromium-review.googlesource.com/c/7599840）
7. **[riscv][builtins] Fix stack overflow handling in ResumeGeneratorTrampoline**  
   [RISC-V][内置函数] 修复 ResumeGeneratorTrampoline 中栈溢出的处理逻辑（https://chromium-review.googlesource.com/c/7599839）
8. **[riscv] Add WasmCodePointer bounds masking**  
   [RISC-V] 为 WasmCodePointer 添加边界掩码（bounds masking）机制（https://chromium-review.googlesource.com/c/7566742）

## 版本测试及遗留问题
