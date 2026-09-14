# SpaceLens · 空间透镜

面向 AI 编程工作流的本地只读 Mac 文件检查工具。识别重复文件、大文件、长期未修改文件和开发产物，并展示判断依据，由用户决定如何处理。

## 当前状态

这是私有发布准备仓库，尚未正式公开发布。应用为 0.1.0 开发预览版，macOS 13+，当前预览安装包仅适用于 Apple Silicon（M 系列）。

- 本地扫描与内容比对，不上传扫描文件。
- 不删除文件、不关闭进程。
- 候选文件体积不代表保证可释放空间。
- 本地编译及 17 项扫描回归检查通过。
- 完整 GUI 验收、多机测试、Developer ID 签名和 Apple 公证尚未完成。

## 源码

下载本仓库的 [SpaceLens-GitHub-source.zip](SpaceLens-GitHub-source.zip)，解压后进入 `SpaceLens` 目录：

```sh
swift build -c release
swift run -c release ScanCoreChecks
bash build-app.sh
```

该压缩包包含完整目录结构、Swift 源码、隐私说明、发布手册及 GitHub 自动检查配置。当前仓库采用源码压缩包交付，压缩包内的 `.github` 工作流尚未部署至仓库根目录，因此不会自动运行。

## 预览包

预览安装包和对应 SHA-256 校验文件放在 Releases 草稿中。带 `-preview` 后缀的包只有临时签名，尚未完成 Apple 公证。请勿把它描述为正式发布或已完成安装兼容性验证。

## 授权与隐私

源码公开范围和许可证尚待所有者确定，本仓库暂不授予开源许可。源码包中的 `LICENSE-DECISION.md` 记录了待决事项。

应用自身没有接入广告、统计或模型 API。导出的清单包含本地文件路径；反馈时请使用虚构文件名和脱敏截图，不要上传完整扫描报告。详细说明见源码包中的 `PRIVACY.md`。
