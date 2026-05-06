# RuyiSDK 双周进展汇报 第 068 期·2026 年 05 月 06 日

## 卷首语


## 包管理器


## IDE

### VSCode 插件

- 新增一键编译系统
- 优化ruyi包管理器安装/升级逻辑
- 升级新欢迎页（初次安装或使用ruyi.home.show触发）
- 修复当用户安装新旧两个ruyi包管理器时，使用旧版本会出现“升级提示”
- 修复虚拟环境的sysroot为空

### Eclipse 插件

- 工程：维护各插件 OSGi 配置文件中信息的一致性。
- 兼容性：支持 Ruyi 0.47。
- 包管理器模块：设备列表支持手动刷新。
- 项目：发布 v0.1.3。

## GCC


## LLVM

- [RISCV][MC] Support experimental Zvdota Family instructions 
https://github.com/llvm/llvm-project/pull/195069
为 RISC-V 中的 Zvdota 扩展添加 MC 支持
正在 review

- [RISCV][MC] Add experimental Zvvmm MC support
https://github.com/llvm/llvm-project/pull/193956
为 RISC-V 的 Zvvmm 拓展增加初步的 MC 汇编支持
已经合并

- [InstCombine] Fold select of ordered fcmps of fabs over NaN-scrubber selects to a single select
https://github.com/llvm/llvm-project/pull/192182
将不可能是NaN的嵌套select ordered fcmp fabs 化简为单层select
已经合并

- [IRBuilder][NFC] Add CreateFAbs helper
https://github.com/llvm/llvm-project/pull/193421
在 IRBuilder 中创建并重构代码库中通用的 CreateFAbs 辅助函数
已经合并

## V8


## 版本测试及遗留问题
