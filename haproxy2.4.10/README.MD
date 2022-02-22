# HAProxy 2.4.10 for windows

## Source code
http://www.haproxy.org/download/2.4/src/haproxy-2.4.10.tar.gz
## Build parameters
```
make TARGET=cygwin USE_PCRE2_JIT=1 USE_THREAD=1 USE_CRYPT_H=1 USE_OPENSSL=1 USE_SLZ=1
```
## Build info
```
HAProxy version 2.4.10-bedf277 2021/12/23 - https://haproxy.org/
Status: long-term supported branch - will stop receiving fixes around Q2 2026.
Known bugs: http://www.haproxy.org/bugs/bugs-2.4.10.html
Running on: CYGWIN_NT-10.0-19043 3.3.3-341.x86_64 2021-12-03 16:35 UTC x86_64
Build options :
  TARGET  = cygwin
  CPU     = generic
  CC      = cc
  CFLAGS  = -O2 -g -Wall -Wextra -Wdeclaration-after-statement -fwrapv -Wno-address-of-packed-member -Wno-unused-label -Wno-sign-compare -Wno-unused-parameter -Wno-clobbered -Wno-missing-field-initializers -Wno-cast-function-type -Wtype-limits -Wshift-negative-value -Wshift-overflow=2 -Wduplicated-cond -Wnull-dereference
  OPTIONS = USE_PCRE2_JIT=1 USE_THREAD=1 USE_CRYPT_H=1 USE_OPENSSL=1 USE_SLZ=1
  DEBUG   =

Feature list : -EPOLL -KQUEUE -NETFILTER -PCRE -PCRE_JIT -PCRE2 +PCRE2_JIT +POLL -PRIVATE_CACHE +THREAD -PTHREAD_PSHARED -BACKTRACE -STATIC_PCRE -STATIC_PCRE2 +TPROXY -LINUX_TPROXY -LINUX_SPLICE -LIBCRYPT +CRYPT_H -GETADDRINFO +OPENSSL -LUA -FUTEX -ACCEPT4 -CLOSEFROM -ZLIB +SLZ -CPU_AFFINITY -TFO -NS -DL -RT -DEVICEATLAS -51DEGREES -WURFL -SYSTEMD +OBSOLETE_LINKER -PRCTL -PROCCTL -THREAD_DUMP -EVPORTS -OT -QUIC -PROMEX -MEMORY_PROFILING

Default settings :
  bufsize = 16384, maxrewrite = 1024, maxpollevents = 200

Built with multi-threading support (MAX_THREADS=64, default=1).
Built with OpenSSL version : OpenSSL 1.1.1l  24 Aug 2021
Running on OpenSSL version : OpenSSL 1.1.1l  24 Aug 2021
OpenSSL library supports TLS extensions : yes
OpenSSL library supports SNI : yes
OpenSSL library supports : SSLv3 TLSv1.0 TLSv1.1 TLSv1.2 TLSv1.3
Built with libslz for stateless compression.
Compression algorithms supported : identity("identity"), deflate("deflate"), raw-deflate("deflate"), gzip("gzip")
Built with transparent proxy support using:
Built with PCRE2 version : 10.39 2021-10-29
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