# RuyiSDK 双周进展汇报 第 078 期 · 2026 年 10 月 13 日

## 卷首语

>

## 基础开发环境


### 包管理器


### RuyiSDK IDE

### 版本测试及遗留问题

## 社区与内容建设


### packages-index 资源更新


### 开发板支持矩阵


### 开发板示例仓库


### 官网&文档


## 基础组件


### 基础C库

- GLIBC:
  - 移植了 powf, sincos, sincosf, sincospi, sincospif, sinf 至现有的 glibc libmvec 框架。
- newlib:
  - 移植了 hypot, log10, log1p, sincospi, sinpi, tanpi 至现有的 newlib 向量数学框架。

### GCC

### LLVM

### V8
本期我们开始在实际硬件平台上开展基于Node.js的RVV的Wasm SIMD功能/性能测试，并在一开始就发现旧版内核不提供hwprobe，导致V8 runtime无法正确获取运行时指令集特征的问题。这类问题是在仅基于V8的开发和测试中无法发现的，接下来适配会进一步推进。

本期提交并合入的patch：
1. **[riscv] Fix CompareTaggedAndBranch with relocatable immediates**
   [RISC-V] 修复带可重定位立即数的 CompareTaggedAndBranch [CL8436921](https://chromium-review.googlesource.com/c/8436921)
2. **[riscv][maglev] Zero-extend string index before address computation**
   [RISC-V][Maglev] 在地址计算前对字符串索引做零扩展 [CL8438659](https://chromium-review.googlesource.com/c/8438659)
3. **[riscv][wasm] Fix OOL spill space size in RecordSpillsInSafepoint**
   [RISC-V][WASM] 修复 RecordSpillsInSafepoint 中Out-Of-Line代码区段溢出空间大小 [CL8436642](https://chromium-review.googlesource.com/c/8436642)
4. **[riscv] Fix zero-extension of BitcastFloat32ToWord32 in ChangeUint32ToUint64**
   [RISC-V] 修复 ChangeUint32ToUint64 中 BitcastFloat32ToWord32 的零扩展 [CL8461522](https://chromium-review.googlesource.com/c/8461522)
5. **[riscv][wasm]Patch jump table slots atomically**
   [RISC-V][WASM] 原子方式修补跳转表槽位 [CL8483311](https://chromium-review.googlesource.com/c/8483311)
6. **[riscv][sandbox] Tag entries in the TrustedPointerTable**
   [RISC-V][Sandbox] 为可信指针表中的条目添加标记 [CL5373845](https://chromium-review.googlesource.com/c/5373845)
7. **[riscv][maglev] Avoid clobbering allocatable register t4 in ByteSwap**
   [RISC-V][Maglev] 在 ByteSwap 中避免覆盖可分配寄存器 t4 [CL8492392](https://chromium-review.googlesource.com/c/8492392)
8. **[riscv][wasm] Zero upper lanes in v128.load{32,64}_zero**
   [RISC-V][WASM] 在 v128.load{32,64}_zero 中将高位通道置零 [CL8485765](https://chromium-review.googlesource.com/c/8485765)
9. **[riscv][wasm] Fix growable stacks return trampoline frame teardown**
   [RISC-V][WASM] 修复可增长栈返回跳板帧的销毁逻辑 [CL8535227](https://chromium-review.googlesource.com/c/8535227)
10. **[riscv][wasm] Add preemptive stack checks to generic JS-to-Wasm wrapper**
    [RISC-V][WASM] 在通用 JS-to-Wasm 包装器中增加抢占式栈检查 [CL8536826](https://chromium-review.googlesource.com/c/8536826)
11. **[riscv][compiler] Simplify AssembleConstructFrame**
    [RISC-V][编译器] 简化 AssembleConstructFrame 实现 [CL8535328](https://chromium-review.googlesource.com/c/8535328)
12. **[riscv][compiler] Add stack check to compiled JS-to-Wasm wrappers**
    [RISC-V][编译器] 在编译后的 JS-to-Wasm 包装器中添加栈检查 [CL8535329](https://chromium-review.googlesource.com/c/8535329)
13. **[riscv] Implement and correctly round FP16 RVV fused multiply-add**
    [RISC-V] 实现 FP16 RVV 融合乘加并正确处理舍入 [CL8544731](https://chromium-review.googlesource.com/c/8544731)

本期审阅并合入的patch：
1. **[riscv] Fall back to /proc/cpuinfo when riscv_hwprobe is unavailable**
   [RISC-V] riscv_hwprobe 不可用时回退读取 /proc/cpuinfo [CL8473041](https://chromium-review.googlesource.com/c/8473041)

### OpenJDK

### Go

### QEMU

## 社区动态


---

## 项目资源入口

获取更多资讯、下载最新工具、查阅硬件适配资料或参与社区共建，欢迎通过以下官方渠道访问：

- RuyiSDK 官网：[ruyisdk.org](https://ruyisdk.org/)
- RISC-V 开发板与操作系统支持矩阵：[matrix.ruyisdk.org](https://matrix.ruyisdk.org/)
- RISC-V 开发板应用示例库：[boards.ruyisdk.org](https://boards.ruyisdk.org/)
- RuyiSDK 技术社区（交流、投稿、问题反馈）：[ruyisdk.cn](https://ruyisdk.cn/)
- 官方工具下载页面：[ruyisdk.org/downloads](https://ruyisdk.org/downloads)
- RuyiSDK 开源组织仓库：[github.com/ruyisdk/](https://github.com/ruyisdk/)
