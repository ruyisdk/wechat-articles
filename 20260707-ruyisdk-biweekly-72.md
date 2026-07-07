# RuyiSDK 双周进展汇报 第 072 期·2026 年 07 月 07 日

## 卷首语

## 基础开发环境

### 包管理器

### RuyiSDK VSCode 插件

### RuyiSDK Eclipse 插件

- 项目: 发布 0.1.5 。
- venv: 支持新的 sysroot 配置方式。
- venv: 根据是否包含 sysroot 筛选列出的工具链。
- venv: 让用户在向导中始终检查虚拟环境文件夹的名称。
- venv: 向项目右键菜单中添加删除 venv 的操作。
- packages: 从树中移除多余的有关包状态的提示内容。

### 版本测试及遗留问题

## 基础组件

### 基础C库

- GLIBC:
  - 实现了 strpbrk 和 strspn 的通用版本 RVV 优化。
  - 在阿里玄铁 C908 平台进一步调优了基于 RVV 和 xthead 标量访问扩展的 memcpy 平台特定优化，并完成了 memset 和 memmove 的初步调优。
- newlib:
  - 先前提交到 newlib 上游的 rawmemchr, memcmp 的通用版本 RVV 优化已合入主线（https://sourceware.org/pipermail/newlib/2026/022437.html）。
  - 移植了 atanh 到当前的 newlib 向量数学库框架。

### GCC

### LLVM
- [compiler-rt][msan] Add MSan support for RISC-V 64-bit Linux | https://github.com/llvm/llvm-project/pull/206674 提供RISC-V msan 功能

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

- 796060: runtime: enable vgetrandom vDSO support for linux/riscv64 | https://go-review.googlesource.com/c/go/+/796060  开启 vdso 提升 crypto 性能
- 796100: runtime: use sigaction syscalls when cgo is enabled on riscv64 | https://go-review.googlesource.com/c/go/+/796100 启动sigaction

### QEMU模拟器
- target/riscv/kvm: skip FP/Vector sync on KVM_PUT_RUNTIME_STATE 减少寄存器同步压力
