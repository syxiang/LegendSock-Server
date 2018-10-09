通过 Cloudflared 使用 DNS over HTTPS（DoH）

> 最后更新时间：{docsify-updated}

---

# 概述

由于中国大陆内存在 DNS 缓存投毒，通过常规方式使用 DNS 会导致某些域名不能被正常解析。DNSSec 曾经是被寄予厚望来解决 DNS 缓存投毒的方案，然而事实证明并没有什么效果。

既然走标准 DNS 协议会被污染，那最简单的方案就是在公网内走非常规的 DNS 查询方法，并且把 DNS 查询内容加密，自然也就规避了 ISP 的 DNS 劫持和防火墙的 DNS 缓存投毒。

目前主流的方法主要是 DNS over HTTPS（DoH）和 DNS over TLS（DoT），本文档介绍第一种方案。

支持 DNS over HTTPS 的 DNS 程序非常多，然而大部分主要用于在核心路由器上甚至公网上提供 DNS 服务，如果你只是简单地在局域网环境使用，则使用 Cloudflare 提供的 Cloudflared 程序就可以轻松完成部署。

---

# Windows

### 此文档中的系统环境 {docsify-ignore}

?> Windows 10 Pro for Workstations / 1804. Build 17134.1

首先需要下载 Cloudflared 二进制文件

[32 位系统](https://bin.equinox.io/c/VdrWdbjqyF/cloudflared-stable-windows-386.zip)

[64 位系统](https://bin.equinox.io/c/VdrWdbjqyF/cloudflared-stable-windows-amd64.zip)

解压缩后放到任意位置，如我们放到 I 盘的 Cloudflare 文件夹中。

![](https://rixcloud-1255365801.file.myqcloud.com/image/olafx.png)

在左下角的 Windows 徽标按钮上右键单击，选择「Windows PowerShell（管理员）」，并在弹出的 UAC 授权提示框（如果有）中允许 PowerShell 使用管理员权限。

![](https://rixcloud-1255365801.file.myqcloud.com/image/rbtat.png)

定位到 `I:\Cloudflare` 目录。

![](https://rixcloud-1255365801.file.myqcloud.com/image/791b3.png)

以 DNS 代理模式运行 Cloudflared

![](https://rixcloud-1255365801.file.myqcloud.com/image/tg9om.png)

这时我们已经成功通过 Cloudflared 隧道程序以 HTTPS 方式连接到了 Cloudflare 提供的 DNS。

由于 Cloudflared 自身以 CLI（Command Lines）方式运行时不会以 Daemon 方式运行，我们需要通过 PowerShell 的功能来让它在后台运行。

输入命令（你需要自行修改命令中的路径）：

```
powershell -windowstyle hidden -command "I:\Cloudflare\cloudflared.exe proxy-dns"
```

!> 某些安全软件可能会拦截以后台静默运行的程序，请允许 Cloudflared.exe 和 PowerShell 这么做

![](https://rixcloud-1255365801.file.myqcloud.com/image/jmrkh.png)

可以看到 PowerShell 窗口一闪而过，我们通过 `nslookup` 测试一下。

![](https://rixcloud-1255365801.file.myqcloud.com/image/u8jc9.png)

测试可以了解到，Cloudflared 仍然在正常运行，并提供着 DNS 代理服务。现在，只需要修改网络适配器中的 DNS 服务器地址为 `127.0.0.1` 就可以使用了。

将这个 PowerShell 设置为开机运行，就可以实现开机启动 Cloudflared 并运行 DNS 代理服务。

 Windows 也可以将 Cloudflared 设置为系统服务来开机运行 Cloudflared，请参考[官方文档](https://developers.cloudflare.com/argo-tunnel/reference/service/)
 
 ---

# macOS

### 此文档中的系统环境 {docsify-ignore}

?> macOS 10.13.5 Beta / Build 17F45c

macOS 系统可以通过包管理器或二进制安装 Cloudflared。

要安装 Homebrew（包管理器），你可以参考 Homebrew 的[官方网站]()或直接在终端中输入：

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

已经安装 Homebrew 后，在终端中输入：

```
brew install cloudflare/cloudflare/cloudflared
```

也可以直接使用二进制文件安装：

```
curl https://bin.equinox.io/c/VdrWdbjqyF/cloudflared-stable-darwin-amd64.tgz | tar xzC /usr/local/bin
```

---

安装后直接在终端输入 `sudo cloudflared proxy-dns` 即可运行 Cloudflared 的 DNS 代理功能。

Cloudflared 以 DNS 代理模式运行时需要监听 53 端口，因此必须提权到 Root 用户才能运行。

![](https://rixcloud-1255365801.file.myqcloud.com/image/5z51t.png)

要在后台运行 Cloudflared，官方方法是将 Cloudflared 设置为服务。

要设置 Cloudflared 为服务，你必须拥有一个 Cloudflare 账户并在至少一个域中购买了 Argo 增值服务。

![](https://rixcloud-1255365801.file.myqcloud.com/image/hs5zh.png)

因此，详细的设置方法请参考[官方文档](https://developers.cloudflare.com/argo-tunnel/reference/service/)

macOS 也可以自行编写脚本来开机运行 Cloudflared，但是由于 macOS 是类 UNIX 系统且权限控制较为严格，此文档没有足够篇幅和必要介绍此种方法。

---

# Linux

### 此文档中的系统环境 {docsify-ignore}

?> Rad Hat Enterprise Linux 7.4  
Ubuntu 18.04 LTS

Linux 发行版可以通过包管理器安装或二进制安装。

[二进制文件 x86-64](https://bin.equinox.io/c/VdrWdbjqyF/cloudflared-stable-linux-amd64.tgz) | [二进制文件 ARMv6](https://bin.equinox.io/c/VdrWdbjqyF/cloudflared-stable-linux-arm.tgz)

[.deb 包 x86-64](https://bin.equinox.io/c/VdrWdbjqyF/cloudflared-stable-linux-amd64.deb) | [.deb 包 ARMv6](https://bin.equinox.io/c/VdrWdbjqyF/cloudflared-stable-linux-arm.deb)

[.rpm 包 x86-64](https://bin.equinox.io/c/VdrWdbjqyF/cloudflared-stable-linux-amd64.rpm) | [.rpm 包 ARMv6](https://bin.equinox.io/c/VdrWdbjqyF/cloudflared-stable-linux-arm.rpm)

---

二进制文件可以直接安装到 `/usr/bin` 等目录，安装后，输入 `sudo cloudflared proxy-dns` 就可以使用，可以部署到路由器上供网关下的设备使用。

Cloudflared 以 DNS 代理模式运行时需要监听 53 端口，因此必须提权到 Root 用户才能运行。如果已经是 Root 用户，直接运行即可。

可以在 screen 中运行 Cloudflared 以变相达成后台运行，或者自行编写 SystemInitV / Systemd 脚本来开机运行。

