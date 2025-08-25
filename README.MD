# HAProxy for Windows (Cygwin builds)

[![Latest Release](https://img.shields.io/github/v/release/xjoker/HAProxyForWindows?display_name=tag&sort=semver)](https://github.com/xjoker/HAProxyForWindows/releases)
[![Downloads](https://img.shields.io/github/downloads/xjoker/HAProxyForWindows/total)](https://github.com/xjoker/HAProxyForWindows/releases)
![Windows x64](https://img.shields.io/badge/Windows-x64-blue)
![Cygwin](https://img.shields.io/badge/Built%20with-Cygwin-1f9f3f)

Automated **Windows x64** builds of [HAProxy](https://www.haproxy.org/) using **Cygwin**.  
Binaries include **OpenSSL 3.x**, **PCRE2 JIT**, **zlib**, **multi-threading**, **Lua 5.3**, and the **built-in Prometheus exporter**.

> ⚠️ Note: HAProxy is primarily designed for Unix/Unix-like systems. These Windows builds target **development/testing** scenarios on Windows; for production, prefer Linux/BSD.

---

## Table of Contents

- [Download](#download)
- [Which version should I choose?](#which-version-should-i-choose)
- [Run as a Windows Service (NSSM)](#run-as-a-windows-service-nssm)

---

## Download

Get the latest binaries from **[Releases](https://github.com/xjoker/HAProxyForWindows/releases)**.

- `haproxy-<ver>-win64.zip` – **Full package**, includes required DLLs. *(recommended)*
- `haproxy-<ver>-win64-nolib.zip` – **Executable only** (requires Cygwin runtime installed system-wide).

Each release page includes the **`haproxy -vv`** build info and options.

---

## Which version should I choose?

| Branch | Status / EOL (from upstream notes) | Recommended for |
|---|---|---|
| **3.2.x** | **LTS** – fixes until ~**Q2 2030** | Long-term stability on Windows |
| **3.1.x** | Stable – fixes until ~**Q1 2026** | Latest stable features |
| **2.8.x** | **LTS** – fixes until ~**Q2 2028** | Mature LTS |
| **2.6.x** | **LTS** – fixes until ~**Q2 2027** | Legacy LTS (only if you must) |
| **2.9.x** | **EOL** – upgrade to 3.x | Avoid for new installs |
| **2.7.x / 2.5.x** | **EOL** | Do not use |

> See the corresponding release notes for exact status per tag.


| Version | OPENSSL | PCRE | PCRE2 | PCRE2 JIT | Lua | Zlib | Prometheus (PROMEX) | TPROXY | SLZ |
|---|---|---|---|---|---|---|---|---|---|
| v3.2.x | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✖ |
| v3.1.x | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✖ |
| v2.9.x | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✖ |
| v2.8.x | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✖ |
| v2.7.x | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✖ |

---

## Run as a Windows Service (NSSM)

If you want HAProxy to start at boot and run headless, use **NSSM**:

```powershell
# Run PowerShell/CMD as Administrator
nssm install haproxy "C:\haproxy\haproxy.exe" "-f C:\haproxy\haproxy.cfg"
nssm set haproxy AppExit Default Restart
nssm start haproxy
```

> Alternative: Task Scheduler can also start HAProxy at boot if you prefer no third-party tools.

---
