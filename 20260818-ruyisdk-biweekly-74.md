# RuyiSDK 双周进展汇报 第 074 期·2026 年 08 月 18 日

## 卷首语

## 基础开发环境

### 包管理器

### RuyiSDK VSCode 插件

### RuyiSDK Eclipse 插件

- venv & UX: 解决进入虚拟环境向导时的性能问题。
- UX: 整理程序各处的文本以统一命名风格。
- venv: 修改虚拟环境向导的部分设计，使线程间数据流向清晰。

### 版本测试及遗留问题

## 基础组件

### 基础C库

### GCC
1. 推进 RISC-V SIMD 扩展工具链落地

本周继续推进 SIMD 扩展在 GNU 工具链中的支持，更新了汇编、反汇编相关实现；同时与 SiFive 合作，进一步完善 intrinsics 功能支持和验证。目前工作正在从基础指令支持向编译器接口和完整工具链支持推进。同时继续担任 RISC-V P Extension Task Group Vice-Chair，参与后续规范、工具链及生态协同工作。

- https://github.com/riscv/riscv-p-spec/pull/322
- https://lists.riscv.org/g/tech-p-ext/message/1031

2. 参与 RISC-V Binutils 上游维护

协助审核 Alibaba 提交的 dtrel 符号解析相关 patch，并推动其合入上游。除了自身功能开发之外，继续承担 RISC-V Binutils 社区的 patch review 和上游维护工作。

- https://sourceware.org/git/?p=binutils-gdb.git;a=commit;h=4e8ba93fdb24f9bcf31f706e62e67c57ae91168f

3. 维护 RISE Toolchain CI 基础设施

持续维护 RISE Toolchain CI，支撑 RISC-V GCC/Binutils 上游开发和回归验证。后续会继续结合实际运行情况完善 CI 稳定性和问题跟踪。

- https://github.com/riseproject-dev/gcc-postcommit-ci/pull/3

### LLVM

### V8

### OpenJDK

### Go

### QEMU模拟器
