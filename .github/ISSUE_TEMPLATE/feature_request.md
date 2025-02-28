---
name: Build failure rrdtool-1.9.0 embedded
about: Embedded buildroot builds fail for rrdlua
title: 'Issue building for an embedded solution'
labels: 'embedded lua'
assignees: ''

---

**Is your feature request related to a problem? Please describe.**
Issue building for an embedded solution.  We are building within a buildroot environment that also includes the lua-5.1.5 package.
When attempting to build with "--enable-lua", we have also tried with "--enable-lua-site-install", configure looks at the version, if any of the lua installed on the build system rather that the version within the buildroot environment.

As buildroot may be built on a random system, installing lua-5.1.5 and lua-dev on all systems that may be used to build the environment, that is not really an option.

**Describe the solution you'd like**
Ultimately, the ability to indicate a "cross-compiler" type environment is preferred

**Describe alternatives you've considered**
I have tried forcing the values of "LUA_MAJOR", "LUA_MINOR" and "LUA_POINT", there are numerous other assumptions that depend the build system having lua and lua-dev installed.

**Additional context**
From "config.log"
configure:19506: checking for lua
configure:19524: found /usr/bin/lua
configure:19537: result: /usr/bin/lua
configure:19558: checking for lua >= 5.0
configure:19570: result: 5.1 found
configure:19578: checking lua-5.1.5/src/lua.h usability
configure:19578:
    /home/matt/dev/rrdtool/cpibuildroot/output/host/usr/bin/arm-linux-gnueabihf-gcc
    -c
    -D_LARGEFILE_SOURCE
    -D_LARGEFILE64_SOURCE
    -D_FILE_OFFSET_BITS=64
    -Os
    -D_GNU_SOURCE
    -fno-strict-aliasing
    -Wall
    -std=gnu99
    -pedantic
    -Wundef
    -Wshadow
    -Wpointer-arith
    -Wcast-align
    -Wmissing-prototypes
    -Wmissing-declarations
    -Wnested-externs
    -Winline
    -Wold-style-definition
    -W
    -D_LARGEFILE_SOURCE
    -D_LARGEFILE64_SOURCE
    -D_FILE_OFFSET_BITS=64
    -I/home/matt/dev/rrdtool/cpibuildroot/output/host/usr/arm-buildroot-linux-gnueabihf/sysroot/usr/include/glib-2.0
    -I/home/matt/dev/rrdtool/cpibuildroot/output/host/usr/arm-buildroot-linux-gnueabihf/sysroot/usr/lib/glib-2.0/include
    -I/home/matt/dev/rrdtool/cpibuildroot/output/host/usr/arm-buildroot-linux-gnueabihf/sysroot/usr/include
    -I/home/matt/dev/rrdtool/cpibuildroot/output/host/usr/arm-buildroot-linux-gnueabihf/sysroot/usr/include/pango-1.0
    -I/home/matt/dev/rrdtool/cpibuildroot/output/host/usr/arm-buildroot-linux-gnueabihf/sysroot/usr/include/glib-2.0
    -I/home/matt/dev/rrdtool/cpibuildroot/output/host/usr/arm-buildroot-linux-gnueabihf/sysroot/usr/lib/glib-2.0/include
    -I/home/matt/dev/rrdtool/cpibuildroot/output/host/usr/arm-buildroot-linux-gnueabihf/sysroot/usr/include
    -I/home/matt/dev/rrdtool/cpibuildroot/output/host/usr/arm-buildroot-linux-gnueabihf/sysroot/usr/include/cairo
    -I/home/matt/dev/rrdtool/cpibuildroot/output/host/usr/arm-buildroot-linux-gnueabihf/sysroot/usr/include/pixman-1
    -I/home/matt/dev/rrdtool/cpibuildroot/output/host/usr/arm-buildroot-linux-gnueabihf/sysroot/usr/include/freetype2
    -I/home/matt/dev/rrdtool/cpibuildroot/output/host/usr/arm-buildroot-linux-gnueabihf/sysroot/usr/include/libpng16
    -I/home/matt/dev/rrdtool/cpibuildroot/output/host/usr/arm-buildroot-linux-gnueabihf/sysroot/usr/include/harfbuzz
    conftest.c >&5
conftest.c:180:31: fatal error: lua-5.1.5/src/lua.h: No such file or directory
compilation terminated.

