# Surge 2 for Mac

> 最后更新时间：{docsify-updated}

!> 这是一个付费软件，你需要购买才能使用。

---

### 此文档中的系统环境 {docsify-ignore}

?> macOS High Sierra 10.13.4 Beta (13E139j)  
Surge Mac 2.5.1 (Build 530)

---

### 为 Surge for Mac 授权

Surge Mac 版在启动时会要求输入购买邮箱和一个激活码来授权，未授权的 Surge Mac 版无法运行。

按下 <kbd>Command</kbd> + <kbd>,</kbd> 可以打开 Surge Mac 偏好设置，并可以查看授权信息。

![Surge Mac 授权](https://rixcloud-1255365801.file.myqcloud.com/image/98e88.png)

---

### 检查 rixCloud 订阅的设置

!> 此步骤非常重要，必须按照此步骤检查无误后才能正常使用 Surge

Surge 3 Pro 并不兼容 SSR 协议，因此需要在 rixCloud 管理门户将所有协议组设置为「兼容模式」才能使用。

访问 rixCloud 管理门户，点击已经激活的订阅进入订阅管理页面。然后点击「订阅设置」按钮，确保所有插件都如下图所示包含「兼容」字样：

![订阅设置](https://rixcloud-1255365801.file.myqcloud.com/image/60qwv.png)

---

### 获取 Surge 配置文件

rixCloud 管理门户提供 Surge 的配置文件。

打开 rixCloud 管理门户，点击订阅名称进入订阅信息管理页面。在「自动配置」功能区找到Surge - 「配置下载」

![Surge 配置下载](https://rixcloud-1255365801.file.myqcloud.com/image/aimpf.png)

浏览器应当会打开一个新窗口，并在稍后自动下载一个名称为 `rixCloud.conf` 的文件。

!> 这个配置文件中包含了你的所有连接信息，你应该妥善保存并不应该将其分享给他人。

![rixCloud.conf](https://rixcloud-1255365801.file.myqcloud.com/image/fpauv.png)

运行 Surge 应用程序，然后按下 <kbd>Command</kbd> + <kbd>,</kbd> 打开 Surge Mac 偏好设置，或点击状态栏上的 Surge 图标，然后选择「配置」。

![Surge Mac 偏好设置](https://rixcloud-1255365801.file.myqcloud.com/image/yccmr.png)

在打开的窗口中点击「配置式」选项卡。

![Surge Mac 配置列表](https://rixcloud-1255365801.file.myqcloud.com/image/hulom.png)

在 Finder（也被称为「访达」）中找到刚才下载的配置文件，然后点击「打开」。

![打开配置文件](https://rixcloud-1255365801.file.myqcloud.com/image/8vtxm.png)

Surge Mac 配置列表中会出现新的名称为 `rixCloud` 的配置，只需要双击此配置以使用此配置即可。

![使用 rixCloud 配置](https://rixcloud-1255365801.file.myqcloud.com/image/cbj7i.png)

点击状态栏的 Surge 图标，然后在策略组 rixCloud 中选择所需使用的接入点

![选择接入点](https://rixcloud-1255365801.file.myqcloud.com/image/mblfi.png)

按下 <kbd>Command</kbd> + <kbd> S </kbd> 或点击 Surge 选择「设置为系统代理」即可开始使用。

![启用 Surge](https://rixcloud-1255365801.file.myqcloud.com/image/6dvul.png)

某些应用程序可能不遵循系统代理，只需要按下 <kbd>Command</kbd> + <kbd> E </kbd> 或点击 Surge 选择「增强模式」即可。

---

### 使用 rixCloud 云端托管配置

Surge Mac 无法直接从 URL 添加配置，而通过下载获得的配置文件为了方便用户修改，默认未启用云端托管配置的功能。但是 Surge Mac 实际上是支持云端托管配置功能的。

那么，如何在 Surge Mac 上使用云端托管配置以及时享受到 rixCloud 新添加的接入点呢？

如果你有 iOS 设备，则只需要点击[这里](/iOS/Surge-3/Guides/)查看文档，在 iOS 上设备添加云端托管配置并启用 iCloud 同步即可。iCloud 会自动将配置文件同步给 Surge Mac。

如果你没有 iOS 设备，也可以手动修改配置文件。

首先打开 rixCloud 管理门户，点击订阅名称进入订阅信息管理页面。在「自动配置」功能区找到Surge - 「托管配置」。

![Surge 托管配置](https://rixcloud-1255365801.file.myqcloud.com/image/ra0pm.png)

按下「托管配置」的按钮，按钮应当显示「已复制到剪贴板」。

!> 这个 API URI 非常重要，你应当把它当做密码一样妥善保管，避免泄露。

![复制云端托管配置链接到剪贴板](https://rixcloud-1255365801.file.myqcloud.com/image/d6xq7.png)

通过文本编辑器或 `vim` 打开之前下载的 `rixCloud.conf`

在配置文件的顶部添加一行

```
#!MANAGED-CONFIG https://api.rixcloud.io/v1/common/service/0000/subscribe/surge?auth=000000000 interval=259200 strict=true
```

将上方代码块中的 `https://api.rixcloud.io/v1/common/service/0000/subscribe/surge?auth=000000000` 替换成你刚才复制的内容，然后粘贴到配置文件的顶部。

重复之前导入配置文件到 Surge 的步骤。

![更新为托管型配置](https://rixcloud-1255365801.file.myqcloud.com/image/f6pt4.png)

恭喜！你的配置文件已经更新为会自动保持更新的 rixCloud 云端托管配置！


