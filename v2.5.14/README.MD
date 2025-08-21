# HAProxy 2.5.14 for windows

## Source code
https://www.haproxy.org/download/2.5/src/haproxy-2.5.14.tar.gz

## Build parameters
```
make TARGET=cygwin USE_OPENSSL=1 USE_PCRE2=1 USE_PCRE2_JIT=1 USE_ZLIB=1 USE_THREAD=1 USE_CRYPT_H=1 USE_PROMEX=1 USE_LUA=1 LUA_INC=/usr/include/lua5.3 LUA_LIB=/usr/lib LUA_LIB_NAME=lua5.3
```

## Build info
```
HAProxy version 2.5.14-52b556a 2023/05/02 - https://haproxy.org/
Status: End of life - please upgrade to branch 2.6.
Known bugs: http://www.haproxy.org/bugs/bugs-2.5.14.html
Running on: CYGWIN_NT-10.0-26100 3.6.4-1.x86_64 2025-07-15 07:55 UTC x86_64
Build options :
  TARGET  = cygwin
  CPU     = generic
  CC      = cc
  CFLAGS  = -O2 -g -Wall -Wextra -Wundef -Wdeclaration-after-statement -fwrapv -Wno-address-of-packed-member -Wno-unused-label -Wno-sign-compare -Wno-unused-parameter -Wno-clobbered -Wno-missing-field-initializers -Wno-cast-function-type -Wtype-limits -Wshift-negative-value -Wshift-overflow=2 -Wduplicated-cond -Wnull-dereference
  OPTIONS = USE_PCRE2=1 USE_PCRE2_JIT=1 USE_THREAD=1 USE_CRYPT_H=1 USE_OPENSSL=1 USE_LUA=1 USE_ZLIB=1 USE_PROMEX=1
  DEBUG   = 

Feature list : -51DEGREES -ACCEPT4 -BACKTRACE -CLOSEFROM -CPU_AFFINITY +CRYPT_H -DEVICEATLAS -DL -EPOLL -EVPORTS -GETADDRINFO -KQUEUE -LIBCRYPT -LINUX_SPLICE -LINUX_TPROXY +LUA -MEMORY_PROFILING -NETFILTER -NS +OBSOLETE_LINKER +OPENSSL -OT -PCRE +PCRE2 +PCRE2_JIT -PCRE_JIT +POLL -PRCTL -PROCCTL +PROMEX -QUIC -RT -SLZ -STATIC_PCRE -STATIC_PCRE2 -SYSTEMD -TFO +THREAD -THREAD_DUMP +TPROXY -WURFL +ZLIB

Default settings :
  bufsize = 16384, maxrewrite = 1024, maxpollevents = 200

Built with multi-threading support (MAX_THREADS=64, default=1).
Built with OpenSSL version : OpenSSL 3.0.17 1 Jul 2025
Running on OpenSSL version : OpenSSL 3.0.17 1 Jul 2025
OpenSSL library supports TLS extensions : yes
OpenSSL library supports SNI : yes
OpenSSL library supports : SSLv3 TLSv1.0 TLSv1.1 TLSv1.2 TLSv1.3
Built with Lua version : Lua 5.3.6
Built with the Prometheus exporter as a service
Built with zlib version : 1.3.1
Running on zlib version : 1.3.1
Compression algorithms supported : identity("identity"), deflate("deflate"), raw-deflate("deflate"), gzip("gzip")
Built with transparent proxy support using:
Built with PCRE2 version : 10.45 2025-02-05
PCRE2 library supports JIT : yes
Encrypted password support via crypt(3): no
Built with gcc compiler version 13.4.0

Available polling systems :
       poll : pref=200,  test result OK
     select : pref=150,  test result OK
Total: 2 (2 usable), will use poll.

Available multiplexer protocols :
(protocols marked as <default> cannot be specified using 'proto' keyword)
              h2 : mode=HTTP       side=FE|BE     mux=H2       flags=HTX|CLEAN_ABRT|HOL_RISK|NO_UPG
            fcgi : mode=HTTP       side=BE        mux=FCGI     flags=HTX|HOL_RISK|NO_UPG
              h1 : mode=HTTP       side=FE|BE     mux=H1       flags=HTX|NO_UPG
       <default> : mode=HTTP       side=FE|BE     mux=H1       flags=HTX
            none : mode=TCP        side=FE|BE     mux=PASS     flags=NO_UPG
       <default> : mode=TCP        side=FE|BE     mux=PASS     flags=

Available services : prometheus-exporter
Available filters :
	[SPOE] spoe
	[CACHE] cache
	[FCGI] fcgi-app
	[COMP] compression
	[TRACE] trace


```
