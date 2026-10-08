# FPV [中文介绍](https://github.com/wyvern3000/FPV/blob/main/README.md)

An Android video player built on libmpv. Plays media from local storage, WebDAV, FTP/FTPS, SMB and IPTV sources.

Requires Android 8.0 (API 26) or later ｜ arm64-v8a

No ads, no account, no data collection.

---

## Features

### Media sources

| Source | Notes |
|---|---|
| Local storage | Internal storage and SD card; any folder can be registered as a source |
| WebDAV | Synology, Alist, Nextcloud, etc. Direct mode and parallel-chunk mode |
| FTP / FTPS | Plain and TLS |
| SMB / Samba | Windows shares, NAS shares |
| IPTV (M3U) | Live channel list with logos and EPG |
| Favourites | Favourited files and channels, gathered across sources |

All four network source types support reading in place: thumbnails, resume positions and subtitle matching work directly on remote files, with no download step.

### Playback

- Hardware decoding: auto / hardware / software
- Seeking works on network sources (SMB, WebDAV and FTP all use protocol-level random access)
- Audio track switching
- Chapter navigation
- Aspect ratio: fit / crop / stretch
- Audio delay and subtitle delay, in 0.1s steps
- A-B loop
- Sleep timer
- Playback speed
- Information panel: codec, resolution, frame rate, decoding mode, bitrate, dropped frames, cache, speed

### Gestures

| Gesture | Action |
|---|---|
| Single tap | Show / hide controls |
| Double tap | Play-pause, or seek (configurable) |
| Horizontal drag | Seek with preview |
| Vertical drag, left half | Brightness |
| Vertical drag, right half | Volume |
| Pinch | Zoom |
| Long press | Fast playback: 2x / 2.5x / 3x |

### Subtitles

- Sidecar subtitles are matched automatically: `movie.zh-CN.srt` and `movie.en.srt` next to `movie.mp4` are mounted on their own; Chinese-tagged files are preferred as the primary track
- Two subtitle tracks can be displayed at once, primary at the bottom and secondary at the top
- Appearance is configurable: font, size, position, colour, outline, shadow; fonts can be imported as ttf / otf
- ASS / SSA styled subtitles

### IPTV

- Import an M3U playlist, or paste an M3U link directly
- Channels grouped and collapsible by `group-title`
- Channel logos loaded automatically
- EPG: the current programme is shown inline on each channel row
- Long-press a channel to favourite it; all channels are queued for playback

### Browsing

- List and grid views, sorted by name, date or size
- Video thumbnails, for all four network source types
- Detects `poster.jpg` and `.nfo`, showing posters and synopses on folders
- Supports `.strm` placeholder files, playing the remote address recorded inside
- Global search
- Resume positions and watch history
- All videos in a folder are queued automatically

### Interface and settings

- Notch avoidance: keeps content clear of a camera cutout or status bar, in both orientations
- Languages: English, 简体中文, 繁體中文, Français, Italiano
- Adjustable network buffer
- WebDAV parallel download toggle
- Custom mpv options

---

## Supported formats

### Browsable and playable

File types that can be tapped and played in the browser (extension matching is case-insensitive):

MP4, M4V, MOV, MKV, WebM, AVI, MPEG-TS (ts / m2ts / mts / m2t), MPEG-PS (mpg / mpeg / mpe), VOB, FLV, F4V, WMV, ASF, RM, RMVB, OGV, 3GP, 3G2, MXF, GXF, DV, QT, AMV, DIVX, MP4V, M1V, M2V, MPV, ISMV, M4P, M4B, plus `.strm` placeholder files.

HLS (m3u8) and MPEG-DASH (mpd) play through "Open URL" or an IPTV source, not as browsable local files.

### Codecs inside video files

These are the codecs of the **tracks inside** a video file - as long as the file itself plays, its tracks decode.

**Video**: H.264 / AVC, H.265 / HEVC, H.266 / VVC, AV1, VP8, VP9, MPEG-1, MPEG-2, MPEG-4 (Xvid / DivX), H.263, VC-1, WMV1 / WMV2 / WMV3, MS-MPEG4, RealVideo 1 / 2 / 3 / 4 (RMVB), Theora, MJPEG, ProRes, DNxHD, CineForm, DV, Cinepak, Sorenson 1 / 3, AVS / CAVS, lossless codecs (FFV1, HuffYUV, Ut Video, Lagarith, MagicYUV)

**Audio**: AAC, AAC-LATM, MP1 / MP2 / MP3, AC-3, E-AC-3, AC-4, DTS, DTS-HD, TrueHD, MLP, FLAC, ALAC, APE, Vorbis, Opus, WMA v1 / v2 / Pro / Lossless / Voice, WavPack, TTA, Musepack (MPC7 / MPC8), Shorten, TAK, RealAudio (Cook, RA-144, RA-288, ATRAC), AMR-NB / AMR-WB, Speex, Nellymoser, QDM2, S302M, the full PCM family (including LPCM / Blu-ray / DVD), ADPCM variants

### Subtitles

SubRip (SRT), ASS, SSA, WebVTT, MOV text, MicroDVD, MPL2, SAMI, RealText, Subviewer, VPlayer, PJS, Jacosub, STL, VobSub, PGS, DVD subtitles, DVB subtitles, XSUB, EIA-608 closed captions

### Streaming protocols

HTTP, HTTPS, HLS, MPEG-DASH, RTMP, RTMPS, RTMPE, RTP, SRTP, UDP, FTP, AES-128 encrypted HLS

### Formats outside the browser

The playback engine can also decode **audio-only files** (FLAC, APE, WAV, AIFF, CAF, MP3, AC-3, DTS and more) and **images** (JPEG, PNG, BMP, GIF, QOI, PAM / PBM / PGM / PPM). FPV is a video player: the browser does not list these files and they cannot be tapped to play.

---

## Installation

1. Download apk
2. Install it on the device (allow "install unknown apps" the first time)

Only an arm64-v8a build is provided.

## Usage

### Adding a source

1. Open the **Browser** tab
2. Tap the **plus** button, then pick a source type
3. Enter the address and credentials, then save
4. Tap the source to browse its files

For an IPTV source, enter the M3U address (for example `http://192.168.1.10:1234/m3u`); the EPG address is optional. Opening the source shows the channel list grouped into collapsible sections.

The **link** button in the Browser toolbar plays an M3U link directly without saving it as a source.

### Adding a local folder

In the Browser root, tap the **plus** button, choose Local, and navigate to your video folder. The folder then appears in the source list.

### Playback

- Tapping a video starts playback; the other videos in the same folder become the queue
- The **playlist** button in the player toolbar opens the queue
- Leaving mid-playback records the position; the next open resumes from it
- The **back to player** button in the Browser toolbar returns to the current video, IPTV channels included

---

## Technical information

- UI: Kotlin + Jetpack Compose
- Playback engine: libmpv (FFmpeg built as LGPL)
- Networking: OkHttp, commons-net, smbj, sardine
- Minimum: Android 8.0 (API 26)
- Target: API 34

### Permissions

| Permission | Purpose |
|---|---|
| `INTERNET`, `ACCESS_NETWORK_STATE` | Network sources, channel logos, thumbnails |
| `READ_MEDIA_VIDEO`, `READ_EXTERNAL_STORAGE` | Reading local videos |
| `MANAGE_EXTERNAL_STORAGE` | Optional, for browsing arbitrary local folders |
| `WAKE_LOCK` | Keeping the screen awake during playback |

No advertising or analytics SDKs are included.

---

## Feedback

When reporting a problem, please include the device model, Android version, source type, steps to reproduce, and the logs from `Downloads/FPV_Logs/`.

---

## Credits

Playback is provided by [mpv](https://mpv.io/) and [FFmpeg](https://ffmpeg.org/). The JNI layer is based on [mpv-android](https://github.com/mpv-android/mpv-android) (MIT).
