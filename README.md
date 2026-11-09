# Akagi AdBlock Android

面向 **AdGuard for Android** 的**补充**过滤规则：拦截常见漏网的移动广告 SDK / 广告网络域名，以及广告点击跳转、弹窗跳转、恶意重定向与常见追踪参数。

> 本仓库是对 AdGuard 内置列表（如 Mobile Ads、Tracking Protection 等）的补充，**不能替代**它们。请继续保留你现有的 AdGuard / AdGuard DNS 配置。

维护者：[@fenix79-newbie](https://github.com/fenix79-newbie) · 角色设定：赤城（Akagi）🦊

## 订阅地址（Raw）

推荐只订阅合并列表：

```
https://raw.githubusercontent.com/fenix79-newbie/akagi-adblock-android/main/filters/all.txt
```

也可按需分开订阅：

| 文件 | 用途 | Raw URL |
|------|------|---------|
| `filters/all.txt` | 合并列表（推荐） | `https://raw.githubusercontent.com/fenix79-newbie/akagi-adblock-android/main/filters/all.txt` |
| `filters/mobile-ads.txt` | 移动广告 SDK / 广告网络 | `https://raw.githubusercontent.com/fenix79-newbie/akagi-adblock-android/main/filters/mobile-ads.txt` |
| `filters/redirect-links.txt` | 广告跳转 / 追踪参数 | `https://raw.githubusercontent.com/fenix79-newbie/akagi-adblock-android/main/filters/redirect-links.txt` |

当前版本：**1.0.0**  
约略规则数：`mobile-ads` ≈ 199 · `redirect-links` ≈ 127 · `all` ≈ 326

## 在 AdGuard for Android 中添加

1. 打开 **AdGuard** → **设置** → **过滤器**（或「过滤」）
2. 进入 **自定义过滤器**（Custom filters）
3. 点 **添加过滤器** / **+**
4. 粘贴上面的 Raw URL（推荐 `all.txt`）
5. 确认添加，等待下载完成并启用
6. （可选）回到过滤器列表，确认该自定义过滤器已打开

### 关于 HTTPS 过滤（强烈建议）

应用内广告跳转、`$removeparam` 去追踪参数、部分 HTTPS 广告请求，需要开启 **HTTPS 过滤 / HTTPS 过滤（带用户证书）**：

1. AdGuard → **设置** → **HTTPS 过滤**
2. 开启 HTTPS 过滤，并按提示安装 / 信任用户证书
3. 如某 App 因证书校验失败无法联网，可在 HTTPS 过滤里为该 App 单独关闭

没有 HTTPS 过滤时，域名级 `||domain^` 规则仍可通过 DNS / 普通过滤拦截大量广告请求，但跳转链接与参数剥离效果会变弱。

## 也适用于 AdGuard DNS / Personal DNS？

- `filters/mobile-ads.txt` 与 `all.txt` 中的 **`||domain^` 网络规则** 可在支持 Adblock 语法的 DNS 过滤中使用（效果限于域名拦截）。
- `$removeparam`、`$document` 等修饰符依赖完整 HTTP(S) 过滤，**DNS  alone 无效**。

## 覆盖范围（摘要）

- 穿山甲 / Pangle / CSJ、广点通 GDT、快手联盟、百度联盟
- 小米 / OPPO·HeyTap / vivo / 华为广告域名
- Unity Ads、AppLovin、Vungle/Liftoff、ironSource、Mintegral、InMobi、AdColony、Chartboost、Tapjoy、Fyber、Rayjump(MTG)、TopOn/AnyThink、Sigmob、倍孜 等
- PropellerAds / PopAds / Adsterra / ExoClick / Clickadu / HilltopAds 等弹窗与跳转网络
- 常见滥用短链跳转（如 adf.ly、ouo.io、linkvertise 等，不含 bit.ly / t.co）
- `utm_*`、`fbclid`、`gclid`、`msclkid`、`click_id` 等追踪参数剥离
- 对微信/Google/Apple 登录支付等核心域名有 `@@` 放行例外

## 漏拦了怎么办？

请在本仓库开 Issue，并尽量提供：

1. App 名称 / 包名
2. 漏拦广告或跳转发生的场景（开屏 / 插屏 / 点链接后跳转…）
3. 如方便：AdGuard 最近请求日志里相关域名，或抓包域名

## 许可

MIT。规则域名来自公开信誉列表整理（含 AdGuard MobileFilter、anti-AD、HaGeZi 等），仅作补充，请遵守各上游项目许可与使用条款。
