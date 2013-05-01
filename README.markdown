Name
====

lua-resty-core - New FFI-based Lua API for the ngx_lua module

Status
======

This library is still under early development and is still incomplete.

Synopsis
========

    # nginx.conf

    http {
        lua_package_path "/path/to/lua-resty-core/lib/?.lua;;";

        init_by_lua '
            require "resty.core"
        ';

        ...
    }

Description
===========

This pure Lua library reimplements part of the ngx_lua's
[Nginx API for Lua](http://wiki.nginx.org/HttpLuaModule#Nginx_API_for_Lua)
with LuaJIT FFI and installs the new FFI-based Lua API into the ngx.* and ndk.* namespaces
used by the ngx_lua module.

The FFI-based Lua API can work with LuaJIT's JIT compiler. ngx_lua's default API is based on the standard Lua C API, which will never be JIT compiled and the user Lua code is always interpreted (slowly).

Prerequisites
=============

* LuaJIT 2.1 (for now, it is the v2.1 git branch in the official luajit-2.0 git repository: http://luajit.org/download.html )
* The "ffi" git branch in the lua-nginx-module repository on GitHub: https://github.com/chaoslawful/lua-nginx-module

API Implemented
===============

### resty.core.hash

* [ngx.md5](http://wiki.nginx.org/HttpLuaModule#ngx.md5)
* [ngx.md5_bin](http://wiki.nginx.org/HttpLuaModule#ngx.md5_bin)
* [ngx.sha1_bin](http://wiki.nginx.org/HttpLuaModule#ngx.sha1_bin)

Author
======

Yichun "agentzh" Zhang (章亦春) <agentzh@gmail.com>

Copyright and License
=====================

This module is licensed under the BSD license.

Copyright (C) 2013, by Yichun "agentzh" Zhang, CloudFlare Inc.

All rights reserved.

Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:

* Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.

* Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

See Also
========
* the ngx_lua module: http://wiki.nginx.org/HttpLuaModule
* LuaJIT FFI: http://luajit.org/ext_ffi.html
