# RuyiSDK 双周进展汇报  第 041 期·2025 年 03 月 25 日

## 卷首语

## 包管理器

## IDE

## GCC
提交了Ssnpm, Smnpm与Smmpm 的工具链支持，在社区中对玄铁C系列RISC-V芯片添加了mcpu选项支持

## LLVM

- 在 17.1.6 版本中新增默认 `_mu` 和 `_tum` 类 policy 的 XTHeadVector 内建指令，与 RVV 1.0 的命名方式提供更好的兼容性。
- 在 17.1.6 中修复 mask 版本的 vector bitwise logical 内建指令的指令选择问题。
- 在 17.1.6 中补全 vector integer merge 和 vector floating-point merge 相关的内建指令。

## V8

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
