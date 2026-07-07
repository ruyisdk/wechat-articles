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

本期提交 PR 如下：

1. [RISCV][P-ext] Select signed widening add/sub accumulate to wadda/wsuba
https://github.com/llvm/llvm-project/pull/205475
添加 wadda/wsuba 的 codegen 支持
已合并

2. [RISCV][P-ext] Add codegen for packed reduction sum
https://github.com/llvm/llvm-project/pull/206004
添加 packed reduction sum (predsum[u].*)的 codegen 支持
已合并

3. [RISCV][P-ext] Avoid redundant accumulator extend for reduction sum
https://github.com/llvm/llvm-project/pull/206430
优化 reduction sum 生成的多余 sext.w/zext.w 指令
已合并

4. [Clang][RISCV] packed reduction sum intrinsics
https://github.com/llvm/llvm-project/pull/206441
添加 packed reduction sum 的 intrinsic 支持
已合并

5. [RISCV][P-ext] Support Packed Merge.
https://github.com/llvm/llvm-project/pull/207110
添加  Packed Merge 的 intrinsic 支持
已合并

6. [RISCV][P-ext] Use brev8 for bitreverse with Zbkb
https://github.com/llvm/llvm-project/pull/207338
当存在 Zbkb 拓展时将 bitreverse 下降为 brev8 指令，完成 FIXME
已合并

7. [RISCV] Canonicalize the true operand of vselect to fold more vmerge.vvm instructions
https://github.com/llvm/llvm-project/pull/206449
将 vselect 的 true 操作数规范化，以便折叠更多的 vmerge.vvm 指令
已合并

8. [VectorCombine] Use TCK_CodeSize for size-optimized functions
https://github.com/llvm/llvm-project/pull/202207
改进 size-optimized functions 下 VectorCombine 的成本模型选择，使其使用 `TCK_CodeSize`
已合并

9. [VectorCombine] foldShuffleChainsToReduce - add FADD/FMUL handling
https://github.com/llvm/llvm-project/pull/201302
为 `foldShuffleChainsToReduce` 增加 `FADD`/`FMUL` 处理，提升向量归约链折叠能力
已合并

10. [CodeGen] Fix ShrinkWrap crash when FindIDom receives empty predecessor/successor list
https://github.com/llvm/llvm-project/pull/198995
修复 ShrinkWrap 在 `FindIDom` 收到空 predecessor/successor 列表时的崩溃问题
已合并

11. [LV][RISCV] Add crash test for wide pointer stride in convertToStridedAccesses
https://github.com/llvm/llvm-project/pull/200985
为 `convertToStridedAccesses` 中 wide pointer stride 场景补充 RISC-V 崩溃回归测试
已合并

12. [RISCV][P-ext] Support packed reverse intrinsics
https://github.com/llvm/llvm-project/pull/207574
支持 packed reverse intrinsics
正在 review

13. [RISCV][P-ext] Improve codegen for packed reverse intrinsics
https://github.com/llvm/llvm-project/pull/207575
优化  packed reverse intrinsics codegen
正在 review

14. [RISCV][P-ext] Add codegen for packed absolute difference sum
https://github.com/llvm/llvm-project/pull/207314
添加 packed absolute difference sum codegen 支持
正在 review

15. [RISCV][LLVM][Clang] Add experimental Zvvm config intrinsics
https://github.com/llvm/llvm-project/pull/203774
添加 Zvvm config 相关 intrinsics 支持
正在 review，遇到和LLVM上游和RISC-V规范冲突问题，暂时需要等待规范更新


### V8

本期提交patch如下：
1. **[riscv] sandbox: Replace CPT with TPT**
   [RISC-V][沙箱] 将代码指针表（CPT）替换为可信指针表（TPT）（https://chromium-review.googlesource.com/c/7983344）

2. **[riscv] Add RISC-V ZVFH extension to CPU feature list**
   [RISC-V] 将ZVFH向量半精度浮点扩展添加至CPU特性标识列表（https://chromium-review.googlesource.com/c/7980709）

3. **[riscv][maglev] Sign extend index register in DataView bounds check**
   [RISC-V][Maglev] 在DataView边界校验逻辑中对索引寄存器执行符号扩展（https://chromium-review.googlesource.com/c/7980016）

4. **[Revert "[riscv][maglev] Sign extend index register in DataView bounds check"]**
   [回退提交] 撤销上一条Maglev索引寄存器符号扩展修改（https://chromium-review.googlesource.com/c/7992036）

5. **[Reland [riscv][maglev] Sign extend index register in DataView bounds check]**
   [重提提交] 重新合入Maglev索引寄存器符号扩展修复（https://chromium-review.googlesource.com/c/7992037）

6. **[riscv] Enable ZVFH support for Liftoff WebAssembly SIMD**
   [RISC-V] 为Liftoff WebAssembly SIMD开启ZVFH向量半精度浮点扩展支持（https://chromium-review.googlesource.com/c/7980710）

7. **[riscv][wasm][jspi] Initialize suspend builtin return value**
   [RISC-V][WASM][JSPI] 初始化线程挂起内置函数的返回值（https://chromium-review.googlesource.com/c/8017623）

8. **[riscv]Implement fp16 rounding operations for RISCV**
   [RISC-V] 实现半精度浮点（fp16）舍入运算指令（https://chromium-review.googlesource.com/c/8017624）

9. **[riscv] Unify floating-point rounding ops to support fp16**
   [RISC-V] 统一浮点舍入运算底层逻辑，新增fp16半精度浮点适配（https://chromium-review.googlesource.com/c/8028101）

10. **[riscv][compiler] Scheduler resource allocation table**
    [RISC-V][编译器] 新增指令调度器资源分配表（https://chromium-review.googlesource.com/c/8037086）
### OpenJDK

### Go

### QEMU模拟器
