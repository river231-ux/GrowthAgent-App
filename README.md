# GrowthAgent X for Linux

GrowthAgent X 是 GrowthAgent 的 Linux 桌面执行器。服务器负责搜索计划、Signals、公告、审核、预算和发布结算；App 使用绑定的 Chrome / OpenCLI Profile 执行读取和发布。

0.1.24 起提供 X、Facebook、Instagram、小红书（`xiaohongshu.com`）、Bluesky 和 Threads 的渠道接入。`rednote.com` 不在接入范围内。新渠道需要单独配置官方账号并完成真实账号联调后启用。

## 安装

从 [Releases](https://github.com/river231-ux/GrowthAgent-App/releases) 下载 Linux x86_64 安装包：

- production：`GrowthAgent-X_<version>_x86_64.AppImage` 或 `.deb`，连接 `https://agent.openmodel.online`。
- staging：`GrowthAgent-X_<version>_staging_x86_64.AppImage` 或 `.deb`，连接 `https://agentcocreate.com`。

两套 App 的服务器、安装身份、更新清单和本地数据相互隔离。请选择与后台环境相同的安装包。

1. AppImage 先允许执行：`chmod +x GrowthAgent-X_*.AppImage`。无 FUSE 的环境可使用 `--appimage-extract-and-run`；Debian / Ubuntu 也可安装 `.deb`。
2. 准备图形桌面、用户 D-Bus 会话，以及已启用并解锁的 Secret Service 密钥环（例如 GNOME Keyring）。App 不作为无桌面服务器守护进程运行。
3. 安装 Chrome 和 OpenCLI Browser Bridge，在对应 Profile 登录所需平台的官方账号。
4. 在匹配环境的 GrowthAgent 后台配置渠道并生成配对码，再在 App 中添加绑定、选择 Profile 和核对账号。凭证保存在系统密钥环中。

## 更新与诊断

AppImage 支持签名自动更新；`.deb` 通过安装新版软件包更新。0.1.24 改进了免 FUSE 启动模式保留、更新互斥、安装期间的 Worker 启动隔离和启动失败日志。

启动日志位于用户数据目录的 `com.growthagent.x/logs/startup.log`；staging 使用 `com.growthagent.x.staging/logs/startup.log`。Linux 实际客户端升级和真实平台账号运行仍需在目标桌面环境验证。

## 校验与发布来源

Release Assets 提供安装包、AppImage `.sig` 签名、production/staging 更新清单和 `SHA256SUMS`。构建流水线会解包检查 App、Worker Core、OpenCLI 版本及环境绑定，并验证更新签名。

本仓库只公开安装包、安装说明和自动更新文件，不公开应用源码。每个版本的 `releases/` 记录及 Release 说明包含私有源码提交和构建任务。GitHub 自动生成的 Source code 压缩包是分发记录，不是应用源码；请从 Assets 下载安装包。
