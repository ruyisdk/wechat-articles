# RuyiSDK 双周进展汇报 第 072 期·2026 年 07 月 07 日

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
- [compiler-rt][msan] Add MSan support for RISC-V 64-bit Linux | https://github.com/llvm/llvm-project/pull/206674 提供RISC-V msan 功能

### V8

### OpenJDK

### Go

- 796060: runtime: enable vgetrandom vDSO support for linux/riscv64 | https://go-review.googlesource.com/c/go/+/796060  开启 vdso 提升 crypto 性能
- 796100: runtime: use sigaction syscalls when cgo is enabled on riscv64 | https://go-review.googlesource.com/c/go/+/796100 启动sigaction

### QEMU模拟器
- target/riscv/kvm: skip FP/Vector sync on KVM_PUT_RUNTIME_STATE 减少寄存器同步压力
