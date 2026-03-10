# RuyiSDK 双周进展汇报 第 064 期·2026 年 03 月 10 日

## 卷首语

## 包管理器

## IDE

### VSCode 插件

- 多版本管理对不受支持的Ruyi包管理器版本添加outdated标记
- 上架 [Open VSX](https://open-vsx.org/extension/RuyiSDK/ruyisdk-vscode-extension)
- 发布 0.1.2 版本！

### Eclipse 插件

## GCC

## LLVM

## V8
本期亮点：
下文提到的第5项代码提交，将JSToWasmInterpreterWrapper迁移至Torque语言， 统一了V8内置组件的开发范式。这意味着如意V8团队作为RISC-V架构维护者不再仅局限于“适配移植”层面，而是开始深度跟进并参与到V8核心主体功能（WASM解释器核心逻辑）的架构改进与原生实现中，为后续RISC-V架构下V8核心功能的原生优化奠定了基础。

本期提交的patch：
1. **[riscv][sandbox] Fix CrashFilter to detect ASAN shadow memory addresses**  
   [RISC-V][沙箱] 修复 CrashFilter 使其能检测 ASAN 影子内存地址（https://chromium-review.googlesource.com/c/7641970）
2. **[riscv][ic] Introduce homomorphic state for ICs sharing a handler**  
   [RISC-V][内联缓存] 为共享处理程序的内联缓存（IC）引入同态状态（homomorphic state）（https://chromium-review.googlesource.com/c/7623545）
3. **[riscv][jspi] Clear EPT entry on stack return**  
   [RISC-V][JSPI] 在栈返回时清空 EPT（扩展页表）表项（https://chromium-review.googlesource.com/c/7608971）
4. **[riscv][maglev] Handle equal inputs in Float64Max/Min**  
   [RISC-V][Maglev编译器] 处理 Float64Max/Min 操作中输入值相等的场景（https://chromium-review.googlesource.com/c/7599842）
5. **[wasm-interpreter] Port JSToWasmInterpreterWrapper into torque**  
   [WASM解释器] 将 JSToWasmInterpreterWrapper 迁移至 Torque 语言实现（https://chromium-review.googlesource.com/c/v8/v8/+/7455469）
   ### 格式化提交记录
6. **[riscv] Remove kCArgsSlotsSize/kCArgSlotCount**  
   [RISC-V] 移除 kCArgsSlotsSize/kCArgSlotCount 两个常量（https://chromium-review.googlesource.com/c/v8/v8/+/7649603）

## 版本测试及遗留问题
