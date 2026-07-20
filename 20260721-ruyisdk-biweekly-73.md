# RuyiSDK 双周进展汇报 第 073 期·2026 年 07 月 21 日

## 卷首语

## 基础开发环境

### 包管理器

### RuyiSDK VSCode 插件

### RuyiSDK Eclipse 插件

- 项目: 发布 0.1.6 测试版。
- CI: 添加测试版交付流程。
- venv: 在所选工具链不包含 sysroot 时禁用相应的 sysroot 配置选项。
- venv: 调整向导配置页的布局。
- 添加问卷调查弹窗。

### 版本测试及遗留问题

## 基础组件

### 基础C库

### GCC

### LLVM

### V8

### OpenJDK

### Go

提交代码

- 801460: runtime: add msan support for linux/riscv64 | https://go-review.googlesource.com/c/go/+/801460 添加msan支持
- 802100: runtime, internal/fuzz: add libFuzzer support on riscv64 | https://go-review.googlesource.com/c/go/+/802100 添加 fuzz 支持
- 796100: runtime: use sigaction syscalls when cgo is enabled on riscv64 | https://go-review.googlesource.com/c/go/+/796100 cgo 信号支持【合入】

Review
- 801681: runtime, internal/cpu: detect RISC-V vector extension and VLEN | https://go-review.googlesource.com/c/go/+/801681 支持 RISC-V RVV VLEN 长度动态侦测
- 796820: cmd/internal/obj/riscv: document rva23u64 feature macros | https://go-review.googlesource.com/c/go/+/796820 文档支持 【合入】
- 801683: runtime: save RISC-V vector registers state during async preemption | https://go-review.googlesource.com/c/go/+/801683 抢占过程中保存 RVV 寄存器状态 （已经影响部分images/的向量优化）
- 801360: test/codegen: add riscv64 checks for conditional subtractions | https://go-review.googlesource.com/c/go/+/801360 添加codegen 检查（目前 zkt 才有const time能力，大概率拒收）

### QEMU模拟器
