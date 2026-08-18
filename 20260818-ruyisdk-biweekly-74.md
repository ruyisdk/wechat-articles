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

本期提交 PR 如下

- [RISCV][P-ext] Support Packed Narrowing Clip Pair
 https://github.com/llvm/llvm-project/pull/215779
 补齐 P 扩展 Packed Narrowing Clip Pair，覆盖 Clang、LLVM IR、RISC-V 后端选择及 RV32/RV64 测试。已合并

- [Clang][RISCV] Add packed sign and zero extend intrinsics
 https://github.com/llvm/llvm-project/pull/211487
 增加 packed sign/zero extend（psext/pzext）的 Clang 内建函数、头文件封装及代码生成测试。已合并

- [RISCV][P-ext] Select scalar mulhr/mulhru/mulhrsu for RV32 v2i32
 https://github.com/llvm/llvm-project/pull/215938
 修复 RV32 v2i32 舍入高位乘法选择，将运算拆分为 mulhr、mulhru、mulhrsu 标量指令。已合并

- [RISCV][P-ext] Support Packed Multiply High
 https://github.com/llvm/llvm-project/pull/211223
 增加 P 扩展 Packed Multiply High 的 Clang 内建函数、LLVM IR 和代码生成支持，覆盖 RV32/RV64。已合并

- [RISCV][MC] Add experimental Smcsps and Sscsps support
 https://github.com/llvm/llvm-project/pull/211712
 增加 Smcsps 和 Sscsps 拓展的汇编支持。已合并


### V8

### OpenJDK

本期审阅并合入的JDK主线patch:

- https://github.com/openjdk/jdk/pull/31340 (8385702: Improve polymorphic handling in JDK-8385648)  为各CPU平台优化polymorphic相关处理的指令跳转逻辑
- https://github.com/openjdk/jdk/pull/31358 (8384442: Shenandoah: Remove vestigial CAS barrier code)  为各CPU平台清理ShenandoahGC未使用的CAS barrier函数
- https://github.com/openjdk/jdk/pull/31373 (8385915: RISC-V: Remove unused cmpxchg* methods)  为RISC-V平台清理未使用的cmpxchg汇编函数
- https://github.com/openjdk/jdk/pull/31423 (8386161: RISC-V: Auto-enable Zvkn/Zvkg extension features)  为RISC-V平台自动开启Zvkn/Zvkg探测和加解密指令运用（SpaceMit K3平台加解密操作性能实测2-3倍性能加速）
- https://github.com/openjdk/jdk/pull/31434 (8386252: Shenandoah: Polish LRB argument preparation)  为各CPU平台优化LRB参数准备
- https://github.com/openjdk/jdk/pull/31424 (8385323: Support capstone on riscv64)  支持配置构建面向RISC-V平台的capstone反汇编器so文件

Java重要新特性JEP 401: 值类与对象（Value Classes and Objects）的调研和移植工作进展：
已完成RISC-V平台Java虚拟机的模板解释器、C1、C2 JIT即时编译器三大模块对JEP 401特性的兼容性支持，能够在Server模式下跑通JEP 401相关兼容性测试用例。
同时，JVM相关修改可在RISC-V平台全量通过JDK自带全部回归测试用例。JEP 401兼容性相关工作已经通过PR形式提交到Valhalla代码仓，详细修改见PR链接。
下一步工作：
继续调研JEP 401 Value Class相关的性能优化实现细节，具体包括值类型Flattening支持（UseArrayFlattening & UseFieldFlattening）和方法调用值类型参数传递内联支持（InlineTypePassFieldsAsArgs & InlineTypeReturnedAsFields）。

- https://github.com/openjdk/valhalla/pull/2531 (8386240: [lworld] Port JEP 401 to RISC-V)

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
- 812961: cmd/asm, cmd/internal/obj: support 6-bit VROR.VI immediates | https://go-review.googlesource.com/c/go/+/812961 支持VROR.VI 的 6-bit编码模式
- 806200: internal/cpu: detect RISC-V VLENB when the vector extension is available | https://go-review.googlesource.com/c/sys/+/806200 添加runtime VLENB
- 815840: runtime: fix sigtramp abi in riscv64 mipsx mips64x and s390x | https://go-review.googlesource.com/c/go/+/815840 修复Go ABI 跳过了sigtramp 的save/restore 【合入】

### QEMU模拟器
