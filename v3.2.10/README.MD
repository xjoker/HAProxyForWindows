# HAProxy 3.2.10 for windows

## Source code
https://www.haproxy.org/download/3.2/src/haproxy-3.2.10.tar.gz

## Build parameters
```
make TARGET=cygwin USE_OPENSSL=1 USE_PCRE2=1 USE_PCRE2_JIT=1 USE_ZLIB=1 USE_THREAD=1 USE_CRYPT_H=1 USE_PROMEX=1 USE_LUA=1 LUA_LIB_NAME=lua5.3
```

## Build info
```
HAProxy version 3.2.10-35a71a0 2025/12/18 - https://haproxy.org/
Status: long-term supported branch - will stop receiving fixes around Q2 2030.
Known bugs: http://www.haproxy.org/bugs/bugs-3.2.10.html
Running on: CYGWIN_NT-10.0-20348 3.6.6-1.x86_64 2026-01-09 17:39 UTC x86_64
Build options : 
  TARGET  = cygwin
  CC      = cc
  CFLAGS  = -O2 -g -fwrapv -fvect-cost-model=very-cheap
  OPTIONS = USE_THREAD=1 USE_CRYPT_H=1 USE_OPENSSL=1 USE_LUA=1 USE_ZLIB=1 USE_PROMEX=1 USE_PCRE2=1 USE_PCRE2_JIT=1
  DEBUG   = 

Feature list : -51DEGREES -ACCEPT4 -BACKTRACE -CLOSEFROM -CPU_AFFINITY +CRYPT_H -DEVICEATLAS -DL -ENGINE -EPOLL -EVPORTS -GETADDRINFO -KQUEUE -LIBATOMIC -LIBCRYPT -LINUX_CAP -LINUX_SPLICE -LINUX_TPROXY +LUA +MATH -MEMORY_PROFILING -NETFILTER -NS +OBSOLETE_LINKER +OPENSSL -OPENSSL_AWSLC -OPENSSL_WOLFSSL -OT -PCRE +PCRE2 +PCRE2_JIT -PCRE_JIT +POLL -PRCTL -PROCCTL +PROMEX -PTHREAD_EMULATION -QUIC -QUIC_OPENSSL_COMPAT -RT -SLZ +SSL -STATIC_PCRE -STATIC_PCRE2 -TFO +THREAD -THREAD_DUMP +TPROXY -WURFL +ZLIB +ACME

Default settings :
  bufsize = 16384, maxrewrite = 1024, maxpollevents = 200

Built with multi-threading support (MAX_TGROUPS=32, MAX_THREADS=1024, default=1).
Built with SSL library version : OpenSSL 3.0.18 30 Sep 2025
Running on SSL library version : OpenSSL 3.0.18 30 Sep 2025
SSL library supports TLS extensions : yes
SSL library supports SNI : yes
SSL library supports : SSLv3 TLSv1.0 TLSv1.1 TLSv1.2 TLSv1.3
OpenSSL providers loaded : default
Built with Lua version : Lua 5.3.6
Built with the Prometheus exporter as a service
Built with zlib version : 1.3.1
Running on zlib version : 1.3.1
Compression algorithms supported : identity("identity"), deflate("deflate"), raw-deflate("deflate"), gzip("gzip")
Built with transparent proxy support using:
Built with PCRE2 version : 10.47 2025-10-21
PCRE2 library supports JIT : yes
Encrypted password support via crypt(3): no
Built with gcc compiler version 13.4.0

Available polling systems :
       poll : pref=200,  test result OK
     select : pref=150,  test result OK
Total: 2 (2 usable), will use poll.

Available multiplexer protocols :
(protocols marked as <default> cannot be specified using 'proto' keyword)
         h2 : mode=HTTP  side=FE|BE  mux=H2    flags=HTX|HOL_RISK|NO_UPG
         h1 : mode=HTTP  side=FE|BE  mux=H1    flags=HTX|NO_UPG
  <default> : mode=HTTP  side=FE|BE  mux=H1    flags=HTX
       fcgi : mode=HTTP  side=BE     mux=FCGI  flags=HTX|HOL_RISK|NO_UPG
       spop : mode=SPOP  side=BE     mux=SPOP  flags=HOL_RISK|NO_UPG
  <default> : mode=SPOP  side=BE     mux=SPOP  flags=HOL_RISK|NO_UPG
       none : mode=TCP   side=FE|BE  mux=PASS  flags=NO_UPG
  <default> : mode=TCP   side=FE|BE  mux=PASS  flags=

Available services : prometheus-exporter
Available filters :
	[BWLIM] bwlim-in
	[BWLIM] bwlim-out
	[CACHE] cache
	[COMP] compression
	[FCGI] fcgi-app
	[SPOE] spoe
	[TRACE] trace


```
