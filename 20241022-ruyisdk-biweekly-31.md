# RuyiSDK双周进展汇报  第031期·2024年10月22日

## 卷首语

## 包管理器

## IDE
从零开始开发VSCode插件与Ruyi IDE插件 第2课已经上线B站。视频可以在[此](https://space.bilibili.com/13429452)观看。欢迎点赞关注一键三连！

## GCC

## LLVM

- 支持 rv64ilp32 ABI，目前可以成功编译 rv64ilp32 Linux kernel（bf63582b08）并进入用户态了（需要使用 [rv64ilp32](https://github.com/ruyisdk/llvm-project/tree/rv64ilp32) 分支下的代码），还有部分小问题正在修复中
- XTHeadVector 拓展正在逐渐 rebase 到 LLVM 19.1.1 上，目前已经完成了大部分的 rebase 工作，正在进行测试

## V8

## 官网

## 操作系统支持矩阵

新增：
- VisionFive 2 / NetBSD
- Duo 256M / Alpine, Arch Linux
- Mango MQ Pro / NetBSD
- Duo S / Arch Linux
- Huashan Pi / buildroot
- Milk-V Jupiter / Bianbu 1.0
- CI 生成首页表格 SVG

更新：
- VisionFive 2 / Ubuntu: 24.04 LTS -> 24.04.1 LTS, 24.10
- BPI-F3: typo fix
- VisionFive 2 / openKylin: 2.0
- PIC64GX / Ubuntu: 24.10

此外，我们为所有测试报告都添加了元数据，方便后续与 packages-index 同步更新。
