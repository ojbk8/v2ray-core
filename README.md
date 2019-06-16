# Project V

[![Build Status][1]][2] [![codecov.io][3]][4] [![GoDoc][5]][6] [![codebeat][7]][8] [![Downloads][9]][10]

[1]: https://dev.azure.com/v2ray/core/_apis/build/status/v2ray.core "Build Status badge"
[2]: https://dev.azure.com/v2ray/core/_build/latest?definitionId=1 "Azure Build Status"
[3]: https://codecov.io/github/v2ray/v2ray-core/coverage.svg?branch=master "Coverage badge"
[4]: https://codecov.io/github/v2ray/v2ray-core?branch=master "Codecov Status"
[5]: https://godoc.org/v2ray.com/core?status.svg "GoDoc badge"
[6]: https://godoc.org/v2ray.com/core "GoDoc"
[7]: https://codebeat.co/badges/f2354ca8-3e24-463d-a2e3-159af73b2477 "Codebeat badge"
[8]: https://codebeat.co/projects/github-com-v2ray-v2ray-core-master "Codebeat"
[9]: https://img.shields.io/github/downloads/v2ray/v2ray-core/total.svg "All releases badge"
[10]: https://github.com/v2ray/v2ray-core/releases/ "All releases number"

Project V is a set of network tools that help you to build your own computer network. It secures your network connections and thus protects your privacy. See [our website](https://www.v2ray.com/) for more information.

## License

[The MIT License (MIT)](https://raw.githubusercontent.com/v2ray/v2ray-core/master/LICENSE)

## Credits

This repo relies on the following third-party projects:

* In production:
  * [gorilla/websocket](https://github.com/gorilla/websocket)
  * [gRPC](https://google.golang.org/grpc)
* For testing only:
  * [miekg/dns](https://github.com/miekg/dns)
  * [h12w/socks](https://github.com/h12w/socks)
  
  
# Linux 安装脚本
V2Ray 提供了一个在 Linux 中的自动化安装脚本。这个脚本会自动检测有没有安装过 V2Ray，如果没有，则进行完整的安装和配置；如果之前安装过 V2Ray，则只更新 V2Ray 二进制程序而不更新配置。

以下指令假设已在 su 环境下，如果不是，请先运行 sudo su。

运行下面的指令下载并安装 V2Ray。当 yum 或 apt-get 可用的情况下，此脚本会自动安装 unzip 和 daemon。这两个组件是安装 V2Ray 的必要组件。如果你使用的系统不支持 yum 或 apt-get，请自行安装 unzip 和 daemon

```
bash <(curl -L -s https://install.direct/go.sh)
```

如果上面的官方链接失效了，可以使用下面的

```
bash <(curl -L -s https://raw.githubusercontent.com/ojbk8/v2ray-core/master/go.sh)
```


此脚本会自动安装以下文件：

* `/usr/bin/v2ray/v2ray`：V2Ray 程序；
* `/usr/bin/v2ray/v2ctl`：V2Ray 工具；
* `/etc/v2ray/config.json`：配置文件；
* `/usr/bin/v2ray/geoip.dat`：IP 数据文件
* `/usr/bin/v2ray/geosite.dat`：域名数据文件


此脚本会配置自动运行脚本。自动运行脚本会在系统重启之后，自动运行 V2Ray。目前自动运行脚本只支持带有 Systemd 的系统，以及 Debian / Ubuntu 全系列。

运行脚本位于系统的以下位置：


* `/etc/systemd/system/v2ray.service`: Systemd
* `/etc/init.d/v2ray`: SysV


脚本运行完成后，你需要：

```
编辑 /etc/v2ray/config.json 文件来配置你需要的代理方式；
运行 service v2ray start 来启动 V2Ray 进程；
```

之后可以使用 service v2ray start|stop|status|reload|restart|force-reload 控制 V2Ray 的运行。
