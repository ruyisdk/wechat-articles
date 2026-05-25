# RuyiSDK 双周进展汇报 第 069 期·2026 年 05 月 26 日

## 卷首语


## 基础开发环境

### 包管理器

### RuyiSDK VSCode 插件

### RuyiSDK Eclipse 插件


## 编译工具链

### 基础C库

### GCC

### LLVM

- [RISCV] Add support for Ziccid 1.0
https://github.com/llvm/llvm-project/pull/196459 
为 RISC-V 的 Ziccid 1.0 拓展添加支持
已经合并

- [RISCV][MC][NFC] Update IME vtype layout to match latest spec riscv-isa-release-fa55752-2026-05-04
https://github.com/llvm/llvm-project/pull/195998
更新 RISC-V 的 IME vtype 布局以匹配最新的规范
已经合并

- [RISCV][NFC] Rename Zvvmm instruction file to Zvvm
https://github.com/llvm/llvm-project/pull/196692
重命名 RISC-V 的 Zvvmm 指令文件为 Zvvm，以匹配最新的规范
已经合并

- [RISCV][MC] add experimental Zvvfmm MC support
https://github.com/llvm/llvm-project/pull/196486
为 RISC-V 的 Zvvfmm 拓展增加初步的 MC 汇编支持
已经合并

- [RISCV][MC] Add experimental Zvvmtls and Zvvmttls support
https://github.com/llvm/llvm-project/pull/198229
为 RISC-V 的 Zvvfmm、Zvvmtls 和 Zvvmttls 拓展增加初步的 MC 汇编支持
正在 review

- [RISCV][P-ext] Set BITCAST to Custom for 64-bit packed vectors on RV32 /
[RISCV][P-ext] Custom-lower SELECT for v4i16/v8i8 on RV32
https://github.com/llvm/llvm-project/pull/198267
https://github.com/llvm/llvm-project/pull/198723
将 64-bit 的 packed 向量在 RV32 上的 bitcast 设置为 custom 下降，可以解决在 RV32 上一些指令选择不到 p*.d* 这种寄存器对指令的问题。

- Add missing vxsat to PSADDU.B, PSSUB.B/W, and PSSUBU.W. /
Fix PSSHLR.WS left-shift saturation pseudocode. /
Use Sail's <_s/>_s/>_u (with underscore) in pseudocode.
https://github.com/riscv/riscv-p-spec/pull/282
https://github.com/riscv/riscv-p-spec/pull/283
https://github.com/riscv/riscv-p-spec/pull/284
在 RV-32 上 custom 下降 v4i16/v8i8 的 select, 减少指令数


## 语言运行时

### V8

### OpenJDK

### Go


## 版本测试及遗留问题