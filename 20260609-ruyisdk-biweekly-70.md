# RuyiSDK 双周进展汇报 第 070 期·2026 年 06 月 09 日

## 卷首语

## 基础开发环境

### 包管理器

### RuyiSDK VSCode 插件

### RuyiSDK Eclipse 插件

### 版本测试及遗留问题

## 基础组件

### 基础C库
- GLIBC:
   - 实现了 rawmemchr, strcasecmp 和 mempcpy 的通用版本 RVV 优化。
   - 先前提交到 GLIBC 上游的 memccpy, memchr, memcmp, strchr, ctrrchr 的通用版本 RVV 优化已合入主线（https://patchwork.sourceware.org/project/glibc/list/?series=57340&state=*）。
- newlib:
   - 先前提交到 newlib 上游的 mempcpy, memrchr, memchr, memccpy 的通用版本 RVV 优化已合入主线（https://sourceware.org/pipermail/newlib/2026/022437.html）。
   - 先前提交到 newlib 上游的 rawmemchr, memcmp 接口的通用版本 RVV 优化，reviewer 提出了修改意见，已完成相关修正。
   - 移植了 acosh 到当前的 newlib 向量数学库框架。

### GCC

### LLVM

### V8

### OpenJDK

### Go

### 模拟器QEMU
