# HAProxy Windows 版 (Cygwin 构建)

[![Latest Release](https://img.shields.io/github/v/release/xjoker/HAProxyForWindows?display_name=tag&sort=semver)](https://github.com/xjoker/HAProxyForWindows/releases)
[![Downloads](https://img.shields.io/github/downloads/xjoker/HAProxyForWindows/total)](https://github.com/xjoker/HAProxyForWindows/releases)
![Windows x64](https://img.shields.io/badge/Windows-x64-blue)
![Cygwin](https://img.shields.io/badge/Built%20with-Cygwin-1f9f3f)

中文 | **[English](README.md)**

基于 **Cygwin** 自动构建的 [HAProxy](https://www.haproxy.org/) **Windows x64** 版本。

每日自动检测上游所有维护中的分支（LTS + Stable + Dev），构建包含 **OpenSSL 3.x**、**PCRE2 JIT**、**zlib**、**Lua 5.4**、**多线程**、**DNS 解析** 和 **内置 Prometheus 导出器** 的预编译二进制文件。

> **提示：** HAProxy 主要面向 Unix/Linux 系统设计。Windows 版适用于 **开发、测试和轻量生产** 场景。高性能生产环境建议使用 Linux/BSD。

---

## 下载

前往 **[Releases](https://github.com/xjoker/HAProxyForWindows/releases)** 下载。

| 包类型 | 内容 | 适用场景 |
|--------|------|----------|
| `haproxy-<ver>-win64.zip` | 可执行文件 + 所有依赖 DLL + README | **推荐** - 开箱即用 |
| `haproxy-<ver>-win64-nolib.zip` | 仅可执行文件 + README | 系统已安装 Cygwin 的环境 |

每个 Release 页面包含完整的 `haproxy -vv` 构建信息。

---

## 版本选择

| 分支 | 类型 | 生命周期结束 | 建议用途 |
|------|------|-------------|----------|
| **3.4.x** | **开发版** | 待定（预计 LTS ~2031 Q2） | 测试新功能 |
| **3.3.x** | 稳定版 | ~2027 Q1 | 最新稳定特性 |
| **3.2.x** | **长期支持 (LTS)** | ~2030 Q2 | **大多数用户的最佳选择** |
| **3.1.x** | 稳定版 | ~2026 Q1 | 上一代稳定版（建议升级到 3.3） |
| **3.0.x** | **长期支持 (LTS)** | ~2029 Q2 | 长期稳定 |
| **2.8.x** | **长期支持 (LTS)** | ~2028 Q2 | 成熟 LTS |
| **2.9.x** | 已停维 | 不再维护 | **不建议使用** - 请升级到 3.x |
| **2.6.x** | LTS（仅关键修复） | ~2027 Q2 | 遗留系统，非必要勿用 |

> **建议：** 追求稳定选 **3.2.x LTS**，追求新特性选 **3.3.x**。

---

## 构建特性

所有版本使用以下编译选项：

| 特性 | 编译标志 | 状态 |
|------|---------|------|
| OpenSSL 3.x (TLS/SSL) | `USE_OPENSSL` | 已启用 |
| PCRE2 正则 + JIT | `USE_PCRE2` `USE_PCRE2_JIT` | 已启用 |
| zlib 压缩 | `USE_ZLIB` | 已启用 |
| Lua 5.4 脚本 | `USE_LUA` | 已启用 |
| 多线程 | `USE_THREAD` | 已启用 |
| Prometheus 导出器 | `USE_PROMEX` | 已启用 |
| DNS 解析 | `USE_GETADDRINFO` | 已启用 |
| 数学库 | `USE_MATH` | 已启用 |
| 透明代理 | `USE_CRYPT_H` | 已启用 |
| QUIC (HTTP/3) | `USE_QUIC` | 不可用（需要 OpenSSL 3.5+） |

> 编译时已将链接器的 `--export-dynamic` 补丁为 `--export-all-symbols` 以兼容 Cygwin PE 格式。

---

## 快速开始

```cmd
:: 解压完整包后运行
haproxy.exe -f haproxy.cfg

:: 查看版本和构建信息
haproxy.exe -vv

:: 验证配置文件
haproxy.exe -c -f haproxy.cfg
```

---

## 注册为 Windows 服务

### 方式一：NSSM（推荐）

[NSSM](https://nssm.cc/) 是一个服务包装器，支持进程监控、自动重启和日志记录。

```powershell
# 以管理员身份运行 PowerShell
nssm install haproxy "C:\haproxy\haproxy.exe" "-f C:\haproxy\haproxy.cfg"
nssm set haproxy AppExit Default Restart
nssm set haproxy AppStdout "C:\haproxy\logs\stdout.log"
nssm set haproxy AppStderr "C:\haproxy\logs\stderr.log"
nssm start haproxy
```

### 方式二：任务计划程序

无需第三方工具，使用 Windows 内置的任务计划程序实现开机自启：

```powershell
# 以管理员身份运行 PowerShell
$action = New-ScheduledTaskAction -Execute "C:\haproxy\haproxy.exe" -Argument "-f C:\haproxy\haproxy.cfg" -WorkingDirectory "C:\haproxy"
$trigger = New-ScheduledTaskTrigger -AtStartup
$settings = New-ScheduledTaskSettingsSet -RestartCount 3 -RestartInterval (New-TimeSpan -Minutes 1)
Register-ScheduledTask -TaskName "HAProxy" -Action $action -Trigger $trigger -Settings $settings -User "SYSTEM" -RunLevel Highest
```

---

## 自动构建

通过 GitHub Actions 实现全自动构建：

- 每日 **UTC 02:00** 自动检测所有支持分支的上游新版本
- 支持手动触发指定版本或全量重新构建
- 检测到新版本后自动创建 Release
- 开发版 / 预发布版本在 GitHub 上标记为 **pre-release**

当前支持的构建分支：
- **稳定版：** 2.8, 3.0, 3.1, 3.2, 3.3
- **开发版：** 3.4

---

## 许可证

HAProxy 是基于 [GPLv2](https://www.haproxy.org/download/3.2/doc/gpl.txt) 许可的自由软件。本仓库仅提供预编译的 Windows 二进制文件，源代码和完整许可条款请参见上游 [HAProxy 项目](https://www.haproxy.org/)。
