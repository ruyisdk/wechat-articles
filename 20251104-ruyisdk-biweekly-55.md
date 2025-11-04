# RuyiSDK 双周进展汇报 第 055 期·2025 年 11 月 04 日

## 卷首语

## 包管理器

## IDE

## GCC

## LLVM

Upstream:
- [LLDB][Editline] empty current line before el_wgets 
 lldb (https://github.com/llvm/llvm-project/pull/165830)
- [LLDB][DWARF] Use the same qualified name computation for Rust 
 lldb (https://github.com/llvm/llvm-project/pull/165840)

## V8
**提交的patch：**
1. **[riscv] Fix incorrect check supports_wasm_simd_128**  
   [RISC-V] 修复 supports_wasm_simd_128 的错误检查逻辑（https://chromium-review.googlesource.com/c/v8/v8/+/7087478）
2. **[riscv][simulator] Only use read/write mutexes if we're multithreaded**  
   [RISC-V][模拟器] 仅在多线程场景下使用读写互斥锁（https://chromium-review.googlesource.com/c/v8/v8/+/7116238）
3. **[riscv] Fix native build failed**   
   [RISC-V] 修复原生构建失败问题（https://chromium-review.googlesource.com/c/v8/v8/+/7090433）
