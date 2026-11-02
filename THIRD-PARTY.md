# 第三方组件与本机验证来源

本项目作者字段为 Luno。以下第三方项目仍属于各自作者，不因本机集成而改变作者或许可。

## 内容核心：aston314/hongguo-tv

- 项目：https://github.com/aston314/hongguo-tv
- 本机研究快照提交：`7647f25053a00be17e700aff396fe968a9e0c9b9`。
- 下载归档：`../插件/tools/hongguo-tv-main.zip`。
- 归档 SHA-256：`122e6b8a7699654a7db55034ed51dcb91c6855daaeeaa3577405e21e1c1d116d`。
- 快照放在 `research/hongguo-tv-main`，不纳入 Vignette 自有源码提交。
- 0.1.0 至 0.1.3 使用未修改的快照；0.1.4 加入本地会话恢复补丁，修改 `minireel.go`、`minireel_range.go` 并增加 `reel_session_recovery_test.go`。补丁位于 `patches/session-recovery.patch`，仍通过 Go 编译为独立的本机研究核心；没有更新上游快照。
- 0.2.2 增加 `patches/aspect-ratio.patch`，分离清晰度档位和实际像素尺寸，并更新媒体缓存版本。快照内的 `vignette_dimensions_test.go` 覆盖横屏、竖屏、方形、缺少尺寸或档位的模型，以及清晰度列表和选择。
- 0.2.3 增加 `patches/cache-management.patch`：Windows 文件租约、可配置容量、后台清理及播放读取保护；修改媒体缓存检查并补充容量边界验证。补丁依次应用在会话恢复及画面比例补丁之后。
- 0.2.5 增加 `patches/playback-recovery.patch`，在前三个补丁之后应用，包含结构化空响应诊断、有限退避、冷却等待、Range 到完整文件回退的模型复用、播放签名和独立匿名播放注册配置。
- 播放签名/备用主机的实现参考 `aston314/hongguo-tv` 于 2026-11-02 的快照 `2119b837d566066e1db93435fcc6c722393958fa`，归档位于 `../插件/build/upstream-20261102.zip`，SHA-256 为 `0e8d06f5a965f2e3eae78a3de9745654da4e69bbb5bc846b9aec584cf780b313`；未整体替换研究核心。
- `minireel_device.go`、`minireel_f13.go` 的配置及播放 F13 分支 0 移植自 `jackotom/hongguo-drama` 的 `v5.4`，`src/native/playback-device.js` 与 `src/native/app-source.js`，保留 GPL-3.0-only 标识。算法来源记录为 `woshishiq1/drpys` 提交 `22261adfa31435e3b3ef5a730b8a2a75bcaf1715`、经 `N3urda/hongguoTV` 提交 `eea73e6a45569a2cbbb9440f7cd5290c459b0b70`；注册配置来源记录为 `tsukiyo-zero/hongguoTV` 提交 `388931852ddc614db8b00775a3dc54c5ede6307f`。本机六组 F13 向量及完整播放签名包的摘要与参考实现交叉校验，未引入 Node.js 或外部签名服务到插件运行包。
- 在快照顶层没有找到项目级 LICENSE；子目录的许可文件不等于整个项目的许可。
- 因此目前只作本机开发验证，不将包含此核心的目录视为可以公开分发的正式发布包。正式复用/分发须先明确授权与各依赖条件。
- Vignette 通过该核心已定义的本地 HTTP API 交互，没有把其账号签名与媒体处理代码复制到 Vignette 自有项目中。
- 该核心会访问源站、注册匿名设备，并包含媒体准备、解密与临时缓存。当前验证不能证明所有剧目、账号、地区或未来接口都可用，也不能替代平台授权判断。
- 账号资料由核心存放在指定本机数据目录。其当前会话文件采用 JSON 存储，尚未增加 Windows DPAPI 加密；不要分享该目录。
- 首版没有增加下载导出、金币任务、广告屏蔽或其他站源。

## LibVLCSharp 3.10.2

- 项目：https://code.videolan.org/videolan/LibVLCSharp
- 包：https://www.nuget.org/packages/LibVLCSharp/3.10.2
- NuGet 声明许可：LGPL-2.1-or-later。
- 作为独立辅助进程的托管播放器接口使用，未修改上游。

## VideoLAN.LibVLC.Windows 3.0.24

- 项目：https://www.videolan.org/vlc/libvlc.html
- 包：https://www.nuget.org/packages/VideoLAN.LibVLC.Windows/3.0.24
- 使用包内 Windows x64 动态库与插件，未修改上游。
- 本机精简包按 `scripts/package.ps1` 的列表省略当前播放器不使用的部分模块；保留的上游 DLL 按原字节复制。
- 各组件适用各自上游许可。正式发布前需准备相应许可文本、版权与源码获取信息，不能仅以 NuGet 包名代替合规材料。
- ARM64/x86 运行库没有复制进当前 x64 开发目录。

## Dalamud

- 项目：https://github.com/goatcorp/Dalamud
- 文档：https://dalamud.dev/plugin-development/getting-started
- 编译 SDK：Dalamud.CN.NET.Sdk 15.0.0。
- 使用本机 XIVLauncherCN 提供的程序集引用，未把 Dalamud 本体随 Vignette 分发。
- 正式提交官方仓库前还需确认插件发布规则和 AI 使用披露要求。

## 开发工具

- .NET SDK 10.0.302：使用本机环境。
- Go 1.27.3 Windows amd64：用于编译研究核心。
- Go 归档 SHA-256：`f26081f438319757f8a1b46d7d0b2c5ec7583d4038e485e0aa725cfde7885fff`，下载后已校验。
- 工具、缓存和测试会话位于“插件”内的工具/构建/检查目录，不属于发布内容。
