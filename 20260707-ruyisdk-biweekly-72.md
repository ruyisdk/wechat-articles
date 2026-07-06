# RuyiSDK 双周进展汇报 第 072 期·2026 年 07 月 07 日

## 卷首语

## 基础开发环境

### 包管理器

### RuyiSDK VSCode 插件

### RuyiSDK Eclipse 插件

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

### V8

### OpenJDK

### Go

### QEMU模拟器
