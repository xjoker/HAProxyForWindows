# HAProxy for Windows

Automated Windows builds of HAProxy using Cygwin.

## Download

Get the latest release from [Releases](https://github.com/xjoker/HAProxyForWindows/releases).

- **haproxy-X.X.X-win64.zip** - Full package with all DLLs
- **haproxy-X.X.X-win64-nolib.zip** - Executable only (requires Cygwin)

## Quick Start

1.  **Extract**: Download and extract `haproxy-X.X.X-win64.zip`.

2.  **Create Config**: Create a file named `haproxy.cfg` in the same directory and paste the following content into it:

    ```cfg
    global
        maxconn 4096

    defaults
        mode http
        timeout connect 5s
        timeout client 50s
        timeout server 50s

    frontend web
        bind *:80
        default_backend servers

    backend servers
        server s1 127.0.0.1:8080 check
    ```

3.  **Run**: Open your terminal in the same directory and run:

    ```bash
    haproxy.exe -f haproxy.cfg
    ```

## Build Features

These builds typically include the following features:

- OpenSSL 3.x
- PCRE2 with JIT
- Zlib compression
- Multi-threading
- Lua 5.3
- Prometheus exporter

> **Note**: Each release may be built with a different Cygwin toolchain, so the included DLLs and specific features might vary. Please refer to the `README.md` file included with each release for the most accurate information.

## Requirements

- Windows 7/Server 2008 R2 or later (64-bit)
- No dependencies needed (full package)

## Build Status

Weekly automated builds from official HAProxy sources.

## License

HAProxy: GPLv2  
Build scripts: MIT
