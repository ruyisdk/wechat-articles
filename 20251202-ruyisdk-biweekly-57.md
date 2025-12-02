# RuyiSDK 双周进展汇报 第 057 期·2025 年 12 月 02 日

## 卷首语

## 包管理器

## IDE

**VSCode 插件：**
 - 重构news、home、packages、telemetry等模块，统一导出风格，改用异步API
 - 新增包搜索、延迟加载、版本支持、多安装管理
 - 修复venv创建激活、新闻页缓存、遥测配置等问题

**Eclipse 插件：**
 - 制定代码风格约束，审查所有代码。
 - 添加“新闻”模块。

## GCC

## LLVM

## V8
本期亮点：Zba扩展的shxadd指令可融合移位与加法，加速RISC-V的地址计算。V8实现了这项优化，结合偏移调整，加载指令数可减半（从4条指令降低为2条）。

本期提交的patch：
1. **[riscv] Encode AccessMode with kMemoryAccessProtectedNullDereference in visitAtomicLoad**  
   [RISC-V] 在visitAtomicLoad中使用kMemoryAccessProtectedNullDereference对AccessMode进行编码（https://chromium-review.googlesource.com/c/7165988）
2. **[riscv] Optimize Word64Add with shxadd instruction on RISC-V**  
   [RISC-V] 在RISC-V架构上通过shxadd指令优化Word64Add操作（https://chromium-review.googlesource.com/c/7155850）
3. **[riscv] Make the index as a immediate whenever possible**  
   [RISC-V] 尽可能将索引处理为立即数（https://chromium-review.googlesource.com/c/7155768）
4. **[riscv][wasmfx] Implement tag parameters and returns**  
   [RISC-V][wasmfx] 实现标签参数与返回值功能（https://chromium-review.googlesource.com/c/7202304）
5. **[riscv][maglev] Fix an issue where SMI values do not overflow correctly**  
   [RISC-V][Maglev] 修复SMI值溢出处理不正确的问题（https://chromium-review.googlesource.com/c/7202584）
6. **[riscv][codegen] Remove IsolateAddressId in favour of IsolateFieldId**  
   [RISC-V][代码生成] 移除IsolateAddressId，改用IsolateFieldId（https://chromium-review.googlesource.com/c/7214846）

审阅的patch：
1. **[riscv] Reset the rounding mode when returning from API**  
   [RISC-V] 从API返回时重置舍入模式（https://chromium-review.googlesource.com/c/6994659）
2. **[riscv] Fix loading of InstanceType in BaselineAssembler**  
   [RISC-V] 修复 BaselineAssembler 中 InstanceType 的加载逻辑问题（https://chromium-review.googlesource.com/c/7190169）
