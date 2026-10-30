# FlashCast-public (闪电投屏)

自研三端无线投屏：Windows PC 发送端（Go，单文件）· Android 手机发送端 · Android TV 接收端。
CRCP 协议自研实现，无签名/加密依赖，端口独立（投屏 12580 / 管理页 12581）。

## 下载

| 端 | 文件 | 说明 |
|---|---|---|
| PC (Win10/11 x64) | [pc/flashcast-go.exe](pc/flashcast-go.exe) | 单文件，双击 GUI 或 `--tv <ip>` CLI |
| TV 接收端 (Android 5.0+) | [apk/flashcast-tv.apk](apk/flashcast-tv.apk) | arm64 + armv7 |
| 手机发送端 (Android 5.0+) | [apk/flashcast-phone.apk](apk/flashcast-phone.apk) | arm64 + armv7 |

自动升级：三端启动时检测本仓库 `version.json`，发现新版本即提示。

## 端口

- 投屏服务 **12580**（TCP 控制 + 动态 UDP 媒体，握手自协商）
- 接收端管理页 **12581**（浏览器打开 `http://<TV IP>:12581/`，含设置与下载）

> 注意：官方客户端硬编码 7382，与本接收端不兼容（有意为之）。

## 编译

- PC: `cd go-client && go build`
- TV: `cd tv-receiver && gradle assembleDebug`（需 `prebuilt/crcp-stubs.jar`、`zxing-core.jar`）
- 手机: `cd flashcast && scripts/build.sh`
