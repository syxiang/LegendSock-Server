# Quantumult

> 最后更新时间：{docsify-updated}

!> 这是一个付费软件，你需要购买才能使用。

> 此软件更新较为频繁，文档中的某些内容可能随时间变化而不再有效。

!> 此应用程序的配置步骤较长，需要耐心仔细阅读每一个步骤。

---

### 此文档中的系统环境 {docsify-ignore}

?> iPhone10,3 / iOS 11.2.5 (15D60)  
Quantumult 2.1.4 (Build 403)

---

### 检查 rixCloud 订阅的设置

!> Quantumult 完全支持 SSR 协议

如果不需要使用 Surge 等软件，建议将订阅协议组设置为不带有「兼容」字样的协议（混淆插件除外）。

访问 rixCloud 管理门户，点击已经激活的订阅进入订阅管理页面。然后点击「订阅设置」按钮即可修改。

![订阅设置](https://rixcloud-1255365801.file.myqcloud.com/image/8plkh.png)

---

### 获取 rixCloud API 订阅

打开 rixCloud 管理门户，点击订阅名称进入订阅信息管理页面。在「自动配置」功能区找到桌面平台 - 「节点订阅」。

![rixCloud API 订阅](https://rixcloud-1255365801.file.myqcloud.com/image/grx5a.jpg)

在弹出的窗口中选择「普通模式」，按下按钮，如果按钮文字变为「已复制到剪贴板」，则说明 rixCloud API URI 已经复制。

!> 这个 API URI 非常重要，你应当把它当做密码一样妥善保管，避免泄露。

![已复制到剪贴板](https://rixcloud-1255365801.file.myqcloud.com/image/oo35o.jpg)

---

### 配置 Quantumult

##### 添加服务器订阅

打开 Quantumult，点击底部的「Settings」进入设置页面。

![设置页面](https://rixcloud-1255365801.file.myqcloud.com/image/bznet.jpg)

点击「Favorites」 进入订阅管理页面，然后点击右上角的 <kbd>+</kbd>

![添加订阅](https://rixcloud-1255365801.file.myqcloud.com/image/ww5o2.jpg)

在弹出的菜单中选择「Server」

在新的页面中，点击 「Name」，输入 `rixCloud` 并保存，然后点击 「URL」，将刚才复制的 rixCloud API URI 粘贴进去，并勾选下方的「Delete Option」。

?> Delete Option 表明当远程 API 返回某个服务器已经被删除时，Quantumult 也将在本地删除这个节点。这可以避免某些无效的接入点仍然储存在本地客户端。

![添加 Server](https://rixcloud-1255365801.file.myqcloud.com/image/ix6au.jpg)

添加完成后，会自动返回订阅管理页面，这时在 Server 分类下名称为 rixCloud 的选项上向左轻扫，点击「Update」

![更新接入点](https://rixcloud-1255365801.file.myqcloud.com/image/khf70.jpg)

Quantumult 会开始更新接入点并在完成后返回：

![更新完成](https://rixcloud-1255365801.file.myqcloud.com/image/vx8tq.jpg)

##### 添加 TCP Filter 订阅

点击「Favorites」 进入订阅管理页面，然后点击右上角的 <kbd>+</kbd>

![添加订阅](https://rixcloud-1255365801.file.myqcloud.com/image/ww5o2.jpg)

在弹出的菜单中选择「TCP Filter」

在新的页面中，点击 「Name」，输入 `rixCloud` 并保存，然后点击 「URL」，添加：

`https://static.rixcloud.io/Resources/iOS/Quantumult/Rules/Default.conf`

[或长按此处复制 URL](https://cdn.rixcloud.io/resource/rules/Android/ACL/banAD.acl)

然后勾选下方的「Filter Action」

![TCP 规则](https://rixcloud-1255365801.file.myqcloud.com/image/2zwqb.jpg)

同样，在 TCP Filgter 分类下名称为 rixCloud 的选项上向左轻扫，点击「Replace」。Quantumult 会从 rixCloud 静态资源服务器上下载 TCP 规则，并在完成后弹出新页面：

![TCP 规则](https://rixcloud-1255365801.file.myqcloud.com/image/ce5u3.jpg)

点击 OK 即可。

##### 添加 Rejection 规则

点击「Favorites」 进入订阅管理页面，然后点击右上角的 <kbd>+</kbd>

![添加订阅](https://rixcloud-1255365801.file.myqcloud.com/image/ww5o2.jpg)

在弹出的菜单中选择「Rjection」

在新的页面中，点击 「Name」，输入 `rixCloud` 并保存，然后点击 「URL」，添加：

`https://static.rixcloud.io/Resources/iOS/Quantumult/Rules/Reject.conf`

[或长按此处复制 URL](https://cdn.rixcloud.io/resource/rules/Android/ACL/banAD.acl)

由于 rixCloud 提供的规则中不包含 MitM 中间人攻击规则，因此无需勾选下方的选项。

如果你需要使用 MitM 以将规则应用到 HTTPS 连接中，则应当勾选这个选项后启用中间人攻击功能。

![拒绝类规则](https://rixcloud-1255365801.file.myqcloud.com/image/b9qhu.jpg)

同理，在  Rejection 分类下名称为 rixCloud 的选项上向左轻扫，点击「Replace」。

![更新规则](https://rixcloud-1255365801.file.myqcloud.com/image/m1gg6.jpg)

Quantumult 会从 rixCloud 静态资源服务器上下载拒绝类规则，并在完成后弹窗：

![拒绝类规则](https://rixcloud-1255365801.file.myqcloud.com/image/wnk00.jpg)

---

# 启动 Quantumult

上述规则都完成添加后，返回 Quantumult 设置页面

![设置页面](https://rixcloud-1255365801.file.myqcloud.com/image/s5b4r.jpg)

可以在 「Servers」中选择需要的接入点。

![选择接入点](https://rixcloud-1255365801.file.myqcloud.com/image/btrm6.jpg)

然后点击底部的 Home 选项卡，打开页面上方的开关以启动 Quantumult。

如果是第一次使用，会提示需要添加 VPN 连接，点击 Allow 后按系统提示操作。

![添加 VPN 连接](https://rixcloud-1255365801.file.myqcloud.com/image/ohzdh.jpg)

添加完成后会自动返回到 Quantumult，可以看到 Quantumult 已经正常运行。

![Quantumult 已启动！](https://rixcloud-1255365801.file.myqcloud.com/image/ydyde.jpg)

---

### 特殊模式

某些银行类和金融类的软件可能在启动时检查系统环境，在检测到 VPN 后会拒绝运行，启用 Quantumult 的特殊模式可以解决此问题。

同时，如果使用 Facebook Messenger 时遇到连接问题，也可以尝试此特殊模式

!> 如果能正常使用这些应用程序请勿启用此模式，将可能导致未知问题。

使用 iOS 设备的 Safari 浏览器点击下面的链接就可以启用或关闭此特殊模式。

点击[这里](quantumult://settings?compatible_level=1)启用特殊模式

点击[这里](quantumult://settings?compatible_level=0)关闭特殊模式


