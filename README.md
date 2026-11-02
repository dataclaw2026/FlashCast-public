# 闪电投屏 FlashCast

三端无线投屏：Windows PC 发送端 · Android 手机发送端 · Android TV 接收端。
自研协议实现，无第三方签名/加密依赖，局域网直连、开箱即用。

## 下载

从本仓 **Releases** 页下载对应平台的最新发布（三端版本号统一）：

| 平台 | 文件 | 说明 |
|---|---|---|
| Windows 10/11 x64 | `FlashCastPC.exe` | 单文件，双击运行 GUI，或 `--tv <ip>` 作 CLI |
| Android TV / 盒子（5.0+） | `FlashCastTV.apk` | 接收端，arm64 + armv7 |
| Android 手机（5.0+） | `FlashCastPhone.apk` | 发送端，arm64 + armv7 |

> 最新资产名与直接下载链接见本页 [Releases](../../releases)。
> 三端启动时会静默比对升级清单 `version.json`，发现新版自动提示升级。

## 快速开始

1. TV / 盒子安装并打开 `FlashCastTV.apk`，记下屏幕上的 **投屏码** 与 **本机 IP**。
2. PC 安装并打开 `FlashCastPC.exe`，自动扫描局域网接收端；或手动填 IP + 投屏码。
3. 手机安装 `FlashCastPhone.apk`，扫/填投屏码即可投屏。

## 端口

- 投屏服务 **12580**（TCP 控制 + 动态 UDP 媒体，握手自协商）
- 接收端管理页 **12581**（浏览器打开 `http://<TV IP>:12581/`，含设置与下载）

## 特性

- 多网卡自动探测，扫描全部网段寻找接收端投屏码；配置按钮随选中接收端动态定向。
- 三端本机 IP 展示（多网卡逗号分隔）。
- 懒加载自动升级：后台比对 `version.json`，有新版才提示，出错静默不打扰 UI。
- TV 未 root 时默认息屏策略，root 时默认关机策略。
