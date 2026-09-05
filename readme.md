**本规则具有以下特点：**

- 黑名单由最新版 [GFWList](https://github.com/gfwlist/gfwlist) 自动转换；
- 加入 [Greatfire Analyzer](https://github.com/Loyalsoldier/cn-blocked-domain) 检测到的屏蔽域名；
- 自动转换最新版本的 `EasyList`, `Eaylist China`, `Peter Lowe 广告和隐私跟踪域名`，`乘风规则` 为 SR 规则，全面去除广告且去除重复；
- 包括自定义的广告过滤规则，针对 iOS 端的网页广告、App 广告和视频广告；
- 提供多个规则文件供大家自由选择或者自由切换使用；
- 专门针对 ShadowRocket 开发，可以保证与 SR 的兼容性；
- 将 [Apple及其CDN域名](https://raw.githubusercontent.com/felixonmars/dnsmasq-china-list/master/apple.china.conf) 进行优化；
- 方便的快捷指令与自动化联动，每天自动更新规则；
- 增加使用代理组的懒人配置；
- 由于世界排名 top 500 网站列表已无法通过无账户/免费方式取得，故原来的 top500 检测方法失效。我已根据旧的 top500 榜单重构了新的 top500 网站连接情况表。**同时，希望大家可以帮助 pull requests 一份最新的 top500 榜单: [格式](https://github.com/Johnshall/Shadowrocket-ADBlock-Rules-Forever/blob/build/factory/resultant/top500_manual.list)**
- **所有发布的规则都会在每天北京时间 8:00 更新发布**


## 规则列表

![规则选择指南](https://johnshall.github.io/Shadowrocket-ADBlock-Rules-Forever/figure/guide.png)

规则 | 规定代理的网站 | 规定直连的网站 
--- | ----------- | ------------- 
[黑名单规则 + 去广告](#黑名单过滤--广告) |  被墙的网站（GFWList） | 正常的网站 
[黑名单规则](#黑名单过滤) |   |  
[白名单规则 + 去广告](#白名单过滤--广告) | 其他网站 | top500 网站中可直连的网站、中国网站 
[白名单规则](#白名单过滤) |   |  
[国内外划分 + 去广告](#国内外划分--广告) |  国外网站 | 中国网站
[国内外划分](#国内外划分) |   |  
[全局直连 + 去广告](#直连去广告) | / | 全部
[全局代理 + 去广告](#代理去广告) |  全部 | /
[回国规则 + 去广告](#回国规则--广告) | 中国网站 | 国外网站 
[回国规则](#回国规则) |   |  
[仅去广告规则](#仅去广告规则) |   |  
[懒人配置](#懒人配置) | 国外网站 | 国内网站  
[懒人配置（含策略组）](#懒人配置-含策略组) | 国外网站 | 国内网站  

- 以上所有规则，局域网内请求均直连。
- 可以下载多个规则切换使用。

## 规则使用方法

方法一：用 Safari 或 ShadowRocket 扫描二维码即可。  
方法二：在 ShadowRocket 应用中，进入 [配置] 页面，点击右上角加号，将规则文件地址粘贴到 url 处，点击“下载”即可。

最好让 ShadowRocket 断开并重新连接一次，以确保新的规则文件生效。 

## 如何自动更新
步骤一：安装[捷径](https://www.icloud.com/shortcuts/20bd590bc99e4ef0a157d2fe6e8c273d)，并填写规则文件地址；  
步骤二：打开“快捷指令”下方的“自动化”，轻击右上角加号，点击“创建个人自动化”，选择“特定时间”，设定时间为 8:05 或更晚的时间（规则生成需要一定时间），点击下一步，点击添加操作，选择 APP 栏，找到快捷指令，选择“运行快捷指令”，点击浅色“快捷指令”，选择“Shadowrocket 规则自动更新”，点击下一步，关闭运行前询问（可选），点击完成即可。

如果出现无法正常跳转 Safari 对 google.cn 的请求的情况，请在每次更新后点击规则后方的ℹ️，点击 HTTPS 解密，将 HTTPS 解密关闭，返回，再开启，即可正常跳转。

- **广告过滤不完全？**

> 该规则并不保证 100% 过滤所有的广告，尤其是视频广告，与网页广告不同的是，优酷等 App 每次升级都有可能更换一次广告策略，因此难以保证其广告屏蔽的实时有效性。而油管广告则不能通过简单的 url 匹配实现完全去广告。

- **外区 Apple Podcasts 无法正常加载** (感谢 [@jesuiseric](https://t.me/jesuiseric))

> 请将 `podcasts.apple.com`、`bookkeeper.itunes.apple.com`、`play.itunes.apple.com`、`xp.apple.com` 加入代理，详见 [#214](https://github.com/DivineEngine/Profiles/issues/214)

- **无法正常跳转 Safari 对 google.cn 的请求**

> 轻击配置 -> 轻击本地文件中正在使用的规则文件后的ℹ️ -> HTTPS 解密 -> 将右上角开关启动 -> 安装证书 -> 允许 -> 打开系统设置 -> 已下载描述文件 -> 安装 -> 输入密码 -> 安装 -> 通用 -> 关于本机 -> 证书信任设置 -> 对刚刚安装的根证书完全信任 即可正常跳转。

## 问题反馈

任何问题欢迎在 [Issues](https://github.com/Johnshall/Shadowrocket-ADBlock-Rules-Forever/issues) 中反馈。

你的反馈会让此规则变得更加完美。

**如何贡献代码？**

通常的情况下，对 [factory 目录](https://github.com/Johnshall/Shadowrocket-ADBlock-Rules-Forever/tree/build/factory) 下的 3 个 `manual_*.txt` 文件做对应修改即可。**Pull requests 请发送至 build 分支。**

----------------------------------------

## 黑名单过滤 + 广告

黑名单中包含了境外网站中无法访问的那些，对不确定的网站则默认直连。

- 代理：被墙的网站（GFWList）
- 直连：正常的网站
- 包含广告过滤

规则地址：<https://tumblemelon.github.io/Shadowrocket-ADBlock-Rules-Forever/sr_top500_banlist_ad.conf>

![二维码](https://tumblemelon.github.io/Shadowrocket-ADBlock-Rules-Forever/figure/sr_top500_banlist_ad.png)

## 白名单过滤 + 广告

白名单中包含了境外网站中可以访问的那些，对不确定的网站则默认代理。

- 直连：top500 网站中可直连的境外网站、中国网站
- 代理：默认代理其余的所有境外网站
- 包含广告过滤

规则地址：<https://tumblemelon.github.io/Shadowrocket-ADBlock-Rules-Forever/sr_top500_whitelist_ad.conf>

![二维码](https://tumblemelon.github.io/Shadowrocket-ADBlock-Rules-Forever/figure/sr_top500_whitelist_ad.png)


## 黑名单过滤

现在很多浏览器都自带了广告过滤功能，而广告过滤的规则其实较为臃肿，如果你不需要全局地过滤 App 内置广告和视频广告，可以选择这个不带广告过滤的版本。

- 代理：被墙的网站（GFWList）
- 直连：正常的网站
- 不包含广告过滤

规则地址：<https://tumblemelon.github.io/Shadowrocket-ADBlock-Rules-Forever/sr_top500_banlist.conf>

![二维码](https://tumblemelon.github.io/Shadowrocket-ADBlock-Rules-Forever/figure/sr_top500_banlist.png)


## 白名单过滤

现在很多浏览器都自带了广告过滤功能，而广告过滤的规则其实较为臃肿，如果你不需要全局地过滤 App 内置广告和视频广告，可以选择这个不带广告过滤的版本。

- 直连：top500 网站中可直连的境外网站、中国网站
- 代理：默认代理其余的所有境外网站
- 不包含广告过滤

规则地址：<https://tumblemelon.github.io/Shadowrocket-ADBlock-Rules-Forever/sr_top500_whitelist.conf>

![二维码](https://tumblemelon.github.io/Shadowrocket-ADBlock-Rules-Forever/figure/sr_top500_whitelist.png)


## 国内外划分 + 广告

国内外划分，对中国网站直连，外国网站代理。包含广告过滤。国外网站总是走代理，对于某些港澳台网站，速度反而会比直连更快。

规则地址：<https://tumblemelon.github.io/Shadowrocket-ADBlock-Rules-Forever/sr_cnip_ad.conf>

![二维码](https://tumblemelon.github.io/Shadowrocket-ADBlock-Rules-Forever/figure/sr_cnip_ad.png)


## 国内外划分

国内外划分，对中国网站直连，外国网站代理。不包含广告过滤。国外网站总是走代理，对于某些港澳台网站，速度反而会比直连更快。

规则地址：<https://tumblemelon.github.io/Shadowrocket-ADBlock-Rules-Forever/sr_cnip.conf>

![二维码](https://tumblemelon.github.io/Shadowrocket-ADBlock-Rules-Forever/figure/sr_cnip.png)


## 直连去广告

如果你想将 SR 作为 iOS 全局去广告工具，这个规则会对你有所帮助。

- 直连：所有请求
- 包含广告过滤

规则地址：<https://tumblemelon.github.io/Shadowrocket-ADBlock-Rules-Forever/sr_direct_banad.conf>

![二维码](https://tumblemelon.github.io/Shadowrocket-ADBlock-Rules-Forever/figure/sr_direct_banad.png)


## 代理去广告

如果你想将 SR 作为 iOS 全局去广告 + 全局翻墙工具，这个规则会对你有所帮助。

- 直连：局域网请求
- 代理：其余所有请求
- 包含广告过滤

规则地址：<https://tumblemelon.github.io/Shadowrocket-ADBlock-Rules-Forever/sr_proxy_banad.conf>

![二维码](https://tumblemelon.github.io/Shadowrocket-ADBlock-Rules-Forever/figure/sr_proxy_banad.png)


## 回国规则

提供给海外华侨使用，可以回到墙内，享受国内的一些互联网服务。

- 直连：国外网站
- 代理：中国网站
- 不包含广告过滤

规则地址：<https://tumblemelon.github.io/Shadowrocket-ADBlock-Rules-Forever/sr_backcn.conf>

![二维码](https://tumblemelon.github.io/Shadowrocket-ADBlock-Rules-Forever/figure/sr_backcn.png)


## 回国规则 + 广告

提供给海外华侨使用，可以回到墙内，享受国内的一些互联网服务。

- 直连：国外网站
- 代理：中国网站
- 包含广告过滤

规则地址：<https://tumblemelon.github.io/Shadowrocket-ADBlock-Rules-Forever/sr_backcn_ad.conf>

![二维码](https://tumblemelon.github.io/Shadowrocket-ADBlock-Rules-Forever/figure/sr_backcn_ad.png)


## 仅去广告规则

仅包含去广告规则，不包含代理/直连规则。用于与其他规则联用。

- 仅包含去广告规则，不包含代理/直连规则。无任何其他配置。

规则地址：<https://tumblemelon.github.io/Shadowrocket-ADBlock-Rules-Forever/sr_ad_only.conf>

![二维码](https://tumblemelon.github.io/Shadowrocket-ADBlock-Rules-Forever/figure/sr_ad_only.png)


----------------------------------------

以下规则基于 [blackmatrix7/ios_rule_script](https://github.com/blackmatrix7/ios_rule_script) 生成： 

## 懒人配置

不折腾，开箱即用。

- 配置简洁
- 规则覆盖范围广
- 国内外常用app单独分流

规则地址：<https://tumblemelon.github.io/Shadowrocket-ADBlock-Rules-Forever/lazy.conf>

![二维码](https://tumblemelon.github.io/Shadowrocket-ADBlock-Rules-Forever/figure/lazy.png)


## 懒人配置-含策略组

不折腾，开箱即用。下载规则后可在 i -> 代理分组 中自行配置。

- 配置简洁
- 规则覆盖范围广
- 国内外常用app单独分流
- 添加自动切换延迟最低节点类型
- 通过「代理分组」灵活调整流媒体分流策略

规则地址：<https://tumblemelon.github.io/Shadowrocket-ADBlock-Rules-Forever/lazy_group.conf>

![二维码](https://tumblemelon.github.io/Shadowrocket-ADBlock-Rules-Forever/figure/lazy_group.png)

