# iOS 上安装与配置 Stash

## **Stash 简介**

**Stash** 是一款多协议代理客户端，支持 iOS/tvOS/macOS 平台，并完全兼容 Clash Premium 配置。它提供了丰富的功能，包括 Rule Set 规则、按需连接、SSID Policy Group、MitM、HTTP 嗅探、JavaScript 脚本改写等特性，使其成为 iOS 平台上 Clash 规则的最佳选择。

## **功能介绍**

*   **多协议代理**: Stash 支持多种协议，可以满足不同用户的代理需求。
*   **兼容 Clash Premium 配置**: 完全兼容 Clash Premium 配置，方便用户快速使用。
*   **丰富特性**: 提供 Rule Set 规则、按需连接、SSID Policy Group、MitM、HTTP 嗅探、JavaScript 脚本改写等丰富功能，满足用户个性化需求。

## **获取 Stash**

*   **Stash on iOS**: [在 iOS App Store 上下载 Stash](https://apps.apple.com/us/app/stash-proxy/id1577183161)
*   **Stash on tvOS**: [在 tvOS App Store 上下载 Stash](https://apps.apple.com/us/app/stash-proxy/id1577183161)
*   **Stash on macOS**: [在 macOS 上下载 Stash](https://stash.ws/mac) （需购买）

# **快速上手**

要在你的 iOS 设备启用 Stash，你仅需要导入一份 Stash / Clash 格式的配置文件。Stash 需要配置文件来指定代理服务器与网络策略，你可以通过 URL 下载服务提供商的配置，或者是导入存放在 iCloud / One Drive 的本地文件来使用 Stash。

![Stash Logo](https://yunqijpg.oss-cn-hongkong.aliyuncs.com/image.png)

## **导入远程配置**

> 服务商一般会提供 Stash / Clash Premium / Clash 的订阅链接，最简单的方式是在 Stash 中导入机场订阅。

先进行 [订阅购买](https://vip06.stableconnect.cloud/#/plan) ，获取到订阅链接。订阅链接位于：仪表盘 > 一键订阅 , 然后复制订阅地址或者扫描二维码订阅。
    

![Remote Configuration](https://yunqijpg.oss-cn-hongkong.aliyuncs.com/wc2.jpg)

1.  在 Stash 的设置页面，选择配置文件。
2.  在 Stash 的配置列表，选择从 URL 下载。
3.  在输入框输入您的订阅地址后，点击下载。
4.  确保您所希望使用的配置文件已在选中状态。
5.  回到 Stash 首页，点击启动。
6.  至此，您的 Stash 已进入可用状态，请尽情享用！😉

## **在官网支持一键"导入Stash"**

*   官网->一键订阅->导入到Stash

![Auto Import](https://yunqijpg.oss-cn-hongkong.aliyuncs.com/ap7.jpg)

---

# **常见问题！**

## **无法安装 Stash Mac 帮助程序 (Helper)**

部分用户可能会遇到反复提示需要安装帮助程序 (Helper) 的情况。Stash 需要使用管理员权限安装一个帮助程序，否则 Stash 将无法设置系统代理。

部分杀毒软件或清理软件可能会导致 Stash Helper 无法正常运行，请确保没有使用这一类软件阻止或清理 Stash Mac 。

### **macOS 13 Ventura**

在 macOS 13 苹果引入了新的后台权限管理，如错误配置此项会引起 Stash Helper 无法正常运行。

在 Mac 的「系统设置」 - 「通用」 - 「登陆项」 - 「允许在后台」，请确保 Stash 或 Stash Networks Limited 等开关为启用状态。

### **修复步骤**

如执行上述操作后依然无法安装 Stash Helper ，请尝试参照以下步骤修复：

1.  打开终端 (Terminal)。
2.  运行以下命令移除 Helper （需输入系统密码并按回车键）：

```plaintext
sudo rm -rf /Library/PrivilegedHelperTools/ws.stash.app.mac.daemon.helper
```

1.  运行以下命令启用 Helper （需输入系统密码并按回车键）。

```plaintext
sudo /bin/launchctl load -w /Library/LaunchDaemons/ws.stash.app.mac.daemon.helper.plist
```

如果提示 "service already loaded" 或 "Operation already in progress"，无需理会。

1.  重启电脑。
2.  打开 Stash ，重新安装帮助程序（需输入系统密码）。

至此，您的 Stash Helper 已修复。

## **防止代理被检测**

部分应用程序可能会检测系统是否使用代理软件，从而禁止用户在代理环境下使用。Stash 提供了「仅使用 Tunnel 代理」模式来防止应用程序检测代理程序，该选项将禁用 Stash Proxy，使得所有 HTTP(S) 请求亦会交由 Stash Tunnel 进行处理，以改善和某些应用的兼容性问题。

1.  在 Stash 的设置页面，选择「网络设置」。
2.  打开「仅使用 Tunnel 代理」。

![Prevent Detection](https://stash.wiki/_next/image?url=%2F_next%2Fstatic%2Fmedia%2Fproxy-detected-zh.b9871f08.png&w=3840&q=75)

开启这个选项会使得 Stash HTTP Engine 失效 ，导致 HTTP 改写功能失效。避免该问题，请参考 Force HTTP Engine。
