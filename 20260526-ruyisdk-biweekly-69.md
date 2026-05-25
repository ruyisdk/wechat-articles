# RuyiSDK 双周进展汇报 第 069 期·2026 年 05 月 26 日

## 卷首语


## 基础开发环境

### 包管理器

### RuyiSDK VSCode 插件

- 新增 i18n
- 新增中文翻译
- 为虚拟环境的 sysroot 添加额外包选择框
- 重新设计新闻页面，添加中英文翻译与动画
- 修复一键编译识别 CMake 错误
- 在 ruyisdk home 页面添加 board 文档入口

### RuyiSDK Eclipse 插件

- 包管理器模块：修复设备列表的排序。
- ruyi: 添加必要的环境变量。
- 虚拟环境：支持在“项目”视图中右键项目新建或应用虚拟环境。
- 虚拟环境：在创建时让用户选择已打开的项目而不是输入路径，减少迷惑。
- 虚拟环境：在列表中显示项目名称和虚拟环境的相对路径。
- 项目：发布 v0.1.4。


## 编译工具链

### 基础C库

### GCC
更新GCC版本至gcc16.1, 同步了回归测试中发现的错误，更新了白名单。
更新了P扩展binutils支持，继续更新intrinsic支持中。

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
本期提交并合入的patch：
1. **[riscv][headers] roots-inl.h should not include objects-inl.h**
   [RISC-V][头文件] 修复 roots-inl.h 不应包含 objects-inl.h 的问题（https://chromium-review.googlesource.com/c/7819506）
2. **[riscv][turboshaft][wasm] Decouple SIMD from WebAssembly**
   [RISC-V][Turboshaft][WASM] 将 SIMD 模块与 WebAssembly 解耦（https://chromium-review.googlesource.com/c/7819100）
3. **[riscv][wasm-wide-arith] implement sub128 for Turboshaft**
   [RISC-V][WASM宽算术] 在 Turboshaft 中实现 sub128 指令（https://chromium-review.googlesource.com/c/7830322）
4. **[riscv] Enable zba/zbb/zbs/zicond when enable rva23u64**
   [RISC-V] 启用 rva23u64 时自动开启 zba/zbb/zbs/zicond 扩展（https://chromium-review.googlesource.com/c/7831421）
5. **[riscv] Delete zero_extend after fcvtmod_w_d in TruncateDoubleToInt32**
   [RISC-V] 在 TruncateDoubleToInt32 中移除 fcvtmod_w_d 后的冗余零扩展操作（https://chromium-review.googlesource.com/c/7839765）
6. **[riscv][debugger] Fix a crash when debugging**
   [RISC-V][调试器] 修复调试过程中出现的崩溃问题（https://chromium-review.googlesource.com/c/7846282）
7. **[riscv][wasm-wide-arith] Implement Add128/Sub128 for riscv64**
   [RISC-V][WASM宽算术] 为 riscv64 实现 Add128/Sub128 指令（https://chromium-review.googlesource.com/c/7847572）
8. **[riscv] Detect RVC in cpu-riscv and rename SIMD flag to RVV**
   [RISC-V] 在 cpu-riscv 中增加 RVC 检测，并将 SIMD 标识重命名为 RVV（https://chromium-review.googlesource.com/c/7834018）
9. **[riscv] Fix AtomicCompareExchange write barrier**
   [RISC-V] 修复 AtomicCompareExchange 写屏障问题（https://chromium-review.googlesource.com/c/7858601）
10. **[riscv]Wide multiplication implementation in liftoff**
    [RISC-V] 在 Liftoff 中实现宽乘法指令（https://chromium-review.googlesource.com/c/7862260）
11. **[riscv][wasm][fuzzer] Optimize CheckMaxSteps with platform-specific code**
    [RISC-V][WASM][模糊测试] 使用平台专属代码优化 CheckMaxSteps（https://chromium-review.googlesource.com/c/7862178）
12. **[riscv]Lower LoadTrustedPointer in the code generators**
    [RISC-V] 在代码生成器中实现 LoadTrustedPointer 指令下沉（https://chromium-review.googlesource.com/c/7866844）
13. **[riscv] Fix condition inversion in kArchLoadTrustedPointer**
    [RISC-V] 修复 kArchLoadTrustedPointer 中的条件反转错误（https://chromium-review.googlesource.com/c/7870367）

### OpenJDK

### Go


## 版本测试及遗留问题

RuyiSDK 0.49.0 测试报告尚未发布，只更新部分测试情况。

### 测试套件

本次测试切换到新编写的基于 pytest 的测试套件，更适合 ruyi 项目 CI 集成。

+ 测试套件 <https://github.com/ruyisdk-test/ruyi-pytest>
+ 测试工程 <https://github.com/ruyisdk-test/ruyi-pytest-ci>
+ 测试报告模板 <https://github.com/ruyisdk-test/ruyi-pytest-reports>

### Ruyi 测试

上一版本新增缺陷在本版本均修复。

### RuyiSDK Eclipse IDE 测试

暂无测试情况更新。

### RuyiSDK VSCode IDE 测试

暂无测试情况更新。
