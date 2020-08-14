<div align="center">
<img src="https://i.loli.net/2020/02/12/N2jT3DXpIHumiBS.png">
</div>

<h1 align="center">ServerStatus</h1>

<p align="center">
ServerStatus 是一个提供 Web 界面的云探针<br />
实时展示网络连接、CPU、内存、硬盘容量等数据<br />
源于 <a href="https://github.com/ToyoDAdoubi/ServerStatus-Toyo">ServerStatus-Toyo</a>
</p>

<div align="center">
<a href="LICENSE"><img src="https://img.shields.io/github/license/LilligantMatsuri/ServerStatus" alt="LICENSE"></a>
<a href="https://visitor-badge.laobi.icu"><img src="https://visitor-badge.laobi.icu/badge?page_id=LilligantMatsuri.ServerStatus" alt="visitor badge"/></a>
<a href="https://cdn.jsdelivr.net/gh/LilligantMatsuri/ServerStatus@master/"><img src="https://data.jsdelivr.com/v1/package/gh/LilligantMatsuri/ServerStatus/badge?style=rounded" alt="jsDelivr"></a>
</div>

## 截图

![ServerStatus_preview.png](https://i.loli.net/2020/01/31/Iv47fYVSecxUCML.png)

## 安装

### 脚本部署

**v2 (systemd)**

<div>
系统要求：
<a href="https://www.centos.org"><img src="https://img.shields.io/badge/CentOS-%E2%89%A5%207-%23262577?logo=centos" alt="CentOS"></a>
<a href="https://www.debian.org"><img src="https://img.shields.io/badge/Debian-%E2%89%A5%208-%23A81D33?logo=debian" alt="Debian"></a>
<a href="https://ubuntu.com"><img src="https://img.shields.io/badge/Ubuntu-%E2%89%A5%2015.04-%23E95420?logo=ubuntu" alt="Ubuntu"></a>
</div>

```bash
wget https://git.io/statusv2 -O status.sh && chmod +x status.sh && bash status.sh
```

**v1 (init)**

不推荐，除非系统版本不符合上述要求

```bash
wget https://git.io/statusv1 -O status.sh && chmod +x status.sh && bash status.sh
```

运行脚本后将显示如下菜单，根据提示进行操作即可

```bash
  ServerStatus 一键安装管理脚本 [vx.x.x]
-- Author: Toyo | Maintainer: Matsuri --

 0. 升级脚本
————————————
 1. 安装 服务端
 2. 更新 服务端
 3. 卸载 服务端
————————————
 4. 启动 服务端
 5. 停止 服务端
 6. 重启 服务端
————————————
 7. 设置 服务端配置
 8. 查看 服务端信息
 9. 查看 服务端日志
————————————
10. 切换 客户端菜单

当前状态: 服务端 未安装

请输入选项的编号 [0-10]:
```

### 目录结构

ServerStatus 安装路径：/usr/local/ServerStatus

```bash
ServerStatus
    ├─ client
        ├─ status-client.py ........... 客户端程序
    ├─ server
        ├─ config.conf
        ├─ config.json ................ 节点配置文件
        ├─ sergate .................... 服务端程序
    ├─ web
        ├─ css
        ├─ img
        ├─ js
        ├─ json
        ├─ favicon.ico
        ├─ index.html
        ├─ robots.txt
    ├─ jq
```

### 常见问题

#### Q：客户端无法正常运行？

**A**：客户端依赖 Python 2.7 及以上（此分支已兼容 3.x）。CentOS ≤ 6／Debian ≤ 6／Ubuntu ≤ 13.10 的软件包管理器内 Python 版本过低，如果出于某些原因不得不使用这些系统，则需在脚本部署前自行安装符合要求的版本并正确配置（命令 `python -V` 能够输出版本号即可）。

如果客户端成功启动，但服务端依然接收不到数据，请检查是否输入了正确的用户名、密码等信息。

#### Q：终端输入中文显示错误？

**A**：输入的节点名称、位置等含有中文字符时，如果终端模拟器不支持中文编码，将无法正常显示。可以先输入任意内容，然后再修改节点配置文件中相应的字段。修改后，重启服务端才会生效。

#### Q：如何在“位置”一栏添加国旗图标？

**A**：打开节点配置文件，在 “location” 字段添加 `<span class=\\\"flag-icon flag-icon-xx\\\"></span>` （“xx”为二位字母国家地区代码，反斜杠的作用是转义），例如中国国旗 :cn: 为 `flag-icon-cn` 。同样地，修改完毕后需要重启服务端。

更详细的用法请参考 flag-icon-css 的[使用说明](https://github.com/lipis/flag-icon-css#usage)。

## 管理

### 服务端

- 启动：`systemctl start statuss` 或 `service status-server start`

- 停止：`systemctl stop statuss` 或 `service status-server stop`

- 状态：`systemctl status statuss` 或 `service status-server status`

### 客户端

- 启动：`systemctl start statusc` 或 `service status-client start`

- 停止：`systemctl stop statusc` 或 `service status-client stop`

- 状态：`systemctl status statusc` 或 `service status-client status`

## 致谢

此分支只是在 Toyo 所做工作的基础上进行维护，确保它一直可用、易用，并没有多少实质性的改进。

谨向相关开源项目作者表示感谢。

* [Uptime Checker script](https://www.lowendtalk.com/discussion/comment/169690#Comment_169690) by **BlueVM**
* [ServerStatus](https://github.com/mojeda/ServerStatus) by **mojeda**
* [ServerStatus](https://github.com/BotoX/ServerStatus) by **BotoX**
* [ServerStatus-Toyo](https://github.com/ToyoDAdoubi/ServerStatus-Toyo) by **ToyoDAdoubi**
* [ServerStatus](https://github.com/cppla/ServerStatus) by **cppla**
* [flag-icon-css](https://github.com/lipis/flag-icon-css) by **lipis**
* [![jsDelivr](https://www.jsdelivr.com/img/logo-horizontal.svg)](https://www.jsdelivr.com/)
