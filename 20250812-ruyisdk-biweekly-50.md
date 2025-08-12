# RuyiSDK 双周进展汇报  第 050 期·2025 年 08 月 12 日

## 卷首语

## 包管理器

## IDE
为了方便开发协作，RuyiSDK IDE 插件项目（[ruyisdk-eclipse-plugins](https://github.com/ruyisdk/ruyisdk-eclipse-plugins)） 近期进行了一些代码规范化改进，制定了[Java Code 规范指南](https://github.com/ruyisdk/ruyisdk-eclipse-plugins/blob/main/docs/developer/coding-guidelines/index.md)，明确代码样式要求，并对部分代码进行了格式规范化调整。

此外，欢迎对Eclipse插件开发有兴趣的小伙伴加入开发团队，详情参考 [J159 RuyiSDK IDE 开发实习生](https://github.com/lazyparser/weloveinterns/blob/master/open-internships.md) ，期待您的加入。

## GCC

根据社区review建议，修复了部分指令的立即数编码问题，已同步至ruyisdk-binutils仓库

正在实现p扩展的gcc支持，预计本月底完成初步实现

## LLVM

根据社区的建议，在 XTHeadVector 拓展开启时一同开启 zfh 拓展，解决 intrinsic 遇到 float16 无法提升的问题。
- xtheadvector: [LLVM][XTHeadVector] xtheadvector implies zfh by default: https://github.com/ruyisdk/llvm-project/pull/162

## V8
PLCT 提交并合入的代码：

1. **Add Kasper Lund to RISC-V owners list**  
   将 RIVOS 贡献者（V8 创始阶段参与者之一）Kapser 加入 V8 RISCV 后端维护者列表  
   [chromium-review.googlesource.com/c/6826483](https://chromium-review.googlesource.com/c/6826483)

2. **[riscv] Optimize SignExtend Opcode emit**  
   优化 SignExtend 操作码的生成  
   [chromium-review.googlesource.com/c/6774564](https://chromium-review.googlesource.com/c/6774564)

3. **[risc-v] Use sign-extension (via sext.w) to replace slliw when the shift amount is zero**  
   当移位量为零时（即 slliw rd, rs, 0），使用符号扩展（通过 sext.w）替代 slliw，使代码更规范  
   [chromium-review.googlesource.com/c/6726075](https://chromium-review.googlesource.com/c/6726075)

4. **[riscv][wasm][growable-stacks] Record missing safepoint entry**  
   实现 wasm 可增长栈功能，记录缺失的安全点入口  
   [chromium-review.googlesource.com/c/6808523](https://chromium-review.googlesource.com/c/6808523)

5. **[riscv][wasm][jspi][sandbox] Avoid writes to StackMemory from sandboxed code**  
   避免沙箱代码对栈内存进行写入  
   [chromium-review.googlesource.com/c/6808522](https://chromium-review.googlesource.com/c/6808522)

6. **[riscv] Optimize Change [Truncate] and Change [SignExtend] IR emit.**  
   优化 Change [Truncate] 和 Change [SignExtend] 的中间表示（IR）生成  
   [chromium-review.googlesource.com/c/6795158](https://chromium-review.googlesource.com/c/6795158)

7. **[riscv] Optimize emit of sext.w when CompareZero/WordShl/Word32Shr/Word32Sar**  
   在 CompareZero/WordShl/Word32Shr/Word32Sar 时优化 sext.w 的生成  
   [chromium-review.googlesource.com/c/6780050](https://chromium-review.googlesource.com/c/6780050)

PLCT 审核并合入的代码：

1. **[riscv][maglev] Fix compilation**  
   修复 maglev 新特性引起的编译问题  
   [chromium-review.googlesource.com/c/6831542](https://chromium-review.googlesource.com/c/6831542)

2. **[riscv] Handle indirect pointer slots when recording writes**  
   记录写入操作时处理间接指针槽  
   [chromium-review.googlesource.com/c/6818368](https://chromium-review.googlesource.com/c/6818368)

3. **[riscv] Clean up MacroAssembler::StoreReturnAddressAndCall**  
   整理 MacroAssembler::StoreReturnAddressAndCall 方法  
   [chromium-review.googlesource.com/c/6818339](https://chromium-review.googlesource.com/c/6818339)

4. **[riscv] Restore status registers after tests**  
   在测试后恢复状态寄存器  
   [chromium-review.googlesource.com/c/6827265](https://chromium-review.googlesource.com/c/6827265)

5. **[riscv] Fail in the simulator if the vector unit wasn't initialized**  
   若向量单元未初始化则使模拟器运行失败  
   [chromium-review.googlesource.com/c/6826963](https://chromium-review.googlesource.com/c/6826963)

6. **[riscv] Fix load-transforms to setup the vector unit first**  
   修复加载转换以先设置向量单元  
   [chromium-review.googlesource.com/c/6826962](https://chromium-review.googlesource.com/c/6826962)

7. **[riscv] Fix duplicated comment**  
   修复重复的注释  
   [chromium-review.googlesource.com/c/6827141](https://chromium-review.googlesource.com/c/6827141)

8. **[riscv] Implement register constraints for more operations**  
   为更多操作实现寄存器约束  
   [chromium-review.googlesource.com/c/6760111](https://chromium-review.googlesource.com/c/6760111)

9. **[riscv] Don't use kSimd128RegZero in the code-generator**  
   在代码生成器中不使用 kSimd128RegZero，避免当 kSimd128RegZero 未正确初始化时产生错误  
   [chromium-review.googlesource.com/c/6760119](https://chromium-review.googlesource.com/c/6760119)

10. **[riscv] Avoid unnecessary moves**  
    避免不必要的 move 操作  
    [chromium-review.googlesource.com/c/6760118](https://chromium-review.googlesource.com/c/6760118)

11. **[riscv] Use register constraints for I8x16Shuffle**  
    为 I8x16Shuffle 使用寄存器约束  
    [chromium-review.googlesource.com/c/6760117](https://chromium-review.googlesource.com/c/6760117)

12. **[riscv] Avoid temp and unique registers for ExtAddPairwise**  
    为 ExtAddPairwise 避免使用临时和唯一寄存器  
    [chromium-review.googlesource.com/c/6760116](https://chromium-review.googlesource.com/c/6760116)

13. **[riscv] Remove register uniqueness constraints for some instructions**  
    移除部分指令的寄存器唯一性约束  
    [chromium-review.googlesource.com/c/6760115](https://chromium-review.googlesource.com/c/6760115)

14. **[riscv] Avoid unique register in VisitRRIR**  
    在 VisitRRIR 中避免使用唯一寄存器  
    [chromium-review.googlesource.com/c/6760114](https://chromium-review.googlesource.com/c/6760114)

15. **[riscv] Add register constraints**  
    添加寄存器约束，简化 codegen 逻辑  
    [chromium-review.googlesource.com/c/6760110](https://chromium-review.googlesource.com/c/6760110)

16. **[riscv] Move forward declarations of Set {Hi20|Lo12} Offset**  
    移动 Set {Hi20|Lo12} Offset 的前置声明  
    [chromium-review.googlesource.com/c/6760071](https://chromium-review.googlesource.com/c/6760071)

17. **[riscv] Implement register constraints for I32x4DotI8x16I7x16AddS**  
    为 I32x4DotI8x16I7x16AddS 实现寄存器约束  
    [chromium-review.googlesource.com/c/6760113](https://chromium-review.googlesource.com/c/6760113)

18. **[riscv] Implement more register constraints**  
    实现更多 opcode 代码生成的寄存器约束  
    [chromium-review.googlesource.com/c/6760112](https://chromium-review.googlesource.com/c/6760112)


## 操作系统支持矩阵

- 支持矩阵
   - [Dump RT-Thread@DuoS: 5.2.0->5.2.1](https://github.com/ruyisdk/support-matrix/pull/346)
   - [fix dead link for deepin](https://github.com/ruyisdk/support-matrix/pull/347)
   - [metadata: use vendor to mark board manufacturer](https://github.com/ruyisdk/support-matrix/pull/348)
   - [LicheePi4A: Add openEuler RISC-V 24.03 LTS-SP2 test report (good).](https://github.com/ruyisdk/support-matrix/pull/349)
   - [docs(treewide): unify case of distro names & fix typo](https://github.com/ruyisdk/support-matrix/pull/351)
   - [LiP3A: Add irradium test report (good).](https://github.com/ruyisdk/support-matrix/pull/352)
- 前端网站
   - [修复测试报告页面跳转](https://github.com/QA-Team-lo/support-matrix-frontend/commit/0a70f776a25579f6b5e3723516873dd4a626145e)
   - [修复系统表格排版](https://github.com/QA-Team-lo/support-matrix-frontend/commit/a076852f3d21cdd70ef1c3589ee6f0a269a82041)
