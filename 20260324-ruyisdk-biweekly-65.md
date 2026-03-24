# RuyiSDK 双周进展汇报 第 065 期·2026 年 03 月 24 日

## 卷首语

## 包管理器

## IDE

### VSCode 插件

- [修复创建虚拟环境时 sysroot 缺失127](https://github.com/ruyisdk/ruyisdk-vscode-extension/issues/127)
- 重构虚拟环境 profile 提取逻辑

### Eclipse 插件

- 重构代码，集中插件内所有对 Ruyi 包管理器的调用，为将来铺路。
- 调研并编写代码测试基于 OIDC 的 Discourse 用户登录逻辑。

## GCC
提交了Zibi扩展的工具链支持，修复了RVP在RV32构建时intrinsic生成不正确的问题

## LLVM

上游：
- [RISCV]Lower one active interleaved load to normal segmented load (#185602) https://github.com/llvm/llvm-project/pull/185602
生成stride load指令。已经合并
- [InstCombine] Fold fcmp (C - [su]itofp X), C to integer compares https://github.com/llvm/llvm-project/pull/185826
将含有整数转换成的浮点数的比较转换成整数比较。正在 review
- [PatternMatch][NFC] Add m_IToFP and m_FPToI https://github.com/llvm/llvm-project/pull/188040
新增 m_IToFP 和 m_FPToI 两个 IR 模式匹配函数。已经合并


P 拓展：
- add missing blank lines https://github.com/riscv/riscv-p-spec/pull/229
修复 P spec 文档格式错误 已合并

- Minor fixes for typos and inconsistencies - https://github.com/topperc/p-ext-intrinsics/pull/2
修复 topperc P intrinsics spec 文档多处指令、函数名错误，以及一些格式修复。 已合并

## V8

## 版本测试及遗留问题
