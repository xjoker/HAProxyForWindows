# HAProxy 2.5-dev9 for windows

## Source code
http://www.haproxy.org/download/2.5/src/devel/haproxy-2.5-dev9.tar.gz
## Build parameters
```
make TARGET=cygwin USE_PCRE2_JIT=1 USE_THREAD=1 USE_CRYPT_H=1 USE_OPENSSL=1 USE_SLZ=1
```
## Build info
```
HAProxy version 2.5-dev9-4c67bd6 2021/10/08 - https://haproxy.org/
Status: development branch - not safe for use in production.
Known bugs: https://github.com/haproxy/haproxy/issues?q=is:issue+is:open
Running on: CYGWIN_NT-10.0-19043 3.2.0-340.x86_64 2021-03-29 08:42 UTC x86_64
Build options :
  TARGET  = cygwin
  CPU     = generic
  CC      = cc
  CFLAGS  = -O2 -g -Wall -Wextra -Wundef -Wdeclaration-after-statement -fwrapv -Wno-address-of-packed-member -Wno-unused-label -Wno-sign-compare -Wno-unused-parameter -Wno-clobbered -Wno-missing-field-initializers -Wno-cast-function-type -Wtype-limits -Wshift-negative-value -Wshift-overflow=2 -Wduplicated-cond -Wnull-dereference
  OPTIONS = USE_PCRE2_JIT=1 USE_THREAD=1 USE_CRYPT_H=1 USE_OPENSSL=1 USE_SLZ=1
  DEBUG   =

Feature list : -EPOLL -KQUEUE -NETFILTER -PCRE -PCRE_JIT -PCRE2 +PCRE2_JIT +POLL +THREAD -BACKTRACE -STATIC_PCRE -STATIC_PCRE2 +TPROXY -LINUX_TPROXY -LINUX_SPLICE -LIBCRYPT +CRYPT_H -GETADDRINFO +OPENSSL -LUA -ACCEPT4 -CLOSEFROM -ZLIB +SLZ -CPU_AFFINITY -TFO -NS -DL -RT -DEVICEATLAS -51DEGREES -WURFL -SYSTEMD +OBSOLETE_LINKER -PRCTL -PROCCTL -THREAD_DUMP -EVPORTS -OT -QUIC -PROMEX -MEMORY_PROFILING

Default settings :
  bufsize = 16384, maxrewrite = 1024, maxpollevents = 200

Built with multi-threading support (MAX_THREADS=64, default=1).
Built with OpenSSL version : OpenSSL 1.1.1f  31 Mar 2020
Running on OpenSSL version : OpenSSL 1.1.1f  31 Mar 2020
OpenSSL library supports TLS extensions : yes
OpenSSL library supports SNI : yes
OpenSSL library supports : SSLv3 TLSv1.0 TLSv1.1 TLSv1.2 TLSv1.3
Built with libslz for stateless compression.
Compression algorithms supported : identity("identity"), deflate("deflate"), raw-deflate("deflate"), gzip("gzip")
Built with transparent proxy support using:
Built with PCRE2 version : 10.37 2021-05-26
PCRE2 library supports JIT : yes
Encrypted password support via crypt(3): no
Built with gcc compiler version 11.2.0

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

Available services : none

Available filters :
        [SPOE] spoe
        [CACHE] cache
        [FCGI] fcgi-app
        [COMP] compression
        [TRACE] trace

```