# Vignette

游戏内的小手机，用于搜索、选集和观看短剧。作者：**Luno**。

## 安装

在卫月设置的“自定义插件仓库”中添加：

```text
https://raw.githubusercontent.com/Aporiyan/Vignette/main/pluginmaster.json
```

保存后在插件安装器搜索 **Vignette** 并安装。需要 Windows x64、Dalamud API 15 和 .NET 10。

当前版本：**0.2.3**。插件包含独立播放器和内容核心，无需安卓模拟器。

## 使用

- `/vignette`：打开小手机。
- `/vignette settings`：打开设置。
- `/vignette hide`：隐藏小手机。

支持横竖屏切换、窗口缩放、选集、播放进度、观看记录和账号页。播放可用性与画质取决于内容服务。

视频缓存默认位于 Dalamud 配置目录的 `Vignette/content/media-cache`，与安装目录分离。设置中可修改缓存目录、选择容量目标或清空缓存。默认清理目标为 256 MB；当前播放或下载中的视频可能暂时超过目标。账号和观看记录保留在配置目录。

## 更新

本仓库沿用 Chrysalism 的发布结构：`pluginmaster.json` 指向固定版本标签中的 `Vignette.zip`，由卫月安装器检查和安装更新。ZIP 内的 `host/`、`core/` 为运行依赖，不能只提取主 DLL。

本仓库存放安装文件和仓库索引；开发源码、构建工具、测试视频、账号资料与本机缓存不随仓库上传。

第三方组件来源和已知限制见 [THIRD-PARTY.md](THIRD-PARTY.md)。

Create by Luno
