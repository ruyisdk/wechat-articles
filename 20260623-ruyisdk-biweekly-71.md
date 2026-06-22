# RuyiSDK 双周进展汇报 第 071 期·2026 年 06 月 23 日

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

### OpenJDK

### Go

本期提交主线的CL：

- 790080: cmd/compile: support zba extensions for riscv64 | https://go-review.googlesource.com/c/go/+/790080 添加ZBA SSA 支持
- 789520: cmd/compile: support zbs extensions for riscv64 | https://go-review.googlesource.com/c/go/+/789520 添加ZBS SSA 支持

本期审阅并提出修改意见CL：

- 580276: cmd/compile: support Zba extensions in riscv64 compiler | https://go-review.googlesource.com/c/go/+/580276 沟通后关闭无法进行的CL，移除RVA23合入障碍
- 579797: cmd/compile: support Zbs extensions in riscv64 compiler | https://go-review.googlesource.com/c/go/+/579797 沟通后关闭无法进行的CL，移除RVA23合入障碍
- 616095: test/codegen: add tests for combined shift and zero extension on riscv64 | https://go-review.googlesource.com/c/go/+/616095 添加zero extend 位移测试
- 717980: runtime, cmd/internal/obj/riscv: support spin lock on riscv64 | https://go-review.googlesource.com/c/go/+/717980 要求移除跟随ABIInternal
- 732700: cmd/internal/obj/riscv: add assembly support of Zfa extension | https://go-review.googlesource.com/c/go/+/732700 添加ZFA 支持

### QEMU模拟器
