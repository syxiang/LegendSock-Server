# Koolshare Modified ROM

> 最后更新时间：{docsify-updated}

!> 我们仅在特定平台和版本上进行过测试，并以此撰写文档

> 此软件更新较为频繁且有多个版本，文档中的部分内容可能和实际存在差异。

---

### 此文档中的系统环境 {docsify-ignore}

?> ASUS GT-AC5300  
Koolshare Modified ROM 3.0.0.4.382_15984_koolshare  
KoolSS 1.1.6(Merlin)

---

### 注意事项

由于使用 Koolshare Modified ROM（改版固件）的太多是普通家用路由器，其使用的 CPU 大都为 MIPS 或 ARMv7 架构，其性能可能不足，因此使用 KoolSS 可能无法达到较高速率。

目前经过 rixCloud 和 Koolshare 的测试，以下两款路由器使用 Koolshare Modified ROM 的 KoolSS 后可基本达到 200Mbps 的速率：

> ASUS GT-AC5300
> 
> ASUS RT-AC86U

如果想要在路由器上达到较高 SS 连接速率，请考虑购买以上两款路由器或购买软路由使用 LEDE

以下是各常见路由型号使用 KoolSS 的大致连接速率：

我们会根据收集到的数据不断更新此表格，但用户提供的数据本身未经验证，仅供参考。你也可以提供你的测试数据，以便协助我们完善此内容。


| 型号 | 数据提供方 | 品牌 | 大致连接速率 |
| :-- | :-: |:-: | :-: |
| R6300v2 | rixCloud | NETGEAR | 60Mbps |
| R6400 | rixCloud | NETGEAR | 30Mbps |
| R6900 | rixCloud | NETGEAR | 60Mbps |
| R7000 | rixCloud | NETGEAR | 80Mbps |
| R8000 | rixCloud | NETGEAR |  未经测试  |
| R8500 | rixCloud | NETGEAR | 110Mbps |
| RT-N66U | rixCloud | ASUS |  未经测试 |
| RT-AC56U | rixCloud | ASUS | 20Mbps |
| RT-AC66U | rixCloud | ASUS | 30Mbps |
| RT-AC68U | rixCloud | ASUS | 70Mbps |
| RT-AC87U | rixCloud | ASUS | 70Mbps |
| RT-AC88U | rixCloud | ASUS | 100Mbps |
| RT-AC86U | rixCloud | ASUS | 200Mbps |
| RT-AC1900P | rixCloud | ASUS | 70Mbps |
| RT-AC3100 | rixCloud | ASUS |  未经测试 |
| RT-AC3200 | rixCloud | ASUS |  未经测试 |
| RT-AC66U-B1 | rixCloud | ASUS | 50Mbps |
| RT-AC5300 | rixCloud | ASUS | 120Mbps |
| GT-AC5300 | rixCloud | 玩家国度 | 250Mbps |
| EA6200 | rixCloud | Linksys |  未经测试 |
| EA6400 | rixCloud | Linksys |  未经测试 |
| EA6700 | rixCloud | Linksys |  未经测试 |
| EA6500v2 | rixCloud | Linksys |  未经测试  |
| EA6900 | rixCloud | Linksys |  未经测试 |
| WRT1900ACS | rixCloud | Linksys | 120Mbps |

（数据提供方表明此数据是通过何种渠道收集的）

!> 以上测试仅供参考，不同服务配置的情况下数值可能存在差异

（感谢[这些](/Routers/Merlin/Acknowledgment-list/)用户为我们提供数据）

点击[这里](https://goo.gl/forms/4dZQy8D5WZbyff2S2)可以协助我们完善以上的表格。

---

### 从软件中心安装 KoolSS

!> 安装前可能有额外操作

Koolshare Modified ROM 在使用软件中心前需要先清空并格式化 JFFS2 分区，由于此不属于我们文档应当包含的一部分，因此阁下需要自行前往 Koolshare 社区了解不同机型的不同清除方法。

---

通过浏览器访问 Koolshare Modified ROM（改版固件） 管理页面。

!> 由于 Koolshare Modified ROM 的页面存在一些兼容性问题，建议使用 Google Chrome 浏览器

在管理页面底部点击「软件中心」，然后点击「未安装」选项卡，然后点击「科学上网」插件来安装。

![安装 KoolSS](https://rixcloud-1255365801.file.myqcloud.com/image/kl1m4.png)

页面会提示正在安装。

![正在安装中](https://rixcloud-1255365801.file.myqcloud.com/image/dx00y.png)

如果安装完成，页面会自动跳转，并可以在「已安装」选项卡下看到此插件。

![安装完成](https://rixcloud-1255365801.file.myqcloud.com/image/spv3m.png)

### 检查 rixCloud 订阅的设置

!> KoolSS 完全支持 SSR 协议

如果不需要使用 Surge 等软件，建议将订阅协议组设置为不带有「兼容」字样的协议（混淆插件除外）。

访问 rixCloud 管理门户，点击已经激活的订阅进入订阅管理页面。然后点击「订阅设置」按钮即可修改。

![订阅设置](https://rixcloud-1255365801.file.myqcloud.com/image/8plkh.png)

---

### 获取 rixCloud API 订阅

打开 rixCloud 管理门户，点击订阅名称进入订阅信息管理页面。在「自动配置」功能区找到桌面平台 - 「节点订阅」。

![rixCloud API 订阅](https://rixcloud-1255365801.file.myqcloud.com/image/6tib7.png)

点击按钮后会弹出新的窗口，在新的窗口中点击「普通模式」。

![rixCloud API 订阅模式](https://rixcloud-1255365801.file.myqcloud.com/image/p467g.png)

按钮上的文字应当在点击后变成「已经复制到剪贴板」，说明 rixCloud API URI 已经复制到你计算机的剪贴板中。

!> 这个 API URI 非常重要，你应当把它当做密码一样妥善保管，避免泄露。

![复制 API URI 到剪贴板](https://rixcloud-1255365801.file.myqcloud.com/image/kh4at.png)

---

### 配置 KoolSS

点击「已安装」选项卡中的「科学上网」插件进入插件管理页面。

如果是第一次使用此插件，则可能弹出此会话框：

![首次使用提示](https://rixcloud-1255365801.file.myqcloud.com/image/xw3x7.png)

点击「订阅节点」按钮进入更新管理页面。

如果没有弹出此会话框，则手动打开 KoolSS 开关并点击「更新管理」选项卡。

![更新管理页面](https://rixcloud-1255365801.file.myqcloud.com/image/4t8kw.png)

进入「更新管理」页面后，滑动页面到下方的「SSR 订阅设置」区域。

![SSR 订阅设置](https://rixcloud-1255365801.file.myqcloud.com/image/c6y24.png)

在「订阅地址管理」中粘贴我们之前复制的 rixCloud API URI，然后进行如下设定

> 将「订阅节点模式设定」设置为「游戏模式」
> 
> 将「订阅节点混淆参数设定」设置为「使用订阅设定」
> 
> 将「下载订阅时走 SS 网络」设置为「不走 SS」
> 
> 开启「订阅计划任务」，并选择一个你可能不会使用网络的时间。

设置完成后，点击「保存并订阅」按钮。页面会打开一个新的提示框并出现类似下图中的内容：

![正在进行订阅](https://rixcloud-1255365801.file.myqcloud.com/image/afxde.png)

订阅完成后，页面会自动跳转到主页面，此时 KoolSS 的开关可能将会再次出于关闭状态，点击开关来打开它。

![打开 KoolSS 开关](https://rixcloud-1255365801.file.myqcloud.com/image/25eg5.png)

---

### 附加设置

为了使我们的使用更加舒适，我们需要进行一些附加设置。

点击「更新管理」选项卡，将「规则定时更新任务」设置为「开启」，然后选择一个你可能不会使用网络的时间段。并将所有规则的更新全部勾选，然后点击「保存设置」。

![开启规则更新](https://rixcloud-1255365801.file.myqcloud.com/image/7pfas.png)

页面将会自动跳转，完成后应当再次返回此页面，然后点击「立即更新」。以确保 KoolSS 已经获取到最新的规则。

点击「DNS 设定」选项卡，然后进行以下设定：

> 将选择国内 DNS 设置为运营商 DNS，如果你的运营商 DNS 存在劫持，则可以使用 `119.29.29.29` 或自定义设置为 `119.28.28.28`
> 
> 将「选择国外 DNS」设置为 `ss-tunnel`，然后设置你喜欢的国外公共 DNS 服务提供商

![DNS 设定](https://rixcloud-1255365801.file.myqcloud.com/image/1z7ik.png)

---

### 开启 KoolSS

完成附加设置后，点击「账号设置」选项卡，选择需要的接入点，然后点击底部的「提交」按钮。KoolSS 将会启动。

一段时间后，页面将会自动刷新并返回到账号设置页面，此时 KoolSS 会自动检测状态，如果国内国外均为 OK 状态即可正常使用。

![KoolSS 已经正常运行](https://rixcloud-1255365801.file.myqcloud.com/image/wxhxb.png)

!> 某些情况下，显示连接错误并非未能连接上，而是可能的测试失败，请实际使用浏览器打开网页测试。

