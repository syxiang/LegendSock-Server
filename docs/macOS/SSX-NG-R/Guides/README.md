# SSX-NG-R

> 最后更新时间：{docsify-updated}

---

### 此文档中的系统环境 {docsify-ignore}

?> macOS High Sierra 10.13.4 Beta (17E139j)  
SSX-NG-R 1.4.3-R8(2)

---

### 安装 SSX-NG-R

!> 以下操作将可能需要使用终端

从[这里](https://cdn.rixcloud.io/download/ShadowsocksX-NG-R8.dmg)下载 SSX-NG-R。

在 Finder 中双击 SSX-NG-R 打开宗卷，然后用 Finder 打开「应用程序」目录。

![Finder - 应用程序](https://rixcloud-1255365801.file.myqcloud.com/image/pe26t.png)

在 SSX-NG-R 的宗卷中，用鼠标将 SSX-NG-R 拖动到 Finder 的应用程序目录。

![安装 SSX-NG-R](https://rixcloud-1255365801.file.myqcloud.com/image/ec6iv.png)

由于 SSX-NG-R 是未经 Apple 签名的应用程序，因此 macOS 可能会阻止运行此程序。

打开「系统偏好设置」-「安全性与隐私」，可以查看到你的 macOS 可能仅允许使用来自 App Store 或受信任开发者的应用程序。

![安全性与隐私设置](https://rixcloud-1255365801.file.myqcloud.com/image/jfntg.png)

打开「终端」。

![终端](https://rixcloud-1255365801.file.myqcloud.com/image/qigzs.png)

在终端的窗口中输入如下指令，并按下回车键。

```
sudo spctl --master-disable
```

由于申请了 sudo 权限，需要输入你当前账户的密码，在 Shell 中输入密码是不可见的，只需要输入密码后按下回车即可。

再次访问「安全性与隐私」页面，将可以看到你的 macOS 已经允许「任何来源」的应用程序运行。

![任何来源](https://rixcloud-1255365801.file.myqcloud.com/image/jgkvg.png)

---

### 检查 rixCloud 订阅的设置

!> SSX-NG-R 完全支持 SSR 协议

如果不需要使用 Surge 等软件，建议将订阅协议组设置为不带有「兼容」字样的协议（混淆插件除外）。

访问 rixCloud 管理门户，点击已经激活的订阅进入订阅管理页面。然后点击「订阅设置」按钮即可修改。

![订阅设置](https://rixcloud-1255365801.file.myqcloud.com/image/8plkh.png)

---

### 通过 API 订阅配置

##### 获取 rixCloud API 订阅

打开 rixCloud 管理门户，点击订阅名称进入订阅信息管理页面。在「自动配置」功能区找到桌面平台 - 「节点订阅」。

![rixCloud API 订阅](https://rixcloud-1255365801.file.myqcloud.com/image/6tib7.png)

点击按钮后会弹出新的窗口，在新的窗口中点击「普通模式」。

![rixCloud API 订阅模式](https://rixcloud-1255365801.file.myqcloud.com/image/p467g.png)

按钮上的文字应当在点击后变成「已经复制到剪贴板」，说明 rixCloud API URI 已经复制到你计算机的剪贴板中。

!> 这个 API URI 非常重要，你应当把它当做密码一样妥善保管，避免泄露。

![复制 API URI 到剪贴板](https://rixcloud-1255365801.file.myqcloud.com/image/kh4at.png)

---

### 配置 SSX-NG-R

打开 SSX-NG-R，打开后将会在状态栏上出现一个灰色的纸飞机图标。

![SSX-NG-R 图标](https://rixcloud-1255365801.file.myqcloud.com/image/vkzcr.png)

点击此图标，选择「服务器」-「编辑订阅」。

![编辑订阅](https://rixcloud-1255365801.file.myqcloud.com/image/hv053.png)

在新的「订阅设置」窗口中点击 `+` 号，然后将刚才复制的 rixCloud API URI 粘贴到「订阅地址」一栏上。点击「OK」

![创建新订阅](https://rixcloud-1255365801.file.myqcloud.com/image/lgpdu.png)

再次点击 SSX-NG-R 的图标，如图所示勾选「打开时自动更新订阅」并点击「手动更新订阅」。

![手动更新订阅](https://rixcloud-1255365801.file.myqcloud.com/image/yv6nz.png)

如果一切顺利，将会收到通知消息提示订阅更新成功。

![订阅更新成功](https://rixcloud-1255365801.file.myqcloud.com/image/k46yv.png)

在服务器分组中选择需要的接入点。

![选择接入点](https://rixcloud-1255365801.file.myqcloud.com/image/stlsx.png)

选择所需的代理模式，然后点击「打开 Shadowsocks」即可。

![打开 SSX-NG-R](https://rixcloud-1255365801.file.myqcloud.com/image/i3a48.png)

---

### 为 Shell 设置代理

如果需要在终端中使用，则需要单独进行设置。

首先查看 SSX-NG-R 当前将本地代理工作在哪个端口。

在已经开启 SSX-NG-R 并启用系统代理时，打开「系统偏好设置」-「网络」，选择当前使用的网络设备，点击「高级」。

点击「代理」选项卡，其中的 HTTP / HTTPS / SOCKS 代理应当已经被勾选。我们需要查看他们的端口。

![查看代理端口](https://rixcloud-1255365801.file.myqcloud.com/image/5geaj.png)

在本例中，SSX-NG-R 的 HTTP/HTTPS 代理工作在 `1087` 端口，SOCKS 5 代理工作在 `1086` 端口。

打开终端，在 Shell 中键入如下指令：

```
export https_proxy=http://127.0.0.1:1087;export http_proxy=http://127.0.0.1:1087;export all_proxy=socks5://127.0.0.1:1086
```

此时 Shell 已经设置为通过 SSX-NG-R 进行代理，可以通过以下指令来检测：

```
curl ip.sb
```

查看 IP 地址是否为 rixCloud 接入点的出口 IP 地址。

