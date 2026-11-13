# 合体债 · Android 更新源

这个仓库只放 Android 版《合体债》的**自动更新包**，不放源码。
游戏启动时会自己来取最新网页包，玩家不用重装 APK。

- 当前安装包：v0.6.5（versionCode 11，APK 95,691 字节）
- 当前网页包：web 12
- 更新清单：`update.json`
- 更新包：`web-12.zip`

## 怎么装

**从 v0.6.5 起才会自动更新。v0.5 及更早版本没有内置更新器，必须手动装一次 v0.6.5。**

固定下载地址（永远指向最新版，转发这个链接就行）：

- 镜像：https://gh-proxy.com/https://raw.githubusercontent.com/WAZGZGWS/-/main/heti-debt-latest.apk
- 备用：https://ghproxy.net/https://raw.githubusercontent.com/WAZGZGWS/-/main/heti-debt-latest.apk
- 原始：https://github.com/WAZGZGWS/-/raw/main/heti-debt-latest.apk

步骤：

1. 手机浏览器打开上面任意一个，下载 `heti-debt-latest.apk`（当前 v0.6.5，95,691 字节）；
2. 点开安装，第一次要允许「安装未知应用 / 未知来源」；
3. **直接覆盖安装，不要卸载**：包名和签名跟 v0.5 一样，存档和设置会保留。
   只有提示「签名不一致」时才需要卸载旧版（会丢存档）；
4. 装完打开，约 1 秒后会自动检查并更新到最新网页包；以后不用再管安装包。

## 最低要求的安卓手机

| 项目 | 最低 | 推荐 |
|---|---|---|
| 系统 | Android 8.0（API 26） | Android 10 及以上 |
| WebView 内核 | Chrome / Android System WebView 66+ | 100+ |
| 内存 | 2 GB | 4 GB 及以上 |
| 可用存储 | 50 MB | 200 MB |
| 屏幕 | 5.5 英寸，1280×720，竖屏 | 6 英寸以上，1080p+ |
| 刷新率 | 30 Hz（设置里可锁 30 帧） | 60 Hz 及以上 |
| CPU | 任意 ARM / ARM64 / x86（APK 不含 native 库） | — |
| 网络 | 单机不需要；更新和联机才用 | Wi-Fi 5 |
| 谷歌服务 | 不需要 | — |

补充说明：

- 安装包的 `minSdk` 是 24（Android 7.0），但游戏用了 `async/await` 等语法，
  **WebView 内核低于 Chrome 55 时主脚本解析不了，菜单会点不动（看着像白屏）**；
  国产 ROM 的 Android 7 往往停在 Chrome 51，所以实际按 **Android 8.0 起**算。
- Android 8/9 如果从没更新过 WebView，也建议先去应用商店把
  「Android System WebView」或 Chrome 更新到最新版。
- 联机要求两台设备在**同一个 Wi-Fi**；路由器开了「AP 隔离」会连不上。

## 实测设备

- 小米平板 5（M2105K81AC），Android 13（API 33），2560×1600，dpr 2.25，WebView 116.0.0.0
- 默认 60 帧；可选自动 / 30 / 60 / 90 / 120，超过屏幕刷新率的档位会自动灰掉
- 平板 + 电脑（Node 房主）联机跑通；两台实体手机同时联机还没实测

## 怎么更新

1. 打开游戏约 1 秒后自动检查，有新版就自己下载、校验 sha256、重启进新版；
2. 更新完首页会提示「已自动更新到 vX（网页包 N）」；
3. 「更多 → 版本与更新」里能看到当前版本、每个版本改了什么，也能手动检查更新。
4. 玩联机时，如果房主的版本比你新，**加入前会自动把房主那一版同步过来**（包括代码和规则改动），
   同步失败就不进房间，避免两边规则对不上。

中国大陆直连 `raw.githubusercontent.com` 经常不通，APK 里已经内置了
`gh-proxy.com` / `ghproxy.net` 镜像并按顺序自动切换，**不需要梯子**。
GitHub 的 CDN 有缓存，刚发布后几分钟内可能还拿到旧清单，下次启动就会更新。

## 权限

- `INTERNET`、`ACCESS_NETWORK_STATE`、`ACCESS_WIFI_STATE`
- 不申请存储、定位、通讯录、相机、麦克风权限
- 允许明文 HTTP：联机时连同一 Wi-Fi 下的房主手机（`http://192.168.x.x:8788`）

## 版本

- v0.6.5（2026-11-14）：联机加入看门狗（20 秒没连上自动恢复，不再卡灰）、请求 6 秒超时；联机版本闸门（联机前自动同步房主新版）
- 更早的改动在游戏内「版本与更新」里

## 说明

个人项目，自用和分享给朋友，没有上架应用商店。
