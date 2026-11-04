# RuyiSDK 双周进展汇报 第 080 期 · 2026 年 11 月 05 日

## 卷首语

>

## 基础开发环境


### 包管理器


### RuyiSDK IDE

- 包索引刷新失败时可展开查看完整错误输出。 
- 新闻刷新复用包索引刷新流程，去除重复实现。 
- 错误信息支持本地化。 
- 统一 Ruyi（命令行工具）与 RuyiSDK（产品/扩展）的术语用法。 

### 版本测试及遗留问题

## 社区与内容建设


### packages-index 资源更新


### 开发板支持矩阵


### 开发板示例仓库


### 官网&文档


## 基础组件


### 基础C库

- GLIBC:
  - 移植了 sinpif, sqrt, sqrtf, tanf 至现有的 glibc libmvec 框架。
- newlib:
  - 移植了 atanhf, atan2f, atanpif, atan2pif, exp2f, cosf, coshf, cospif, exp10f, expf, log2f, log2p1f, rsqrtf, expm1f 至现有的 newlib 向量数学框架。


### GCC

### LLVM

### V8
本期提交并合入的patch如下：
1. **[riscv] Fix RISC-V trusted pointer tag range check**
   [RISC-V] 修复可信指针标签范围检查 [CL8639244](https://chromium-review.googlesource.com/c/8639244)
2. **[riscv] Zero out-of-range trusted pointers on tag underflow**
   [RISC-V] 标签下溢时将越界可信指针置零 [CL8620871](https://chromium-review.googlesource.com/c/8620871)
3. **[riscv][maglev] Store zero-valued constants through the zero register**
   [RISC-V][Maglev] 借助零寄存器保存零值常量 [CL8641030](https://chromium-review.googlesource.com/c/8641030)
4. **[riscv] Derive CPU features from the GN build configuration**
   [RISC-V] 从 GN 编译配置推导 CPU 特性 [CL8641350](https://chromium-review.googlesource.com/c/8641350)
5. **[riscv][maglev] Preserve the NaN sign in Float64->Float32 conversions**
   [RISC-V][Maglev] 在 Float64 转 Float32 时保留 NaN 的符号位 [CL8701858](https://chromium-review.googlesource.com/c/8701858)
6. **[riscv][liftoff] Allocate sub-word atomic RMW temp outside the loop**
   [RISC-V][Liftoff] 在循环外分配子字原子 RMW 临时寄存器 [CL8714199](https://chromium-review.googlesource.com/c/8714199)

本期审阅并合入的patch如下：
1. **[riscv] Fix emit_i32_eqz error**
   [RISC-V] 修复 emit_i32_eqz 错误 [CL8691005](https://chromium-review.googlesource.com/c/8691005)
2. **[riscv] Implement missing RV64 Add643 ops**
   [RISC-V] 实现缺失的 RV64 Add643 运算 [CL8689521](https://chromium-review.googlesource.com/c/8689521)
3. **[riscv] Fix RV64 int32mul typo**
   [RISC-V] 修复 RV64 int32mul 拼写错误 [CL8690428](https://chromium-review.googlesource.com/c/8690428)
4. **[riscv] Emit only ebreak for stop() on hardware**
   [RISC-V] 在硬件上 stop() 仅生成 ebreak 指令 [CL8698658](https://chromium-review.googlesource.com/c/8698658)
5. **[riscv] Preserve vector tails for scalar moves**
   [RISC-V] 标量移动操作时保留向量尾部 [CL8714039](https://chromium-review.googlesource.com/c/8714039)
6. **[riscv] Allow vlen=1024**
   [RISC-V] 支持 VLEN=1024 [CL8585179](https://chromium-review.googlesource.com/c/8585179)

### OpenJDK

### Go

### QEMU


## 项目资源入口

获取更多资讯、下载最新工具、查阅硬件适配资料或参与社区共建，欢迎通过以下官方渠道访问：

- RuyiSDK 官网：[ruyisdk.org](https://ruyisdk.org/)
- RISC-V 开发板与操作系统支持矩阵：[matrix.ruyisdk.org](https://matrix.ruyisdk.org/)
- RISC-V 开发板应用示例库：[boards.ruyisdk.org](https://boards.ruyisdk.org/)
- RuyiSDK 技术社区（交流、投稿、问题反馈）：[ruyisdk.cn](https://ruyisdk.cn/)
- 官方工具下载页面：[ruyisdk.org/downloads](https://ruyisdk.org/downloads)
- RuyiSDK 开源组织仓库：[github.com/ruyisdk/](https://github.com/ruyisdk/)
