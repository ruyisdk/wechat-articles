# RuyiSDK 双周进展汇报  第 046 期·2025 年 06 月 10 日

## 卷首语

## 包管理器

## IDE

## GCC
添加香山昆明湖CPU到gcc RISC-V后端，目前已合入gcc上游，添加时补充了一系列gcc缺失的特权模式扩展指令集。
修复了binutils中smnrmi缺失zicsr依赖的问题。

## LLVM

## V8
1.  在turbofan RISC-V后端中支持非经典NAN
    - [6621983: [riscv] Implement non-canonical NaNs fadds in turbofan](https://chromium-review.googlesource.com/c/v8/v8/+/6621983)
    - [6616397: [riscv][turboshaft] Propagate non-canonical NaNs](https://chromium-review.googlesource.com/c/v8/v8/+/6616397)
2.  在wasm的liftoff编译器RISC-V后端中支持代码覆盖统计
    - [6621984: [riscv][wasm] Wasm code coverage: Support Liftoff](https://chromium-review.googlesource.com/c/v8/v8/+/6621984)
3.  在RISC-V架构上实现JS undefined value的floating nan boxing
    - [6622041: [riscv][maglev][turboshaft] Fix more issues with HoleyFloat64 conversions](https://chromium-review.googlesource.com/c/v8/v8/+/6622041)
4.  指令选择优化compare zero
    - [6605164: [riscv] Optimize Comparezero](https://chromium-review.googlesource.com/c/v8/v8/+/6605164)
5.  调整maglev中临时寄存器分配作用域，使临时寄存器能尽快被使用
    - [6588676: [riscv] Adjust TemporaryRegisterScope to release kMaglevFlagsRegister quickly](https://chromium-review.googlesource.com/c/v8/v8/+/6588676)
6.  审阅并合入syntacore的针对jalr和jal指令的RAS特性所做的优化
    - [6562942: [riscv] improve calls/jumps to avoid RAS pollution](https://chromium-review.googlesource.com/c/v8/v8/+/6562942)
7.  审阅并合入syntacore的代码生成优化
    - [6593511: [riscv][maglev] Improve StringCharCodeOrCodePointAt to use sh1add instruction on Zba hardware](https://chromium-review.googlesource.com/c/v8/v8/+/6593511)
8.  修复指针压缩模式下对tagged smi的加减法溢出处理
    - [6605718: [riscv] Fix add/sub overflow failed in pointer compression mode](https://chromium-review.googlesource.com/c/v8/v8/+/6605718)
9.  实现优化JITed代码中的diapatch handle正确性保证代码
    - [6596491: [riscv][sandbox] Make sure we have a valid dispatch handle in optimized code](https://chromium-review.googlesource.com/c/v8/v8/+/6596491)
10. 删除InstructionSelectorAdapter，为删除turbofan的SON IR，全面使用turboshaft IR做好准备，
    - [6596249: [riscv][turbofan] Remove InstructionSelectorAdapter](https://chromium-review.googlesource.com/c/v8/v8/+/6596249)


## 操作系统支持矩阵

## 官网
