# RuyiSDK双周进展汇报  第027期·2024年08月13日

## 卷首语


## 包管理器


## IDE


## GCC
RUYISDK-GNU-Toolchain发布了基于GCC14.2与Binutils2.43的linux工具链，修复了回归测试中发现的一些问题。

## LLVM


## 官网

截止今日 8 月 13 日，订阅人数一共 40 人（增加 2 人）。RuyiSDK 网站访问人数 834 人（增加 266 人），访问页面 4907 次（增加 2197 次）。RuyiSDK 微信交流群 83 人（进群请加微信小助手 ruyisdk_helper）。

嘉楠勘智 K230D: 首款基于新 32 位 RuyiSDK 的 AIoT 量产芯片，详情阅读官网博客 https://ruyisdk.org/blog/2024/07/30/k230d/

## 操作系统支持矩阵

本期更新：

- Milk-V Duo S / [NuttX RTOS](https://github.com/ruyisdk/support-matrix/commit/015002b786fbd5117f5e2e9a432d0ca10df4ebe3): 同步最新主线版本
- Milk-V Pioneer : 新增 [Deepin RISC-V](https://github.com/ruyisdk/support-matrix/commit/6a7f56534ae10685846793fcb6ce19b6a5f37cff)
- StarFive VisionFive 2: [重测](https://github.com/linuxdeepin/developer-center/issues/9882)了 Deepin RISC-V CI build，已确认可用
- 主表格：同步 Deepin 测试结果

自动化测试/应用软件支持矩阵准备：[lintestor](https://github.com/255doesnotexist/lintestor)
  - 目前已完成了 Debian 的部分测试用例，结果见[此处](https://github.com/255doesnotexist/lintestor/blob/main/summary.md)
