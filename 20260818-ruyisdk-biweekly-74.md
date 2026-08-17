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

### LLVM

### V8

### OpenJDK

### Go

提交代码

- 664155: cmd/asm, cmd/internal/obj: add crypto algorithm suites for riscv64 | https://go-review.googlesource.com/c/go/+/664155 添加zvk 指令集【合入】
- 796060: runtime: enable vgetrandom vDSO support for linux/riscv64 | https://go-review.googlesource.com/c/go/+/796060 加速crypto库【合入】
- 787960: cmd/compile/internal/ssa: optimize multiply-by-constant on riscv64 | https://go-review.googlesource.com/c/go/+/787960 降低常数乘法强度 【合入】
- 816460: internal/runtime/gc/scan: add RVV impl of filterNil. | https://go-review.googlesource.com/c/go/+/816460 新Greantea GC 添加rvv指令


Review

- 807460: cmd/internal/obj/riscv: compress function returns | https://go-review.googlesource.com/c/go/+/807460 添加C扩展的返回指令，对比原有编译器能减少~2700个指令
- 738760: crypto/internal/poly1305: provide optimised assembly for riscv64 | https://go-review.googlesource.com/c/crypto/+/738760 poly1305添加riscv支持 【合入】
- 808080: runtime: clear frame pointer before calling into C on RISCV64 | https://go-review.googlesource.com/c/go/+/808080 清除帧指针【合入】
- 812961: cmd/asm, cmd/internal/obj: support 6-bit VROR.VI immediates | https://go-review.googlesource.com/c/go/+/812961 支持VRORI 的 6bit编码模式
- 806200: internal/cpu: detect RISC-V VLENB when the vector extension is available | https://go-review.googlesource.com/c/sys/+/806200 添加runtime VLENB
- 815840: runtime: fix sigtramp abi in riscv64 mipsx mips64x and s390x | https://go-review.googlesource.com/c/go/+/815840 修复Go ABI 跳过了sigtramp 的save/restore 【合入】

### QEMU模拟器
