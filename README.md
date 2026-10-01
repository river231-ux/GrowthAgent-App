# GrowthAgent X for macOS / Linux

GrowthAgent X 是 GrowthAgent 的桌面 X 执行器。搜索、读取和发布工作都由服务器下发，App 不自行制定搜索计划或业务周期。

## 安装

1. 从 [Releases](https://github.com/river231-ux/GrowthAgent-App/releases) 下载最新的 `GrowthAgent-X_<version>_universal.dmg`。
2. 将 GrowthAgent X 拖入 Applications。
3. 首次打开时，如果 macOS 阻止未签名应用，请在“系统设置 -> 隐私与安全性”中允许一次。
4. 安装并连接 OpenCLI Browser Bridge 扩展。
5. 在 GrowthAgent 后台生成配对码，然后在 App 中添加 X Worker 并选择对应 Profile。

后续版本由 App 自动下载、验证并安装。

### Linux

1. 下载 `GrowthAgent-X_<version>_x86_64.AppImage`（通用）或 `.deb`（Debian / Ubuntu）。
2. AppImage 在文件属性中允许执行后打开；也可运行 `chmod +x GrowthAgent-X_*.AppImage`。无 FUSE 的环境可使用 `--appimage-extract-and-run`。
3. 安装 Chrome 和 OpenCLI Browser Bridge，登录 X 并连接 Profile。
4. 启用并解锁系统 Secret Service 密钥环（例如 GNOME Keyring），再输入配对码。凭证不会以明文保存在本地数据库。
5. Linux App 需要图形桌面和用户 D-Bus 会话，不是无桌面服务器守护进程。AppImage 支持签名自动更新；`.deb` 请通过安装新软件包更新。

## 支持范围

- macOS 13 或更高版本
- Apple Silicon 和 Intel Mac
- Linux x86_64，建议 Ubuntu 24.04 或兼容的现代桌面系统
- 中文界面

此仓库只用于公开安装包和自动更新文件。应用源代码不在此仓库发布。

每个版本的公开发布记录保存在 `releases/`。Git 标签指向对应版本的公开发布记录提交；构建应用的私有源码提交和构建任务记录在该文件及 Release 说明中。GitHub 自动生成的 Source code 压缩包只包含本仓库的安装说明和发布记录，并不是应用源码。请从 Release 的 Assets 下载安装包。
