# RuyiSDK 双周进展汇报 第 059 期·2025 年 12 月 30 日

## 卷首语

## 包管理器

## IDE

**VSCode 插件：**

**Eclipse 插件：**

## GCC

## LLLVM

## V8
本期提交的patch：
1. **[riscv] Enable CanUseGenericJsToWasmWrapper** [RISCV] 启用 GenericJsToWasmWrapper 功能，节省Wasm Import function的调用开销（https://chromium-review.googlesource.com/c/7268664） 
2. **[riscv][heap] Make read-only MemoryChunk field conditionally optional** [RISCV][堆内存] 使能只读 MemoryChunk 字段的可选配置（https://chromium-review.googlesource.com/c/7271945） 
3. **[riscv] Skip message/wasm-debug-trace-minimal** [RISCV] 跳过 message/wasm-debug-trace-minimal 测试用例（https://chromium-review.googlesource.com/c/7274736） 
4. **[riscv64] Protect return addresses stored on stack.** [RISCV64] 保护存储在栈上的返回地址（https://chromium-review.googlesource.com/c/7039660）
5. **[riscv] Implement FP16 in simulator** [RISCV] 在模拟器中实现FP16（半精度浮点）功能（https://chromium-review.googlesource.com/c/7266607） 
6. **[riscv] Fix build failed on v8_unittests** [RISCV] 修复 v8_unittests 构建失败的问题（https://chromium-review.googlesource.com/c/7304885） 
7. **[Turbofan] optimize ChangeUint32ToUint64(BitcastFloat32ToUint32)** [Turbofan编译器] 优化 ChangeUint32ToUint64(BitcastFloat32ToUint32) 操作（https://chromium-review.googlesource.com/c/7271804） 
8. **[riscv][builtins] Refactor CallApiGetter builtin** [RISCV][内置函数] 重构 CallApiGetter 内置函数（https://chromium-review.googlesource.com/c/7274581）

本期审阅的patch：
1. **[maglev] Do not use condition flags on loong64 and riscv64** [Maglev编译器] 取消loong64和riscv64架构条件标志位在IR上的使用（https://chromium-review.googlesource.com/c/7273937）
