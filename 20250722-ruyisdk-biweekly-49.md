# RuyiSDK 双周进展汇报  第 049 期·2025 年 07 月 22 日

## 卷首语

## 包管理器

## IDE

## GCC
- 支持了P扩展 v015 版本与B扩展、K扩展的重复部分指令编码，添加了相关测试用例，已同步至RUYISDK仓库与社区
- 初步完成了P扩展 v015 版本的 intrinsic 草案，正在进行GCC开发支持
- Rebase了P扩展 v0911 版本的GCC支持到 GCC15

## LLVM

## V8
- [删除RISCV32下的冗余sign extend指令(只有32位计算，不需要向高32位扩展)](https://chromium-review.googlesource.com/c/v8/v8/+/6732071)
- [修复Smi到Word的bitcast，需要从Boxed 64bit中取出tagged的部分作为smi进行转换](https://chromium-review.googlesource.com/c/v8/v8/+/6731860)
- [在Turbolev IR中加入math.sqrt 操作 ](https://chromium-review.googlesource.com/c/v8/v8/+/6731441)
- [规范符号扩展的使用，删除sll32的不恰当用法](https://chromium-review.googlesource.com/c/v8/v8/+/6725218)
- [在ReflectApply builitin中删除负优化的zicond使用](https://chromium-review.googlesource.com/c/v8/v8/+/6718872)
- [baseline JIT中对OSR offset加入更多的运行时check机制 ](https://chromium-review.googlesource.com/c/v8/v8/+/6715563)
- [修复RISCV64和ARM64模拟器中缺失的ProbeMemory函数](https://chromium-review.googlesource.com/c/v8/v8/+/6715698)
- [删除g_thread_in_wasm_code flag ](https://chromium-review.googlesource.com/c/v8/v8/+/6702434)
- [删除liftoff中冗余的code emit size margin ](https://chromium-review.googlesource.com/c/v8/v8/+/6702989)
- 审阅Rivos提交5项，主要涉及后端的代码重构，typo修复和测试用例补充完善。

## 操作系统支持矩阵

- [Tests bump (for Pine64 Star64 and more)](https://github.com/ruyisdk/support-matrix/pull/342)
- [DuoS: Dump Debian](https://github.com/ruyisdk/support-matrix/pull/343)
- [LiP4A: Dump Slackware (basic->good)](https://github.com/ruyisdk/support-matrix/pull/344)
- [Boards: clean metadata, remove test enviroment, test results. ](https://github.com/ruyisdk/support-matrix/pull/345)
