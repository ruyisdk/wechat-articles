# RuyiSDK 双周进展汇报 第 062 期·2026 年 02 月 10 日

## 卷首语

## 包管理器

## IDE

### VSCode 插件

### Eclipse 插件

## GCC

## LLVM

## V8
本期亮点：来自软件所的工程师 wangruikang 解决了node.js长久以来存在的疑难bug（https://ruyisdk.cn/t/topic/403）， patch提交至上游并合入（CL7540554），Node for RISC-V 的稳定性得到提升。
本期提交的patch：
1. **[riscv] Only Enable CheckMemoryAccess in V8_COMPRESS_POINTERS mode**  
   [RISC-V] 仅在 V8_COMPRESS_POINTERS 模式下启用 CheckMemoryAccess 功能（https://chromium-review.googlesource.com/c/7555683）
2. **[riscv] Fix ACCESS BELOW STACK POINTER error**  
   [RISC-V] 修复“访问栈指针下方内存”的错误（https://chromium-review.googlesource.com/c/7550210）
3. **[riscv] Add check stack pointer when access memory**  
   [RISC-V] 新增内存访问时的栈指针检查逻辑（https://chromium-review.googlesource.com/c/7543083）
4. **[riscv][baseline] Inline fast ToBoolean checks for Smis and static roots**  
   [RISC-V][基线编译器] 为 SMI 和 静态根对象 内联快速 ToBoolean 检查逻辑（https://chromium-review.googlesource.com/c/7543084）
5. **[riscv][ic] Introduce CallNamedInterceptorSetter builtin**  
   [RISC-V][内联缓存] 新增 CallNamedInterceptorSetter 内置函数（https://chromium-review.googlesource.com/c/7540545）
6. **[riscv][wasmfx] Implement cont.bind.**  
   [RISC-V][wasmfx] 实现 cont.bind 功能（https://chromium-review.googlesource.com/c/7538513）
7. **[riscv] Skip assembler tests when extension been not supported**  
   [RISC-V] 当扩展未被支持时跳过汇编器测试（https://chromium-review.googlesource.com/c/7533867）
8. **[riscv][wasmfx] Prepare arg buffer for cont.bind**  
   [RISC-V][wasmfx] 为 cont.bind 准备参数缓冲区（https://chromium-review.googlesource.com/c/7533863）
9. **[riscv][cleanup] Use EnumSet<CpuFeature> in multiple places**  
   [RISC-V][代码清理] 更广泛地使用 EnumSet<CpuFeature> 优化代码（https://chromium-review.googlesource.com/c/7529664）
10. **[riscv] Implement word64/word32 Select for Tst/CmpZero operations**  
    [RISC-V] 为 Tst/CmpZero 操作实现 word64/word32 类型的 Select 功能（https://chromium-review.googlesource.com/c/7515447）
11. **[riscv] Fix CWasmEntry uses wrong root register**  
    [RISC-V] 修复 CWasmEntry 误用根寄存器的问题（https://chromium-review.googlesource.com/c/7519177）

本期审核并合入的patch：
1. **[riscv] Fix ISA feature parsing error from /proc/cpuinfo**  
   [RISC-V] 修复从 `/proc/cpuinfo` 文件解析 ISA 特性时的错误（https://chromium-review.googlesource.com/c/7320200）
2. **[riscv] Support fractional LMUL check in simulator**  
   [RISC-V] 在模拟器中支持分数型 LMUL（向量长度乘数）的校验逻辑（https://chromium-review.googlesource.com/c/7531795）
3. **[riscv] Fix sp handling in MacroAssembler::LeaveFrame**  
   [RISC-V] 修复 MacroAssembler::LeaveFrame 方法中栈指针（sp）的处理逻辑问题（https://chromium-review.googlesource.com/c/7540554）
4. **[riscv] Fix illegal instruction caused by unsupported SEW and LMUL configuration**  
   [RISC-V] 修复因不支持的 SEW（向量元素宽度）和 LMUL 配置组合导致的非法指令问题（https://chromium-review.googlesource.com/c/7502635）

## 版本测试及遗留问题
