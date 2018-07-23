 ShadowsocksR for Android

> 最后更新时间：{docsify-updated}

---

### 此文档中的系统环境 {docsify-ignore}

?> Samsung SM-G9650/DS  
Android 8.0.0 / Samsung Experience 9.0  
ShadowsocksR 3.4.0.7.1 (rixCloud Mod)

---

### 获取 rixCloud API 订阅

打开 rixCloud 管理门户，点击订阅名称进入订阅信息管理页面。在「自动配置」功能区找到桌面平台 - 「节点订阅」。

![rixCloud API 订阅](https://rixcloud-1255365801.file.myqcloud.com/image/zvi52.jpg)

在弹出的窗口中选择「普通模式」，按下按钮，如果按钮文字变为「已复制到剪贴板」，则说明 rixCloud API URI 已经复制。

!> 这个 API URI 非常重要，你应当把它当做密码一样妥善保管，避免泄露。

![已复制到剪贴板](https://rixcloud-1255365801.file.myqcloud.com/image/3ku6d.jpg)

---

### 配置 ShadowsocksR

你可以点击[这里](https://cdn.rixcloud.io/download/ShadowsocksR.apk)下载 ShadowsocksR for Android。

![rixCloud Mod 版 ShadowsocksR](https://rixcloud-1255365801.file.myqcloud.com/image/uyiox.jpg)

进入程序后点击顶部的「ShadowsocksR」图标，进入配置文件管理页面，然后点击右下角的「+」，在弹出的选项中选择「添加/升级 SSR 订阅」。

![添加 rixCloud 订阅](https://rixcloud-1255365801.file.myqcloud.com/image/i1k1d.jpg)

在弹出的菜单中选择「添加订阅地址」，在新窗口中粘贴之前从 rixCloud 管理门户获取的 API URI。

!> 这个 API URI 非常重要，你应当把它当做密码一样妥善保管，避免泄露。

![粘贴 API URI](https://rixcloud-1255365801.file.myqcloud.com/image/3p5a8.jpg)

添加完成后会自动返回到之前的菜单，打开「自动更新」然后点击「确定并升级」。

![更新 rixCloud 订阅](https://rixcloud-1255365801.file.myqcloud.com/image/7otpr.jpg)

软件会自动访问 rixCloud RESTful API 并获取相应的数据，成功后应当如图所示：

![节点列表](https://rixcloud-1255365801.file.myqcloud.com/image/z6qwa.jpg)

添加完成后，返回到主界面，然后点击右上角的纸飞机图标开启。初次使用时会弹出提醒询问是否允许添加 VPN 连接，点击「确定」即可。

![添加 VPN 连接](https://rixcloud-1255365801.file.myqcloud.com/image/3p1bi.jpg)

---

### 易用性设置

为了方便你的使用，我们推荐按如下配置来设置你的 ShadowsocksR 客户端。

在「功能设置」区域的「路由」选择中，点击并从下拉菜单中选择「自定义 ACL 文件」，然后根据需求添加以下地址中的任意一个：

大陆白名单模式（大陆网站/应用直连，其他默认走代理） + 过滤常见广告：

`https://cdn.rixcloud.io/resource/rules/Android/ACL/banAD.acl`

[或长按此处复制 URL](https://cdn.rixcloud.io/resource/rules/Android/ACL/banAD.acl)

大陆白名单模式：

`https://cdn.rixcloud.io/resource/rules/Android/ACL/nobanAD.acl`

[或长按此处复制 URL](https://cdn.rixcloud.io/resource/rules/Android/ACL/banAD.acl)

然后打开「IPv6 路由」和「UDP 转发」的选项卡。

IPv6 路由可以使得你在使用特定受支持的 rixCloud 接入点时，可以使用 IPv6 网络访问互联网而无需你本地有 IPv6 网络。

UDP 转发可以满足某些应用程序的连接需求。

设置「China DNS」为：

`119.28.28.28:53,119.29.29.29:53,1.2.4.8:53`

设置「DNS」为：

`1.1.1.1:53`

最终效果为

![优化设置](https://rixcloud-1255365801.file.myqcloud.com/image/jrw6s.jpg)

---

### 设置电池策略

大部分 Android 系统都会因为电池策略导致 ShadowsocksR 应用程序被杀掉导致无法连接网络。出现这种情况的特征是通知栏中 VPN 连接仍然存在，但无法访问网络（包括国内网络）。这是因为 ShadowsocksR 主程序和 VPN 框架是独立存在的，主程序被系统清理后会导致流量仍然通过 VPN 路由到本地但没有应用程序来处理这些流量，导致无法上网。

以 Samsung Experience 9.0 为例，其他第三方系统需要进行类似的设置。

在「常规管理」 - 「电池」 - 「未监视的应用程序」中添加 ShadowsocksR 应用程序（在 rixCloud Mod 版中此应用程序的名称为 rixCloud）。

![设置 ShadowsocksR 不受电池策略影响](https://rixcloud-1255365801.file.myqcloud.com/image/pc2gr.jpg)

在后台中设置「锁定应用程序」并添加 ShadowsocksR 防止被一键清理时误清理掉。

![锁定应用程序](https://rixcloud-1255365801.file.myqcloud.com/image/73w5f.jpg)

此外，由于代理软件的特殊性，可能导致系统将所有因为网络连接而消耗的电量都计算在代理软件上，这是正常情况，并非严重的续航影响。




