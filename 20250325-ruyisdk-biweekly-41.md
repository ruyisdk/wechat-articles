# RuyiSDK 双周进展汇报  第 041 期·2025 年 03 月 25 日

## 卷首语

## 包管理器

## IDE
RuyiSDK IDE 近期正在实现基于包管理器（ruyi list）的软件包资源管理，功能开发中。

此外，RuyiSDK IDE 正在招聘插件开发实习生，欢迎有兴趣的小伙伴加入开发团队，详情参考 [J159 RuyiSDK IDE 开发实习生](https://github.com/lazyparser/weloveinterns/blob/master/open-internships.md) ，期待您的加入。

## GCC
提交了Ssnpm, Smnpm与Smmpm 的工具链支持，在社区中对玄铁C系列RISC-V芯片添加了mcpu选项支持

## LLVM

- 在 17.1.6 版本中新增默认 `_mu` 和 `_tum` 类 policy 的 XTHeadVector 内建指令，与 RVV 1.0 的命名方式提供更好的兼容性。
- 在 17.1.6 中修复 mask 版本的 vector bitwise logical 内建指令的指令选择问题。
- 在 17.1.6 中补全 vector integer merge 和 vector floating-point merge 相关的内建指令。

## V8
- 继续增加 WASM JSPI 的支持功能： 
  - in-sandbox chain of stacks 
  - 删除 jump buffer 外部指针
- 增加 C++ 垃圾回收模块的 Scan simulator stack and registers 功能
- 修复 WASM OOB Trap Handler 特性中，Fault Address Register 没有在 mcontext 中被正确设置的 bug
- 审阅并合入 syntacore 的2个 patch ：
  - 优化32位比较操作代码生成 
  - 类型转换优化
- 修复非对齐 load/store 的代码生成中临时寄存器不够用的问题
- 在指令选择阶段内联 Adapter's DeoptimizeView

## 操作系统支持矩阵

- [CONTRIBUTING: Add CONTRIBUTING.md and report-templates](https://github.com/ruyisdk/support-matrix/pull/193)
- [Add Ubuntu testing reports for MilkV DuoS](https://github.com/ruyisdk/support-matrix/pull/201)
- [Fix: broken Zephyr link](https://github.com/ruyisdk/support-matrix/pull/202)
- [Add/Update mangopi_mq_pro / dongshanpistu (2)](https://github.com/ruyisdk/support-matrix/pull/200)
- [Add Mars Deepin 25 test reports and Ubuntu LTS reports.](https://github.com/ruyisdk/support-matrix/pull/203)
- Web 前端
  - https://verforte.vercel.app/
  - https://github.com/panglars/VeRForTe
  - 开发中
