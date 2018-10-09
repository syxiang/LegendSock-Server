# Shadowrocket

> 最后更新时间：{docsify-updated}

!> 这是一个付费软件，你需要购买才能使用。

> 此软件更新较为频繁，文档中的某些内容可能随时间变化而不再有效。

!> 收到大量报告称，此应用程序存在稳定性问题

---

### 此文档中的系统环境 {docsify-ignore}

?> iPhone10,3 / iOS 11.2.5 (15D60)  
Shadowrocket 2.1.21 (Build 616)

---

### 检查 PPXbar 订阅的设置

!> Shadowrocket 完全支持 SSR 协议

如果不需要使用 Surge 等软件，建议将订阅协议组设置为不带有「兼容」字样的协议（混淆插件除外）。

访问 PPXbar 管理门户，点击已经激活的订阅进入订阅管理页面。然后点击「订阅设置」按钮即可修改。

![订阅设置](https://rixcloud-1255365801.file.myqcloud.com/image/8plkh.png)

---

### PPXbar API 配置

打开 PPXbar 管理门户，点击订阅名称进入订阅信息管理页面。在「自动配置」功能区找到桌面平台 - 「节点订阅」。

![PPXbar API 订阅](https://rixcloud-1255365801.file.myqcloud.com/image/grx5a.jpg)

在弹出的窗口中选择「普通模式」，按下按钮，如果按钮文字变为「已复制到剪贴板」，则说明 PPXbar API URI 已经复制。

!> 这个 API URI 非常重要，你应当把它当做密码一样妥善保管，避免泄露。

![已复制到剪贴板](https://rixcloud-1255365801.file.myqcloud.com/image/oo35o.jpg)

打开  Shadowrocket，点击 <kbd>+</kbd> 或点击「添加节点」

在新的页面中，选择「类型」为 Subscribe

在 URL 中粘贴刚才复制的 PPXbar API URI，在备注中填写为：PPXbar

![添加订阅](https://rixcloud-1255365801.file.myqcloud.com/image/p4buc.jpg)

Shadowrocket 会从 PPXbar API 获取订阅信息并添加节点到客户端。

![节点已经添加](https://rixcloud-1255365801.file.myqcloud.com/image/w31on.jpg)

然后点击底部的「设置」，选择「服务器订阅」，将开关「打开时更新」打开，并确保其他设置和下图相同。

![服务器订阅设置](https://rixcloud-1255365801.file.myqcloud.com/image/9ab0p.jpg)

之后，每次打开 Shadowrocket 时，应用程序就会自动通过 PPXbar API 更新节点信息。

---

### PPXbar 一键导入

打开 PPXbar 管理门户，点击订阅名称进入订阅信息管理页面。在「自动配置」功能区找到全平台 - 「一键导入」，如果你仅安装了 Shadowrocket，则会弹出窗口询问是否使用 Shadowrocket 打开。

![Shadowrocket 打开](https://rixcloud-1255365801.file.myqcloud.com/image/kdv96.jpg)

点击打开，会自动跳转到 Shadowrocket 并添加接入点。

![添加所有接入点](https://rixcloud-1255365801.file.myqcloud.com/image/5au4t.jpg)

此方式更加方便快捷，但接入点信息不会自动更新，如果 PPXbar 添加或删除了某些接入点，则必须手动操作。

---

### 从剪贴板配置

某些情况下，我们可能不止安装了 Shadowrocket，还安装了其他的代理软件，这些软件将可能占用 `ssr://` 的 URL Scheme，导致我们无法直接使用一键配置为 Shadowrocket 添加接入点，如下图。

![由 Quantumult 打开](https://rixcloud-1255365801.file.myqcloud.com/image/v9uuh.jpg)

这时我们仅需要点击「取消」，而 PPXbar 管理门户已经自动复制了 SSR 代码到你的剪贴板（你可能注意到点击一键配置按钮的一瞬间，按钮文字变为了「已经复制到剪贴板」）。

!> 剪贴板内的 SSR 代码非常重要并包含了你所有的连接信息，你应当注意避免泄露

打开 Shadowrocket，Shadowrocket 会侦测到剪贴板内的 SSR 代码并询问是否要添加。

![从剪贴板添加](https://rixcloud-1255365801.file.myqcloud.com/image/pyaqo.jpg)

只需要选择「添加」，所有接入点信息就会添加到你的 Shadowrocket。

此方式添加的接入点信息不会自动更新，如果 PPXbar 添加或删除了某些接入点，则必须手动操作。

---

### 启动 Shadowrocket

在 Shadowrocket 主页面选择一个接入点，然后点击顶部的开关。

如果是第一次使用，则会提示需要添加 VPN 连接。

![添加 VPN 连接](https://rixcloud-1255365801.file.myqcloud.com/image/4rd8k.jpg)

点击 Allow 后按系统提示操作，验证密码或 Touch ID。之后会自动返回到 Shadowrocket 界面并启用。

![Shadowrocket 已运行](https://rixcloud-1255365801.file.myqcloud.com/image/pe5iq.jpg)


