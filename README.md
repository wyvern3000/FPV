# FPV  [English](https://github.com/wyvern3000/FPV/blob/main/README.en.md)

Android 视频播放器，播放内核为 libmpv。支持本地存储、WebDAV、FTP/FTPS、SMB、IPTV 五类来源。

系统要求 Android 8.0（API 26）及以上 ｜ arm64-v8a

---

## 功能

### 媒体来源

| 来源 | 说明 |
|---|---|
| 本地存储 | 内置存储与 SD 卡，可将任意文件夹注册为来源 |
| WebDAV | 群晖、Alist、Nextcloud 等 |
| FTP / FTPS | 明文与 TLS 加密 |
| SMB / Samba | Windows 共享、NAS 共享 |
| IPTV (M3U) | 直播频道列表，支持台标与 EPG |
| 收藏夹 | 收藏的文件与频道汇总，跨来源 |

四类网络来源均支持在线读取：缩略图、断点续播、字幕匹配。

### 播放

- 硬件解码可切换自动 / 硬解 / 软解
- 网络来源支持拖动进度条定位（SMB、WebDAV、FTP 均为协议级随机读）
- 多音轨切换
- 章节跳转
- 画面比例切换：适应 / 裁剪 / 拉伸
- 音频延迟、字幕延迟调整，步长 0.1 秒
- A-B 循环
- 睡眠定时
- 倍速播放
- 信息面板：编码格式、分辨率、帧率、解码方式、码率、丢帧、缓存、倍速

### 手势

| 手势 | 功能 |
|---|---|
| 单击 | 显示 / 隐藏控制层 |
| 双击 | 播放暂停，或快进快退（可配置） |
| 横滑 | 拖动进度，带预览 |
| 左半屏竖滑 | 调节亮度 |
| 右半屏竖滑 | 调节音量 |
| 捏合 | 缩放画面 |
| 长按 | 倍速播放，可选 2x / 2.5x / 3x |

### 字幕

- 同名字幕自动匹配：`电影.mp4` 旁的 `电影.zh-CN.srt`、`电影.en.srt` 自动挂载，中文标记优先作为主字幕
- 双语字幕同时显示，主字幕在下、副字幕在上（位置可调）
- 外观可调：字体、字号、上下位置、颜色、描边、阴影；字体支持导入 ttf / otf
- ASS / SSA 特效字幕

### IPTV

- 导入 M3U 播放列表，或直接粘贴 M3U 链接
- 频道按 `group-title` 分组折叠
- 台标自动加载
- EPG 节目单在频道行内显示当前节目
- 频道可长按收藏，全部频道自动进入播放队列

### 浏览

- 列表 / 网格视图，按名称、时间、大小排序
- 视频缩略图，四类网络来源均支持
- 识别 `poster.jpg` 与 `.nfo`，在文件夹上显示海报与简介
- 支持 `.strm` 占位文件，播放其中记录的远程地址
- 全局搜索
- 断点续播与观看记录
- 文件夹内全部视频自动排成播放队列

### 界面与设置

- 打孔避让：避开屏幕打孔或状态栏所在的一侧，横竖屏均生效
- 多语言：简体中文、繁體中文、English、Français、Italiano
- 网络缓冲秒数可调
- WebDAV 并行下载开关
- 自定义 mpv 参数

---

## 支持的格式

### 可直接浏览与播放的文件类型

MP4、M4V、MOV、MKV、WebM、AVI、MPEG-TS（ts / m2ts / mts / m2t）、MPEG-PS（mpg / mpeg / mpe）、VOB、FLV、F4V、WMV、ASF、RM、RMVB、OGV、3GP、3G2、MXF、GXF、DV、QT、AMV、DIVX、MP4V、M1V、M2V、MPV、ISMV、M4P、M4B，以及 `.strm` 占位文件。

HLS（m3u8）与 MPEG-DASH（mpd）通过「打开 URL」或 IPTV 来源播放，不作为本地文件浏览。

### 支持的编码

**视频**：H.264 / AVC、H.265 / HEVC、H.266 / VVC、AV1、VP8、VP9、MPEG-1、MPEG-2、MPEG-4（Xvid / DivX）、H.263、VC-1、WMV1 / WMV2 / WMV3、MS-MPEG4、RealVideo 1 / 2 / 3 / 4（RMVB）、Theora、MJPEG、ProRes、DNxHD、CineForm、DV、Cinepak、Sorenson 1 / 3、AVS / CAVS、无损编码（FFV1、HuffYUV、Ut Video、Lagarith、MagicYUV）

**音频**：AAC、AAC-LATM、MP1 / MP2 / MP3、AC-3、E-AC-3、AC-4、DTS、DTS-HD、TrueHD、MLP、FLAC、ALAC、APE、Vorbis、Opus、WMA v1 / v2 / Pro / Lossless / Voice、WavPack、TTA、Musepack (MPC7 / MPC8)、Shorten、TAK、RealAudio（Cook、RA-144、RA-288、ATRAC）、AMR-NB / AMR-WB、Speex、Nellymoser、QDM2、S302M、PCM 全系列（含 LPCM / Blu-ray / DVD）、ADPCM 系列

### 字幕

SubRip (SRT)、ASS、SSA、WebVTT、MOV text、MicroDVD、MPL2、SAMI、RealText、Subviewer、VPlayer、PJS、Jacosub、STL、VobSub、PGS、DVD 字幕、DVB 字幕、XSUB、EIA-608 闭字幕

### 流媒体协议

HTTP、HTTPS、HLS、MPEG-DASH、RTMP、RTMPS、RTMPE、RTP、SRTP、UDP、FTP、AES-128 加密 HLS

### 不在浏览范围内的格式

播放内核还能解码**纯音频文件**（FLAC、APE、WAV、AIFF、CAF、MP3、AC-3、DTS 等）与**图片**（JPEG、PNG、BMP、GIF、QOI、PAM / PBM / PGM / PPM）。FPV 是一款视频播放器，此类文件置灰，无法点击播放。

---

## 安装

1. 下载apk
2. 在手机上安装（首次需允许"安装未知来源应用"）

仅提供 arm64-v8a 版本。

## 使用

### 添加来源

1. 进入底部**浏览器**页
2. 点右上角**加号**，选择来源类型
3. 填写地址与账号密码，保存
4. 点开源即可浏览文件

IPTV 来源填写 M3U 地址（例如 `http://192.168.1.10:1234/m3u`），EPG 地址可选。保存后进入该源，显示按分组折叠的频道列表。

浏览器页右上角的**链接**按钮可直接粘贴 M3U 链接播放，不保存为来源。

### 添加本地文件夹

在浏览器页根目录点**加号**，选择本地，定位到视频文件夹。该文件夹会作为来源出现在列表中。

### 播放

- 点视频文件开始播放，同文件夹内其它视频排成播放队列
- 播放页右上角的**播放列表**按钮打开队列跳集
- 退出时记录播放位置，下次打开继续播放
- 浏览器页右上角的**回到播放**按钮返回正在播放的画面，IPTV 频道同样适用

---

## 技术信息

- 界面：Kotlin + Jetpack Compose
- 播放内核：libmpv（FFmpeg 为 LGPL 构建）
- 网络：OkHttp、commons-net、smbj、sardine
- 最低版本：Android 8.0（API 26）
- 目标版本：API 34

### 权限

| 权限 | 用途 |
|---|---|
| `INTERNET`、`ACCESS_NETWORK_STATE` | 访问网络来源、加载台标与缩略图 |
| `READ_MEDIA_VIDEO`、`READ_EXTERNAL_STORAGE` | 读取本地视频 |
| `MANAGE_EXTERNAL_STORAGE` | 可选，浏览任意本地文件夹 |
| `WAKE_LOCK` | 播放时保持屏幕唤醒 |

不含广告 SDK 与数据统计 SDK。

---

## 反馈

提交问题时请附上设备型号、Android 版本、来源类型、复现步骤，以及 `下载/FPV_Logs/` 中的日志。

---

## 致谢

播放能力基于 [mpv](https://mpv.io/) 与 [FFmpeg](https://ffmpeg.org/)。JNI 部分参考 [mpv-android](https://github.com/mpv-android/mpv-android)（MIT）。
