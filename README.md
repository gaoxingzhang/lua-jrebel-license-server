
## 介绍(introduce)

Jrebel & Jet Brains License Server for Lua(support Jrebel,JRebel for Android,XRebel Local,JetBrains Products)
Lua 版的 Jrebel 和 Jet Brains 授权服务器(支持 Jrebel,Jrebel for Android,Xrebel Local,JetBrains Products)

## 鸣谢(Thanks)

Thanks for [ilanyu](http://blog.lanyus.com) and [gsls200808](https://gitee.com/gsls200808)
NOTE: This is provided for educational purposes only. Please support genuine.

非常感谢 [ilanyu](http://blog.lanyus.com) 和 [gsls200808](https://gitee.com/gsls200808) (本项目逻辑部分全部移植自https://gitee.com/gsls200808/JrebelLicenseServerforJava ,本项目只做了java to lua工作)
注意： 本项目仅适用于教育用途，请支持正版

## 依赖(Prerequisites)

[install openresty](https://openresty.org/en/installation.html)
[安装openresty](https://openresty.org/cn/installation.html)

download [doujiang24/lua-resty-rsa](https://github.com/doujiang24/lua-resty-rsa) from github raw server(because opm.openresty.org's version(v0.02) is too low )
从github 上下载最新的[doujiang24/lua-resty-rsa](https://github.com/doujiang24/lua-resty-rsa)代码(需要v0.04以上)

```bash
wget -P /path/to/lualib/resty/ https://raw.githubusercontent.com/doujiang24/lua-resty-rsa/master/lib/resty/rsa.lua
```

## 安装(Install)


```bash
# opm get anjia0532/lua-jrebel-license-server fail upload to opm server -_- 
wget -P /path/to/lualib/resty/ https://raw.githubusercontent.com/anjia0532/lua-jrebel-license-server/master/lib/resty/jrebel-license.lua
```

## 用法(Synopsis)
```nginx
  -- nginx.conf

  lua_package_path "/path/to/lualib/?.lua;;"; -- include resty/rsa.lua resty/jrebel-license.lua

  server {
    location = / {
      content_by_lua_block{
        local cjson = require 'cjson'
        local jrebel = require 'jrebel-license.lua'
        ngx.print(jrebel.handler())
      }
    }
  }
```

JetBrains Activation address was: $scheme://$host[:$port]/
JetBrains 产品激活地址: $scheme://$host[:$port]/   e.g. http://8.8.8.8/  (不支持localhost激活)

JRebel 7.1 and earlier version Activation address was: $scheme://$host[:$port]/{tokenname}, with any email.
JRebel 7.1 以及更早的版本激活地址 $scheme://$host[:$port]/{tokenname} 以及任意的email地址(可以是不存在的)

JRebel 2018.1 and later version Activation address was: $scheme://$host[:$port]/{guid}(eg:$scheme://$host[:$port]/dd5f6ce0-8ed9-11e8-9eb6-529269fb1459), with any email.
JRebel 2018.1 以及更高版本激活地址 $scheme://$host[:$port]/{guid} 例如 http://8.8.8.8/dd5f6ce0-8ed9-11e8-9eb6-529269fb1459 以及任意的email地址 （uuid在线生成 https://www.uuidgenerator.net/）

## 支持产品(Support)

- [Jrebel](https://zeroturnaround.com/software/jrebel/)
- [JRebel for Android](https://zeroturnaround.com/software/jrebel-for-android/)
- [XRebel Local](https://zeroturnaround.com/software/xrebel/)
- [JetBrains Products](https://www.jetbrains.com/)

## 注意事项(Note)

This is provided for educational purposes only. Please support genuine.
非常感谢 [ilanyu](http://blog.lanyus.com) 和 [gsls200808](https://gitee.com/gsls200808) (本项目逻辑部分全部移植自https://gitee.com/gsls200808/JrebelLicenseServerforJava ,本项目只做了java to lua工作)

## 反馈(Feedback)

如果有问题，欢迎提 [issues][]

Copyright and License
=====================

This module is licensed under the BSD license.

Copyright (C) 2017-, by AnJia <anjia0532@gmail.com>.

All rights reserved.

Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:

* Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.

* Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

[issues]: https://github.com/anjia0532/lua-jrebel-license-server/issues/new
