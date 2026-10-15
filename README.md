# LanR2der

<img src="assets/AppIcon-transparent.png" alt="LanR2der" width="128">

**LANraragi + R2 + Reader：支持本地拟物书架、离线下载与隐私锁的 iOS 和 Android 漫画客户端。**

[English](README.en.md) · [下载最新版 iOS IPA](https://github.com/Fuzage/LanR2der/releases/latest) · [下载 Android APK（1.4.5）](https://github.com/Fuzage/LanR2der/releases/download/android-v1.4.5/LanR2der-Android-1.4.5.apk) · [配套 LANraragi-R2 服务器](https://github.com/Fuzage/LANraragi-R2)

## 下载与安装

进入 [Releases](https://github.com/Fuzage/LanR2der/releases)，下载 `LanR2der-1.0.1-unsigned.ipa`。当前版本为 **1.0.1（Build 3）**，要求 **iOS 26.0 或更新版本**。

发布的是未签名 IPA，需要自行使用适合自己的签名工具签名并安装。该下载不包含开发者证书、签名账号或描述文件。校验文件 `LanR2der-1.0.1-SHA256SUMS.txt` 同时提供在 Release 中。

Android 用户请下载 [LanR2der-Android-1.4.5.apk](https://github.com/Fuzage/LanR2der/releases/download/android-v1.4.5/LanR2der-Android-1.4.5.apk)，要求 **Android 9.0（API 28）或更新版本**。APK 使用开发签名；升级安装需使用相同签名的版本。

首次打开 App，会进入服务器连接页面。App 不包含漫画，不预设任何个人书库地址。

## 连接自己的书库

1. 部署 [LANraragi-R2](https://github.com/Fuzage/LANraragi-R2)，为网站配置可访问的 HTTPS 域名和有效证书。
2. 在 LANraragi 网页设置中获取 API Key；未启用服务器密码时可以留空。
3. 在 App 首次连接页面填入完整 HTTPS 地址及 API Key，点击“连接书库”。
4. 成功后进入书架、列表和设置三个页面；以后可在设置中更换连接。

R2 的 Endpoint、桶名和访问密钥由 **服务器端**配置，App 无需填写 Cloudflare R2 密钥。R2 创建、权限及 CORS 设置步骤请查看 [服务端中文说明](https://github.com/Fuzage/LANraragi-R2/blob/main/README.md)。

本客户端主要配合 LANraragi-R2 使用；R2 上传、数据包读取及相关扩展依赖配套后端，官方原版 LANraragi 的完整兼容性尚未验证。

## 功能

### 本地拟物书架

- 木质书架、封面和按封面裁切生成的书脊；可设置每排单本数量。
- 书架初始为空，从书库批量选择漫画放入，支持封面与列表选择、排序。
- 长按跟手拖动、自动让位、悬停合并文件夹、文件夹嵌套及内部排序。
- 批量移动到其他文件夹、下载，以及从书架移除。
- 书架布局和文件夹层级保存在本机，与服务器分类独立。

### 列表和阅读

- 分类侧边栏、搜索、导入日期或标题排序，以及正序/倒序。
- 顶部“最近阅读”入口；侧边栏固定显示“已缓存”和“正在缓存”。
- 点击封面直接阅读；左右点击翻页、中间点击显示控制栏。
- 可开关拟物翻页，调整阅读方向和预加载页数。
- 详情页支持修改标题、标签、简介和分类，也可新建分类。

### 缓存与整本下载

- 封面、书脊和阅读页图使用本机磁盘缓存，普通图片缓存上限可设置为 256 MB 至 8 GB。
- 整本下载独立保留，支持队列进度及离线阅读，不受普通图片缓存上限淘汰。
- 列表长按多选后可批量下载或删除；详情页提供下载入口。
- **删除本机下载**只清除设备文件；**从书架移除**只修改本地摆放；**从服务器删除**会实际删除书库档案，R2 档案由配套服务端同步清理对象。服务器删除需要确认。

### App 内上传

- 上传到 R2 或 VPS，支持多文件队列和分类选择。
- 图片包中的 JPG、PNG、WebP 保留原格式；PDF 优先提取内嵌图片，复杂页面才按 DPI 渲染。
- R2 上传复用服务器提供的上传引擎，每本整理为一个页图数据包直传 R2。
- 上传时保持页面打开；系统进入后台可能暂停或中断上传。

### 隐私

- 固定 6 位隐私密码，支持 Face ID／设备可用的生物识别。
- 可设置返回前台时重新解锁。
- 可独立启用后台画面重度模糊。
- 服务器 API Key 和隐私凭据使用系统钥匙串保存。

## 更新说明

### 1.0.1 · 通用公开版

- 首次启动要求填写自己的服务器，移除预设的个人漫画域名。
- 保留已有用户保存的服务器配置与本地数据。
- 包含 App 内上传、元数据与分类编辑，以及现有书架、阅读、离线下载和隐私功能。

升级安装时尽量沿用相同签名身份及 App 标识；签名工具改动标识或卸载 App 可能影响本地书架、下载和钥匙串数据。

## 相关项目

- [LANraragi-R2](https://github.com/Fuzage/LANraragi-R2)：配套服务器与 R2 存储扩展。
- [LANraragi](https://github.com/Difegue/LANraragi)：原始书库服务。

此仓库用于发布 LanR2der 的安装包、使用说明和问题反馈。
