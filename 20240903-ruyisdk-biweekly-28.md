# RuyiSDK双周进展汇报  第028期·2024年09月03日

## 卷首语

## 包管理器

## IDE

## GCC
- 支持了Zimop扩展
- 修复了部分回归测试中发现的错误

## LLVM

- 支持了对 tuple type 的 vget/vset/vcreate 操作。
- 修复在指定 XTHeadVector 拓展时，编译器未定义 `__riscv_vector` 的问题，现在编译器行为与 GCC 一致。

## V8

## 官网

截止今日9月3日，RuyiSDK 网站访问人数986人，新增152人，访问页面7622次，新增2755次。RuyiSDK 微信交流群132人，新增49人（进群请加微信小助手 ruyisdk_helper）。

官网新增 algolia search，现在可以搜索网站上的任何内容啦！

[RuyiSDK 亮相 elexcon 2024深圳国际电子展](https://mp.weixin.qq.com/s/Rr04my4SxRPfTT7-wvKriw)

## 操作系统支持矩阵

- 修正了部分 typo 和 i18n / 英文翻译。
- lintestor 应用软件可用性测试项目继续更新中
  - 重写了测试调度相关的代码
  - 添加了全局前置环境配置
  - 改进了测试结果报告
  - 新增了更多软件包的测试用例
