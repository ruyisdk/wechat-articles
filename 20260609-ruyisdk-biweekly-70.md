# RuyiSDK 双周进展汇报 第 070 期·2026 年 06 月 09 日

## 卷首语

## 基础开发环境

### 包管理器

### RuyiSDK VSCode 插件

### RuyiSDK Eclipse 插件

- ruyi: 修复有关 RuyiSDK 元数据更新结果的判断逻辑与提示信息。
- ruyi: 修复和简化对已安装 ruyi 包管理器的检查逻辑。
- 界面: 添加有关 ruyi 包管理器版本更新的提示信息。
- 界面: 调整各视图在 Eclipse IDE C/C++ 布局下的初始位置，调整 RuyiSDK.cn 网站视图的启动方式。
- 界面: 整理菜单并对各条目妥善分组。

### 版本测试及遗留问题

## 基础组件

### 基础C库
- GLIBC:
   - 实现了 rawmemchr, strcasecmp 和 mempcpy 的通用版本 RVV 优化。
   - 先前提交到 GLIBC 上游的 memccpy, memchr, memcmp, strchr, strrchr 的通用版本 RVV 优化已合入主线（https://patchwork.sourceware.org/project/glibc/list/?series=57340&state=*）。
- newlib:
   - 先前提交到 newlib 上游的 mempcpy, memrchr, memchr, memccpy 的通用版本 RVV 优化已合入主线（https://sourceware.org/pipermail/newlib/2026/022437.html）。
   - 先前提交到 newlib 上游的 rawmemchr, memcmp 接口的通用版本 RVV 优化，reviewer 提出了修改意见，已完成相关修正。
   - 移植了 acosh 到当前的 newlib 向量数学库框架。

### GCC
- 分析了 bne/beq immediate 支持，完成了Zibi扩展的GCC实现
- 基于 riscv-isa-manual PR #2369，在Ruyisdk GCC / Binutils工具链上支持Zvbc32e / Zvkgs草案
- 完成特权指令扩展Smmtt的第一子扩展Smsdid支持，已更新至Ruyisdk Binutils，正在实现第二子扩展Smmpt部分

### LLVM

- [RISCV][MC] Support experimental Zvdota Family instructions
https://github.com/llvm/llvm-project/pull/195069 已合并

- [RISCV][P-ext] Split v4i16/v8i8 MUL on RV32.
https://github.com/llvm/llvm-project/pull/199504
在 RV32 上拆分 64-bit 向量 v4i16/v8i8 的乘法（按寄存器对拆成两半计算）。
已合并

- [RISCV][P-ext] Fold bitcast of v4i8/v2i16 const splat to scalar on RV64
https://github.com/llvm/llvm-project/pull/199513
在 RV64 上把 v4i8/v2i16 常量 splat 的 bitcast 折叠为标量常量。

- [RISCV][P-ext] Split v4i16/v8i8 INSERT/EXTRACT_VECTOR_ELT on RV32.
https://github.com/llvm/llvm-project/pull/199917
在 RV32 上拆分 64-bit 向量 v4i16/v8i8 的元素插入/提取（INSERT/EXTRACT_VECTOR_ELT）。

- [RISCV][P-ext] packed shift-add codegen
https://github.com/llvm/llvm-project/pull/201294
实现 P 扩展 packed shift-add codegen。

- [RISCV][P-ext] Select scalar asub/asubu and mulhr/mulhru/mulhrsu on RV32
https://github.com/llvm/llvm-project/pull/201540
在 RV32 上为标量 asub/asubu 与 mulhr/mulhru/mulhrsu 指令添加指令选择。

- Fix RV32 instruction sequence for exchanged add/sub i32x2 intrinsics
https://github.com/riscv/riscv-p-spec/pull/293
修正 i32x2 交换式加减（p*_x 系列 intrinsic） intrinsic 文档中的 RV32 指令序列。

- RV32 fallback: scalar instructions for 64-bit packed multiply intrinsics
https://github.com/riscv/riscv-p-spec/pull/295
把 64-bit packed multiply intrinsic 在 RV32 上回退改为正确的标量 .h 指令

- RV32 fallback: widening wmul/wmacc for 64-bit multiply-parts intrinsics
https://github.com/riscv/riscv-p-spec/pull/296
把返回 int64 的 multiply-parts intrinsic 在 RV32 上回退改为单条加宽指令 wmul/wmacc

- Fix typos in 64-bit Q-format multiply-accumulate intrinsics
https://github.com/riscv/riscv-p-spec/pull/297
修正 64 位 Q-format 乘累加 intrinsic 的 typo



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

本期审阅并合入的JDK主线patch:
- https://github.com/openjdk/jdk/pull/30562 (8381611: RISC-V: Factor out function cmpptr from MacroAssembler)  为RISC-V汇编器重构代码，移除非必要的cmpptr汇编函数，改善代码可读性
- https://github.com/openjdk/jdk/pull/30598 (8381724: RISC-V: Pass temp registers and use them in CardTableBarrierSetAssembler::store_check())  为RISC-V汇编函数store_check传递额外的临时寄存器
- https://github.com/openjdk/jdk/pull/30491 (8380163: Fix implicit conversion in macroAssembler_aarch64.hpp)  为ARM64修复一处隐式数据类型转换潜在风险
- https://github.com/openjdk/jdk/pull/30616 (8381677: Remove dependence of UseSHA on UseSHAIntrinsics)  为各CPU后端清理UseSHA / UseSHAIntrinsics选项设置
- https://github.com/openjdk/jdk/pull/30646 (8381926: Fix implicit conversion in macroAssembler_riscv.hpp)  为RISC-V修复一处隐式数据类型转换潜在风险

Java重要新特性JEP 401: 值类与对象（Value Classes and Objects）的调研和移植工作进展：
通过阅读JEP 401规范文档和调试对比X86/ARM64相关代码，已初步了解该特性的设计思路，并开始着手实现CPU平台一侧代码的解耦。
目前已完成模板解释器模块的代码解耦，并能够构建支持解释执行模式RISC-V JDK二进制，下一步考虑C1& C2 JIT模块的代码解耦。
详细修改见如下链接：
- https://github.com/openjdk/valhalla/commit/dd306a5978bb081e842a607b175d9cda7bff1b7f
- https://github.com/openjdk/valhalla/commit/519e69b4882121823d5b66ce1da496d74c1989d5
- https://github.com/openjdk/valhalla/commit/d1d65189cae1a40b16a8f4136a42147271180459
- https://github.com/openjdk/valhalla/commit/ef493a94d3706fa5a8dcafe587b5f6a5616a74bc
- https://github.com/openjdk/valhalla/commit/1a32a6e292f8efa4ae79ac352684ee5b3027c305

### Go

本期提交主线的CL：
- 788080: cmd/compile/internal/ssa: limit zbb to rva22u64 for riscv64 | https://go-review.googlesource.com/c/go/+/788080 修复原有ZBB 优化无视profile
- 787960: cmd/compile/internal/ssa: optimize multiply-by-constant on riscv64 | https://go-review.googlesource.com/c/go/+/787960 通过ZBB 优化常数乘法
- 787280: test/codegen: add riscv64 check for divmod | https://go-review.googlesource.com/c/go/+/787280 添加divmod的代码生成检查

本期审阅并提出修改意见CL：
- 781080: cmd/compile/internal: add intrinsic rule for sync atomic and/or 32/64 on RISCV64 | https://go-review.googlesource.com/c/go/+/781080 添加atomic32/64操作支持
- 738760: crypto/internal/poly1305: provide optimised assembly for riscv64 | https://go-review.googlesource.com/c/crypto/+/738760 优化poly1305标量汇编实现
- 787420: runtime: check RISC-V ISA profile at runtime init | https://go-review.googlesource.com/c/go/+/787420 runtime时期检查profile
- 787401: internal/bytealg: improve Count/CountString for riscv64 | https://go-review.googlesource.com/c/go/+/787401 优化标量count实现

### 模拟器QEMU
