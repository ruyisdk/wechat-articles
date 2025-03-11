# RuyiSDK 双周进展汇报  第 040 期·2025 年 03 月 11 日

## 卷首语

## 包管理器

## IDE

## GCC
- 更新了p扩展寄存器对指令的工具链支持，正在实现RVA23S的有关特权指令扩展中。

## LLVM

- 在 19.1.6 版本中修复了 Greedy Register Allocator 在某些 XTHeadVector intrinsic 上导致的编译器内部错误的问题
- 在 17.1.6 版本中新增部分 XTHeadVector intrinsic 的操作数范围检查，和 RVV 1.0 行为对齐

## V8
- 在陆续添加TurborShaft IR支持后，删除TurboFan SON IR相关的旧代码
- 审核类型转换优化、32bit比较优化patch（来自syntacore）
- 实现Wasm JSPI功能中沙盒内的chain of stacks功能
- 删除RISCV指令集不支持的ByteSwap 代码生成支持

## 操作系统支持矩阵

- [Add a new RTOS: LiteOS and add LiteOS test report for CH32V307](https://github.com/ruyisdk/support-matrix/pull/175)
- [BIT-BRICK K1:add new board  ](https://github.com/ruyisdk/support-matrix/pull/176)
- [LicheePi4A: update to fedora 41](https://github.com/ruyisdk/support-matrix/pull/178)
- [BPI-F3: Update Bianbu v2.0.4 to v2.1](https://github.com/ruyisdk/support-matrix/pull/179)
- [feat/tools: split customized linux distributions](https://github.com/ruyisdk/support-matrix/pull/180)
- [LicheePi4A/RevyOS: Remove ruyi-install version](https://github.com/ruyisdk/support-matrix/pull/181)
- [VisionFive2: add eweOS,update openkylin 2.0 SP1](https://github.com/ruyisdk/support-matrix/pull/182)
- [feat/tools: remove customized distributions from linux table](https://github.com/ruyisdk/support-matrix/pull/183)
- [Pioneer: Bump a bunch of reports](https://github.com/ruyisdk/support-matrix/pull/184)
- [LicheeRV & Duo & Duo256m & VisionFive2/nixos: fix typo](https://github.com/ruyisdk/support-matrix/pull/185)
- [Fix: make `sys` field case insensitive](https://github.com/ruyisdk/support-matrix/pull/186)
- [Add LiteOS test report for CH32V208, update documents and fix some typos.](https://github.com/ruyisdk/support-matrix/pull/187)
- [Add/Update mangopi_mq_pro (1)](https://github.com/ruyisdk/support-matrix/pull/188)
- [  update Licheepi4A_RevyOS_20250123](https://github.com/ruyisdk/support-matrix/pull/189)
- [ IndexUpdator: V1 Version](https://github.com/ruyisdk/support-matrix/pull/190)
- [fix: images generation](https://github.com/ruyisdk/support-matrix/pull/191)
- [VisionFive2: add irradium(core),Bit-Brick_K1: update bianbu](https://github.com/ruyisdk/support-matrix/pull/192)
- [VisionFive2: remove non-existent images](https://github.com/ruyisdk/support-matrix/pull/196)
