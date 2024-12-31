# RuyiSDK双周进展汇报  第036期·2024年12月31日

## 卷首语

## 包管理器

## IDE
RuyiSDK IDE V0.0.2 版本发布，下载地址为：https://mirror.iscas.ac.cn/ruyisdk/ide/0.0.2/ 请按照设备环境选择合适的安装包。
V0.0.2 主要针对 Milk-V Duo example 示例在 RuyiSDK IDE 中的编译器安装配置、构建、目标程序传输、运行等进行验证并创建使用文档。在 RuyiSDK IDE 的 Welcome 中定制了 RuyiSDK 和 Milk-V Duo 的文档链接。


## GCC
提交了Zilsd/Zclsd扩展支持的patch，补充了相应的测试用例。开始更新Profiles命名规范，同步LLVM已有的实现方式。

## V8
1. 增加对 Embedded Object 的 reloc 支持，减少加载此类对象的指令数量。
2. 审阅并合入 Syntacore 对浮点数四舍五入的指令生成的优化。

## 操作系统支持矩阵

## SDK
