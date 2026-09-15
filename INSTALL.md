# Mac 预览版下载、安装与打开问题

## 请先了解限制

SpaceLens 0.1.0 是开发预览版，只有本地临时签名（ad hoc），**没有 Apple Developer ID 正式签名，也没有 Apple 公证**。macOS 可能提示“无法验证开发者”或“Apple 无法检查其是否包含恶意软件”。GitHub 提供下载不代表 Apple 已审核软件，MIT 许可证也不提供安全或兼容性保证。

支持目标：macOS 13+、Apple Silicon（M 系列）。当前仅在 macOS 14.4.1 / Apple Silicon 完成本机基本流程验证。Intel Mac 不适用此安装包；其他系统版本和所有设备均未逐一验证。组织管理的 Mac 可能禁止手动放行。

## 下载与校验

1. 只从 [项目 Releases](https://github.com/sxlforget2-cyber/spacelens/releases) 的 `v0.1.0-preview.2` 下载 `SpaceLens-0.1.0-arm64-preview.zip` 及同名 `.sha256` 文件；不要把 GitHub 自动生成的 Source code ZIP 当成安装包。
2. 把两个文件放在同一目录，在该目录打开终端后运行：

```sh
shasum -a 256 -c SpaceLens-0.1.0-arm64-preview.zip.sha256
```

应显示安装包文件名及 `OK`。不匹配请停止，不要运行。校验用于比对下载内容，并不等同于恶意软件检测或独立的身份认证。

3. 解压 ZIP，把 `SpaceLens.app` 放到“应用程序”或你自己的应用目录，再双击尝试打开。

## 提示“无法验证开发者”时

仅在你已确认来源可信、理解未公证风险且希望运行此软件的情况下，由你本人操作：

1. 先尝试打开一次，然后关闭拦截提示。
2. 打开苹果菜单 → **系统设置 → 隐私与安全性**。
3. 在安全性区域找到针对 SpaceLens 的提示，若系统提供 **“仍要打开”**，点击该按钮，并按系统要求认证和再次确认打开。

这是 Apple 提供的针对单个 App 的例外操作，**不会使 App 获得正式签名或公证**。不同 macOS 版本显示可能不同；按钮通常在尝试打开后的一段时间内提供。不要关闭 Gatekeeper、不要修改全局“允许任何来源”，不要批量删除下载隔离属性。

如果提示 **“会损坏你的电脑”/包含恶意软件**，请停止运行，不要绕过；如果提示 **“已损坏”**，先删除本次下载副本并从官方发布页重新下载、核验 SHA-256，仍失败就反馈，不要强制放行。如果没有“仍要打开”或设备受组织管理，请联系管理员或等待正式签名版。

Apple 官方说明：[在 Mac 上安全地打开 App](https://support.apple.com/zh-cn/102445)。

## 另一种方式：审阅源码后本机编译

适合有开发经验的用户：安装 Apple 官方 Xcode Command Line Tools，下载源码包，解压后进入其中的 `SpaceLens` 目录，运行：

```sh
swift build -c release
swift run -c release ScanCoreChecks
bash build-app.sh
```

此路径需要 macOS SDK、Swift 5.9+（本项目当前使用 Swift 5.10）及命令行工具，不是面向普通用户的“一键安装”，也不等于 Apple 公证。

## 使用和反馈

首次打开显示示例数据。选择具体目录才开始只读扫描；本版不删除文件、不结束进程。导出 JSON 包含使用者自己的文件路径，不要直接上传公开 Issue。请先用测试目录体验。

无法打开时，请在 [Issues](https://github.com/sxlforget2-cyber/spacelens/issues) 提供 macOS 版本、芯片类型、安装包名称、校验是否成功及脱敏的错误提示。不要上传身份证件、密码、真实文件清单或钥匙串文件。
