# HAProxy for Windows (Cygwin builds)

[![Latest Release](https://img.shields.io/github/v/release/xjoker/HAProxyForWindows?display_name=tag&sort=semver)](https://github.com/xjoker/HAProxyForWindows/releases)
[![Downloads](https://img.shields.io/github/downloads/xjoker/HAProxyForWindows/total)](https://github.com/xjoker/HAProxyForWindows/releases)
![Windows x64](https://img.shields.io/badge/Windows-x64-blue)
![Cygwin](https://img.shields.io/badge/Built%20with-Cygwin-1f9f3f)

**[中文文档](README_CN.md)** | English

Automated **Windows x64** builds of [HAProxy](https://www.haproxy.org/) using **Cygwin**.

All maintained upstream branches (LTS + Stable + Dev) are built daily. Each binary includes **OpenSSL 3.x**, **PCRE2 JIT**, **zlib**, **Lua 5.4**, **multi-threading**, **DNS resolution**, and the **built-in Prometheus exporter**.

> **Note:** HAProxy is primarily designed for Unix/Linux. These Windows builds are intended for **development, testing, and lightweight production** scenarios. For high-performance production use, prefer Linux/BSD.

---

## Download

Get binaries from **[Releases](https://github.com/xjoker/HAProxyForWindows/releases)**.

| Package | Contents | Use case |
|---------|----------|----------|
| `haproxy-<ver>-win64.zip` | Executable + all required DLLs + README | **Recommended** - works standalone |
| `haproxy-<ver>-win64-nolib.zip` | Executable + README only | For systems with Cygwin already installed |

Each release page includes the full `haproxy -vv` build info.

---

## Which version should I choose?

| Branch | Type | End of Life | Recommended for |
|--------|------|-------------|-----------------|
| **3.4.x** | **Dev** | TBD (future LTS ~Q2 2031) | Testing upcoming features |
| **3.3.x** | Stable | ~Q1 2027 | Latest stable features |
| **3.2.x** | **LTS** | ~Q2 2030 | **Best choice for most users** |
| **3.1.x** | Stable | ~Q1 2026 | Previous stable (upgrade to 3.3) |
| **3.0.x** | **LTS** | ~Q2 2029 | Long-term stability |
| **2.8.x** | **LTS** | ~Q2 2028 | Mature LTS |
| **2.9.x** | EOL | Unmaintained | **Avoid** - upgrade to 3.x |
| **2.6.x** | LTS (critical only) | ~Q2 2027 | Legacy only if you must |

> **Recommendation:** Use **3.2.x LTS** for stability or **3.3.x** for the latest features.

---

## Build features

All builds are compiled with the following options:

| Feature | Flag | Status |
|---------|------|--------|
| OpenSSL 3.x (TLS/SSL) | `USE_OPENSSL` | Enabled |
| PCRE2 with JIT | `USE_PCRE2` `USE_PCRE2_JIT` | Enabled |
| zlib compression | `USE_ZLIB` | Enabled |
| Lua 5.4 scripting | `USE_LUA` | Enabled |
| Multi-threading | `USE_THREAD` | Enabled |
| Prometheus exporter | `USE_PROMEX` | Enabled |
| DNS resolution | `USE_GETADDRINFO` | Enabled |
| Math library | `USE_MATH` | Enabled |
| Transparent proxy | `USE_CRYPT_H` | Enabled |
| QUIC (HTTP/3) | `USE_QUIC` | Not available (requires OpenSSL 3.5+) |

> The `--export-dynamic` linker warning is patched to `--export-all-symbols` for Cygwin PE compatibility.

---

## Quick start

```cmd
:: Extract the full package and run
haproxy.exe -f haproxy.cfg

:: Check version and build info
haproxy.exe -vv

:: Validate config
haproxy.exe -c -f haproxy.cfg
```

---

## Run as a Windows Service

### Option 1: NSSM (recommended)

[NSSM](https://nssm.cc/) is a service wrapper that handles process monitoring, restart, and logging.

```powershell
# Run PowerShell as Administrator
nssm install haproxy "C:\haproxy\haproxy.exe" "-f C:\haproxy\haproxy.cfg"
nssm set haproxy AppExit Default Restart
nssm set haproxy AppStdout "C:\haproxy\logs\stdout.log"
nssm set haproxy AppStderr "C:\haproxy\logs\stderr.log"
nssm start haproxy
```

### Option 2: Task Scheduler

Create a scheduled task to start HAProxy at boot without third-party tools:

```powershell
# Run PowerShell as Administrator
$action = New-ScheduledTaskAction -Execute "C:\haproxy\haproxy.exe" -Argument "-f C:\haproxy\haproxy.cfg" -WorkingDirectory "C:\haproxy"
$trigger = New-ScheduledTaskTrigger -AtStartup
$settings = New-ScheduledTaskSettingsSet -RestartCount 3 -RestartInterval (New-TimeSpan -Minutes 1)
Register-ScheduledTask -TaskName "HAProxy" -Action $action -Trigger $trigger -Settings $settings -User "SYSTEM" -RunLevel Highest
```

---

## Automated builds

Builds are automated via GitHub Actions:

- **Daily check** at 02:00 UTC for new upstream releases across all supported series
- **Manual trigger** available for specific versions or full rebuild
- New releases are automatically created when a new upstream version is detected
- Dev/pre-release versions are marked as **pre-release** on GitHub

Supported series are configured in the workflow:
- **Stable:** 2.8, 3.0, 3.1, 3.2, 3.3
- **Dev:** 3.4

---

## License

HAProxy is free software licensed under the [GPLv2](https://www.haproxy.org/download/3.2/doc/gpl.txt). This repository provides only pre-compiled Windows binaries; see the upstream [HAProxy project](https://www.haproxy.org/) for source code and full license terms.
