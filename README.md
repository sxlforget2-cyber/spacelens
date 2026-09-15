# SpaceLens · 空间透镜

面向 AI 编程工作流的本地只读 Mac 文件检查工具。识别重复文件、大文件、长期未修改文件和开发产物，提供判断依据，由使用者决定如何处理。

## 下载预览版

**[前往 Releases 下载 v0.1.0-preview.2](https://github.com/sxlforget2-cyber/spacelens/releases/tag/v0.1.0-preview.2)**

选择 `SpaceLens-0.1.0-arm64-preview.zip` 和对应 `.sha256` 文件；GitHub 自动生成的 Source code ZIP 不是安装包。

系统目标：macOS 13+、Apple Silicon（M 系列）。当前仅在 macOS 14.4.1 / Apple Silicon 完成本机基本流程测试。Intel Mac 不适用这个安装包。

## 重要：尚未正式签名和公证

本版仅有本地临时签名（ad hoc），**没有 Apple Developer ID 正式签名，没有 Apple 公证**。macOS 可能阻止打开。GitHub 下载不代表 Apple 审核通过，不能保证所有设备都能直接打开。

请先阅读 **[安装、校验与打开问题解决方法](INSTALL.md)**：

1. 校验 ZIP 的 SHA-256，解压并尝试打开。
2. 仅在确认来源可信并接受风险后，由你本人前往“系统设置 → 隐私与安全性”，使用系统针对 SpaceLens 提供的“仍要打开”。这只是单个 App 的例外，不等于完成公证。
3. 如果系统提示包含恶意软件、会损坏电脑，或文件校验不一致，请停止，不要强制运行。没有放行选项时，可以审阅源码后本机编译，或等待正式签名版。

不要关闭 Gatekeeper、不要设置全局“允许任何来源”、不要批量移除下载隔离属性。组织管理设备可能禁止放行。参考 [Apple 官方说明](https://support.apple.com/zh-cn/102445)。

## 已有能力与限制

- 本机扫描和内容比对，不上传扫描文件，不接入模型 API、广告或统计。
- 不删除文件、不关闭进程；勾选只加入待处理清单。
- 候选文件体积不等于保证可释放空间，清理磁盘也不等于直接释放运行内存。
- 17 项扫描回归检查通过。
- 本机已验证解压、启动、目录选择、扫描、分类筛选、勾选和 JSON 导出。完整 GUI、多机、其他 macOS 版本和正式下载 Gatekeeper 验收未完成。

## 源码与开发

下载 [SpaceLens-GitHub-source.zip](SpaceLens-GitHub-source.zip)，解压后进入其中的 `SpaceLens` 目录：

```sh
swift build -c release
swift run -c release ScanCoreChecks
bash build-app.sh
```

需要 Apple 官方命令行工具、macOS SDK、Swift 5.9+。源码以压缩包保留完整目录结构；包内 `.github` 配置没有部署至仓库根目录，因此自动检查尚未在 GitHub 运行。详细规则、隐私说明、发布脚本和测试记录在源码包中。

## 授权与隐私

采用 [MIT 许可证](LICENSE)，版权署名 `sxlforget2-cyber`，允许在遵守许可证的前提下使用、修改、再分发和商用，按原样提供，不作担保。

发布包已重映射构建路径、剥离调试信息，并检查已配置私密词、绝对用户目录、ZIP 元数据和二进制内容；不承诺绝对匿名。GitHub 提交邮箱经所有者允许保留。将来如采用个人 Apple Developer ID 正式签名，证书可能显示开发者真实姓名，届时会明确标注；当前并未完成这种签名。

应用展示的是使用者选择目录后的本机路径，不附带发布者扫描历史。导出 JSON 含真实路径，反馈请使用虚构文件名和脱敏截图，不要上传完整报告、密钥或个人文件。
