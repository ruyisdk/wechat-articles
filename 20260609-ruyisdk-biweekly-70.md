# RuyiSDK 双周进展汇报 第 070 期·2026 年 06 月 09 日

## 卷首语

## 基础开发环境

### 包管理器

### RuyiSDK VSCode 插件

### RuyiSDK Eclipse 插件

### 版本测试及遗留问题

## 基础组件

### 基础C库

### GCC

### LLVM

### V8
本期提交并合入的patch：

1. **[riscv]Follow established InstructionCode layout for LoadTrustedPointer**
   [RISC-V] 参照现有指令码格式规范实现 LoadTrustedPointer（https://chromium-review.googlesource.com/c/7870730）

2. **[riscv][wasm] Support FP comparison condition in ArchSelect**
   [RISC-V][WASM] 在 ArchSelect 中支持浮点比较条件（https://chromium-review.googlesource.com/c/7870950）

3. **[riscv]Reland [turboshaft] Introduce MemoryRepresentation for LoadTrustedPointer Port commit 8a885ed63641d4b0bfb4d8d9aaddc21104614b35**
   [RISC-V] 重提「[Turboshaft] 为 LoadTrustedPointer 引入内存表示」，移植对应代码提交（https://chromium-review.googlesource.com/c/7878121）

4. **[riscv] Support i16 in liftoff**
   [RISC-V] 在 Liftoff 中增加 i16 类型支持（https://chromium-review.googlesource.com/c/7882462）

5. **[riscv]Add SmiUntagUnsigned helpers and adjust maglev debug condition**
   [RISC-V] 新增 SmiUntagUnsigned 辅助函数，并调整 Maglev 调试判断逻辑（https://chromium-review.googlesource.com/c/7888915）

6. **[riscv] Use unsigned comparison in JSToWasmWrapperHelper**
   [RISC-V] 在 JSToWasmWrapperHelper 中改用无符号数比较（https://chromium-review.googlesource.com/c/7884915）

7. **[riscv] Disable float16 due to RVV don't support Zvfh now.**
   [RISC-V] 因当前 RVV 暂未支持 Zvfh 扩展，禁用 float16 相关功能（https://chromium-review.googlesource.com/c/7889597）

8. **[riscv][wasmfx] Avoid code cache lookup on suspend**
   [RISC-V][WasmFX] 线程挂起时跳过代码缓存查找操作（https://chromium-review.googlesource.com/c/7901154）

### OpenJDK

### Go

### 模拟器QEMU
