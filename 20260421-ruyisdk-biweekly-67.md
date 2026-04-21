# RuyiSDK 双周进展汇报 第 067 期·2026 年 04 月 21 日

## 卷首语


## 包管理器


## IDE

### VSCode 插件


### Eclipse 插件

- 程序设计：清理 OSGi 配置文件。
- 程序设计：重新设计异常系统，重写部分错误信息。
- 程序设计：移除冗余封装，整理代码并适度封装逻辑。
- 兼容性：支持 Ruyi 0.47。
- 虚拟环境模块：调整向导页布局使其内容不被遮挡。
- 虚拟环境模块：不再自动更新索引。

## GCC


## LLVM


## V8
本期提交的patch：
1. **[wasm][riscv] Disable partial OOB write optimization for Memory64**
   [WASM][RISC-V] 禁用 Memory64 的部分越界写入优化（https://chromium-review.googlesource.com/c/7733062）
2. **[riscv] Reland [wasm-wide-arith] Turboshaft x64 implementation of wide multiplication ops.**
   [RISC-V] 重新合入「[WASM 大位宽计算] Turboshaft x64 宽乘法指令实现」（https://chromium-review.googlesource.com/c/7722162）
3. **[riscv] Fix sign during Float64Round**
   [RISC-V] 修复 Float64Round 中的符号处理问题（https://chromium-review.googlesource.com/c/7734228）
4. **[riscv] Fix floating-point rounding in RISC-V simulator**
   [RISC-V] 修复 RISC-V 模拟器中的浮点舍入问题（https://chromium-review.googlesource.com/c/7722161）
5. **[riscv][wasm] Fix vector register save/restore order in growable stacks**
   [RISC-V][WASM] 修复可增长栈中向量寄存器的保存/恢复顺序（https://chromium-review.googlesource.com/c/7736871）
6. **[riscv][wasm][wasmfx] Preserve the target arg_buffer.**
   [RISC-V][WASM][WasmFX] 保留目标参数缓冲区 arg_buffer（https://chromium-review.googlesource.com/c/7743620）
7. **[riscv] Fix ToUint8Clamp in Maglev**
   [RISC-V] 修复 Maglev 中 ToUint8Clamp 实现问题（https://chromium-review.googlesource.com/c/7741807）
8. **[riscv] Remove OptimizedWord32Compare optimization**
   [RISC-V] 移除 OptimizedWord32Compare 优化（https://chromium-review.googlesource.com/c/7761051）
9. **[riscv] Modify the conversion of kNearest mode in Round**
   [RISC-V] 调整 Round 指令中 kNearest 模式的转换逻辑（https://chromium-review.googlesource.com/c/7767929）
10. **[riscv][compiler][fastapi] Fix type expectations for uint64 parameters**
    [RISC-V][编译器][Fast API] 修复 uint64 类型参数的类型匹配问题（https://chromium-review.googlesource.com/c/7769991）
11. **[riscv] Disable unaligned access support in V8 RISC-V backend**
    [RISC-V] 在 V8 RISC-V 后端关闭非对齐访问支持（https://chromium-review.googlesource.com/c/7763908）
12. **[riscv][interpreter] Move interrupt budget reduction to function entry**
    [RISC-V][解释器] 将中断预算递减逻辑移至函数入口处（https://chromium-review.googlesource.com/c/7769992）
13. **[wasm-interpreter] Port JSToWasmInterpreterWrapper into torque**
    [WASM 解释器] 将 JSToWasmInterpreterWrapper 迁移至 Torque 实现（https://chromium-review.googlesource.com/c/7455469）
14. **[riscv] Add Zfa extension**
    [RISC-V] 添加 Zfa 浮点扩展指令支持（https://chromium-review.googlesource.com/c/7768270）

本期审阅并合入的patch：
1. **[sandbox] Fix address space limit detection for RISC-V**
    [沙箱] 修复 RISC-V 架构下地址空间上限检测问题（https://chromium-review.googlesource.com/c/7731448）
