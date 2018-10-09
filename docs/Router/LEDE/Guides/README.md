# Koolshare LEDE

> 最后更新时间：{docsify-updated}

!> 我们仅在特定平台和版本上进行过测试，并以此撰写文档

> 此软件更新较为频繁且有多个版本，文档中的部分内容可能和实际存在差异。

---

### 此文档中的系统环境 {docsify-ignore}

?> Windows Server 2016 Datacenter  
Hyper-V Hypervisor  
Koolshare LEDE x64 v2.8  
KoolSS (Software center) 1.9.7  

---

### 从软件中心中安装 KoolSS

通过浏览器访问 LEDE 管理页面。

!> 由于 Koolshare LEDE 的页面存在一些兼容性问题，建议使用 Google Chrome 浏览器

点击左侧侧边栏的「酷软」。

![打开软件中心](https://rixcloud-1255365801.file.myqcloud.com/image/3t9vc.png)

在软件中心的「未安装」列表中找到「科学上网插件」，如下图：

![](https://rixcloud-1255365801.file.myqcloud.com/image/ll4ht.png)

> 由于我们已经安装过此插件，因此显示为「更新」

点击插件的「安装」按钮安装，页面将会在安装完成够自动跳转。

---

### 检查 PPXbar 订阅的设置

!> KoolSS 完全支持 SSR 协议

如果不需要使用 Surge 等软件，建议将订阅协议组设置为不带有「兼容」字样的协议（混淆插件除外）。

访问 PPXbar 管理门户，点击已经激活的订阅进入订阅管理页面。然后点击「订阅设置」按钮即可修改。

![订阅设置](https://rixcloud-1255365801.file.myqcloud.com/image/8plkh.png)

---

### 获取 PPXbar API 订阅

打开 PPXbar 管理门户，点击订阅名称进入订阅信息管理页面。在「自动配置」功能区找到桌面平台 - 「节点订阅」。

![PPXbar API 订阅](https://rixcloud-1255365801.file.myqcloud.com/image/6tib7.png)

点击按钮后会弹出新的窗口，在新的窗口中点击「普通模式」。

![PPXbar API 订阅模式](https://rixcloud-1255365801.file.myqcloud.com/image/p467g.png)

按钮上的文字应当在点击后变成「已经复制到剪贴板」，说明 PPXbar API URI 已经复制到你计算机的剪贴板中。

!> 这个 API URI 非常重要，你应当把它当做密码一样妥善保管，避免泄露。

![复制 API URI 到剪贴板](https://rixcloud-1255365801.file.myqcloud.com/image/kh4at.png)

---

### 配置 KoolSS

打开软件中心，然后从「已安装」的插件列表中打开 KoolSS。

如果 KoolSS 出于关闭状态，则点击开关打开它。

点击「节点管理」选项卡， 然后点击二级的「节点管理」选项卡。

![节点管理](https://rixcloud-1255365801.file.myqcloud.com/image/olods.png)

在下方的 SSR 节点订阅中填写一些必要信息。

将我们刚才复制的 PPXbar API URI 粘贴到「SSR 节点订阅地址」中；将「订阅节点模式设定」选择为「游戏模式」；然后将订阅节点混淆参数设定设置为「使用订阅设定」。

![配置 PPXbar API 订阅](https://rixcloud-1255365801.file.myqcloud.com/image/t61lj.png)

> 「订阅节点模式设定」可以根据你的需求来设置，但最佳使用体验是设置为「游戏模式」。

配置完成后点击「保存订阅设置」，页面将会自动跳转。

完成后，再次返回此页面，并点击「手动更新订阅」。页面将会自动跳转并刷出类似下图的日志信息：

![更新订阅](https://rixcloud-1255365801.file.myqcloud.com/image/k7zql.png)

此时 PPXbar 接入点信息已经添加到你的 KoolSS 中了，现在让我们来做一些附加设置以便更好地使用。

---

### KoolSS 附加设置

点击「规则管理」选项卡，将下方的 KoolSS 规则自动更新设置为「开启」，将时间设置为你可能不会使用网络的时间，然后勾选所有规则复选框。

![设置规则管理](https://rixcloud-1255365801.file.myqcloud.com/image/u603p.png)

> 你可以只勾选图中红框框选的「chnroute」和「chn_list」，但建议全部勾选。

点击「DNS 设定」选项卡，进行如下设定：

> 将「DNS 解析偏好」设置为「国外优先」  

> 将「选择国内 DNS」设置为「运营商 DNS」或「自定义」，然后输入 `119.28.28.28`  

> 将「选择国外 DNS」设置为「ss-tunnel」，然后选择你喜欢的国外公共 DNS 服务提供商  

> 将「SS 服务器地址解析」设置为「nslookup 方式」，然后输入 `119.28.28.28`  

> 勾选「chromecast 支持」以劫持局域网内设备的 DNS 解析，避免受到 DNS 缓存污染  

![DNS 设定](https://rixcloud-1255365801.file.myqcloud.com/image/jvmlx.png)

---

### 开启 KoolSS

返回到 KoolSS 主页面「账号设置」，选择需要使用的接入点，然后点击下方的「提交」按钮。

![选择接入点](https://rixcloud-1255365801.file.myqcloud.com/image/c4rjl.png)

页面会自动跳转并刷出类似下图的日志信息：

![KoolSS 启动日志](https://rixcloud-1255365801.file.myqcloud.com/image/13gcg.png)

完成后，页面会自动跳转回主页面，并启动连接测试，如果如下图显示则连接成功，所有连接到此路由器的设备都可以通过 PPXbar 网络连接到国际互联网。

![连接检查](https://rixcloud-1255365801.file.myqcloud.com/image/soig9.png)

!> 某些情况下，显示连接错误并非未能连接上，而是可能的测试失败，请实际使用浏览器打开网页测试。

