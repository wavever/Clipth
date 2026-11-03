<p align="center">
  <img src="Clipth/Assets.xcassets/AppLogo.imageset/AppLogo@2x.png" width="96" alt="剪迹" />
</p>

<h1 align="center">剪迹 / Clipth</h1>

<p align="center">
  <strong>为 macOS 打造的本地优先剪贴板，离线语义搜索 + 内置 MCP，让 AI 直接用你的剪贴板。</strong>
</p>

<p align="center">
  <a href="https://clipth.app"><img src="https://img.shields.io/badge/%E4%B8%8B%E8%BD%BD-macOS%2014%2B-black?logo=apple" alt="下载 macOS 版" /></a>
  <a href="https://github.com/wavever/Clipth/stargazers"><img src="https://img.shields.io/github/stars/wavever/Clipth?style=flat" alt="Stars" /></a>
  <a href="https://github.com/wavever/Clipth/actions/workflows/ci.yml"><img src="https://github.com/wavever/Clipth/actions/workflows/ci.yml/badge.svg" alt="CI" /></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-yellow.svg" alt="MIT" /></a>
</p>

<p align="center"><a href="README.md">English</a> · <strong>中文</strong> · <a href="https://clipth.app">clipth.app</a></p>

## 开始使用

1. **[下载 DMG](https://clipth.app)**，把剪迹拖进「应用程序」。
2. 在任意地方按下 **⌘⇧V**，打开剪贴板历史。
3. *（可选）* 设置 → AI，一键通过 MCP 接入 Claude Code、Cursor、Codex，以及另外 12 个客户端。

## 为什么是剪迹？

- **本地优先** — 历史、OCR 文本、标签和语义向量都留在你的 Mac 上。加密同步默认关闭，除非你自己打开。
- **离线按语义搜索** — 使用 Apple `NLEmbedding`，不调用云端 embedding API。
- **为 AI 而生** — 应用本体就是 MCP 服务器，你的 AI 工具可以直接调用。
- **敏感信息自动脱敏** — API 密钥和手机号在界面、导出和 MCP 中默认打码，原文仍留在本机。
- **加密同步会合并** — iCloud 云盘、WebDAV、S3 兼容存储，或你指定的文件夹，AES-256-GCM。
- **真正的原生应用** — SwiftUI 菜单栏应用，带快速粘贴、小组件、预览和片段。
- **隐私开关** — 暂停捕获、排除来源 App、忽略敏感 pasteboard 标记、剥离 URL 跟踪参数、关闭 MCP 工具、删除历史。

名字来自 “clip path”（剪贴路径），中文叫「剪迹」：你复制过的东西留下的一条痕迹。

## 预览

下面是简体中文界面。

<table>
  <tr>
    <td align="center" width="50%">
      <img src="assets/screenshots/board-mainpage-lits-cn-transparent.png" alt="主窗口列表布局" width="380" /><br />
      <sub>主窗口 · 列表</sub>
    </td>
    <td align="center" width="50%">
      <img src="assets/screenshots/board-mainpage-list-cn-transparent.png" alt="主窗口网格布局" width="380" /><br />
      <sub>主窗口 · 网格</sub>
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="assets/screenshots/board-quick-copy-cn-transparent.png" alt="快速粘贴" width="380" /><br />
      <sub>快速粘贴</sub>
    </td>
    <td align="center">
      <img src="assets/screenshots/board-mcp-cn-transparent.png" alt="设置中的 MCP" width="380" /><br />
      <sub>设置里的 MCP</sub>
    </td>
  </tr>
</table>

<details>
<summary>更多截图</summary>

<table>
  <tr>
    <td align="center" width="33%">
      <img src="assets/screenshots/board-filter-cn-transparent.png" alt="筛选" width="280" /><br />
      <sub>筛选</sub>
    </td>
    <td align="center" width="33%">
      <img src="assets/screenshots/board-widget-cn-transparent.png" alt="macOS 小组件" width="280" /><br />
      <sub>小组件</sub>
    </td>
    <td align="center" width="33%">
      <img src="assets/screenshots/board-website-preview-cn-transparent.png" alt="链接预览" width="280" /><br />
      <sub>链接预览</sub>
    </td>
  </tr>
</table>

</details>

<details>
<summary>功能特性</summary>

### 捕获与复用

- 自动捕获文字、图片、视频、文件、链接、富文本
- 双击条目即可写回剪贴板
- 重复复制已有内容时自动浮到顶部，不产生重复记录
- 支持粘贴为纯文本、复制时清理末尾空白
- 软删除垃圾桶，可恢复、彻底删除、按保留期自动清理
- 主窗口和片段支持全局快捷键
- 图片以压缩格式 + 外置存储保存，历史再多也能保持较低的内存与磁盘占用
- 支持列表与网格布局切换：主窗口使用自适应网格，快速粘贴与菜单栏面板可在设置中分别启用双列网格；网格图片预览保持原始宽高比，并以浮层显示图片名称

### 搜索与整理

- 全文搜索与类型过滤
- 对文字和 OCR 内容进行离线语义搜索
- 支持 `app:Safari`、`since:2d`、`before:2026-05-01` 等来源和时间过滤
- 收藏、置顶、标签、自定义标题、标签自动补全
- 同类型条目多选合并

### 内容感知

- hover 富预览
- 图片 OCR 入索引
- 自动识别时间戳、Base64、JSON
- 视频缩略图或内联播放器预览
- 自动剥离 `utm_*`、`fbclid`、`gclid` 等 URL 跟踪参数
- 窗口可隐藏于录屏和屏幕共享

### 内容保护

- 自动且保守地脱敏敏感内容：中国大陆手机号（`13812345678` → `138****5678`）以及 API 密钥、令牌、密码——`appkey=…` 等标签形态，加上 `sk-`、`ghp_`、`AKIA` 等高置信前缀
- 只脱敏敏感值本身，保留标签和上下文结构；对 UUID、哈希、时间戳、普通 URL 不误判
- 列表、预览、菜单栏、Dynamic Island、Quick Paste、Quick Look、搜索摘要均展示脱敏内容，受保护条目带锁形徽标
- 本地存储不改写原文——复制、快速粘贴、复制为纯文本、编辑仍使用原始内容
- 默认导出和 MCP 返回脱敏内容并带 `isProtected` 元数据；外发原文需显式开启
- 设置 → 数据 → 隐私 提供总开关与统一的识别规则列表：内置的手机号 / App Key 规则可编辑、可恢复默认、可停用，也可添加关键词或正则自定义规则

### 导出与统计

- JSON 导出，支持类型、时间、收藏、置顶过滤
- 单条按原始格式导出，例如 text、PNG
- 每日复制次数、14 天柱状图、GitHub 风格年度热力图

</details>

<details>
<summary>会合并，而不是互相覆盖的加密同步</summary>

剪迹不会拿一台 Mac 的整份数据库覆盖另一台。它传输加密的增量操作，逐字段合并修改；当两台设备同时改动无法安全合并的正文时，还会留下可恢复的冲突副本。

你可以选择自动同步，也可以保持手动。主窗口始终用紧凑图标呈现同步状态：关闭自动同步时可一键触发，同步中立即显示进度，完成后会明确提示成功或失败。

| 遇到的情况 | 剪迹的处理方式 |
|---|---|
| 两台 Mac 修改不同字段 | 混合逻辑时钟与字段版本同时保留两边修改 |
| 多台设备同时写入 | 不可变加密日志可跨过快照竞争继续被发现 |
| 标签或分组关系分别变化 | 可收敛集合合并新增项，并保留删除语义 |
| 离线设备带着旧数据回来 | 经设备确认的删除墓碑防止条目静默复活 |

所有数据在到达 iCloud 云盘、WebDAV、S3 兼容存储或同步文件夹前，都会先在本机使用 AES-256-GCM 加密。落败内容会作为加密冲突副本保留 30 天，旧日志与孤儿附件则采用保守策略回收。[阅读同步架构 →](https://github.com/wavever/clipth-website/blob/main/docs/sync-architecture.md)

- 可选的双向同步，支持 iCloud 云盘、WebDAV、S3 兼容对象存储和本地同步文件夹（包括 Dropbox、OneDrive、Syncthing 与网络磁盘目录）
- 支持手动或自动同步；主窗口提供紧凑的同步状态、即时进度反馈以及明确的成功或失败通知
- 数据离开 Mac 前使用 AES-256-GCM 端到端加密；WebDAV 密码、S3 密钥与 256 位恢复密钥保存在钥匙串
- 混合逻辑时钟按字段合并独立修改；标签和分组关系使用可收敛集合合并，落败的正文保留为 30 天冲突副本
- 加密增量日志保护并发写入并压缩为条件写快照；已获设备确认的删除墓碑、旧日志和孤儿附件会被保守回收
- 同步历史、图片、标签、分组、收藏、置顶、垃圾桶状态及单个不超过 25 MB 的文件附件；设备设置、统计和语义向量仍保留在本机
- 另一台 Mac 必须使用同一恢复密钥；密钥丢失后，现有远端数据无法恢复
- 旧版 v1 清单会在下次成功同步时原位升级；恢复密钥会继续复用，远端 `.clipth-sync-v1` 目录在 Clipth 版本中保持稳定

</details>

## MCP Server

应用 binary 同时可以作为 MCP stdio server。

**一键接入。** 设置 → AI 只列出本机真正装了的客户端（CLI 和应用都算），并直接把配置写进它们的配置文件。已支持：Claude Code、Codex CLI、Claude Desktop、Cursor、OpenClaw、VS Code、Zed、Windsurf、Gemini CLI、opencode、Qwen Code、Cline、Kiro、LM Studio、Amazon Q CLI。写入前会把原文件备份为同名的 `.clipth.bak`，并保留原有注释与格式；每个客户端各自的语法也会分别处理（Codex 用 TOML，VS Code 的键是 `servers`，Zed 用 `context_servers`，opencode 的 `command` 是数组）。导入后需重启对应客户端才会加载剪迹。

点「导入」不会立刻写入，而是先弹出确认框展示具体改动 —— 按该配置文件自己的语法显示受影响的那几行，新增部分高亮标出 —— 确认之前不会修改任何文件。每一行也可以直接用速览查看，或用默认编辑器打开配置文件。

也可以手动配置：

```json
{
  "mcpServers": {
    "clipth": {
      "command": "/Applications/Clipth.app/Contents/MacOS/Clipth",
      "args": ["--mcp"]
    }
  }
}
```

Codex 用的是 TOML 而不是 JSON，写在 `~/.codex/config.toml`：

```toml
[mcp_servers.clipth]
command = "/Applications/Clipth.app/Contents/MacOS/Clipth"
args = ["--mcp"]
```

<details>
<summary>MCP 工具</summary>

| 工具 | 用途 |
|---|---|
| `search_clipboard` | 关键词或语义搜索剪贴板历史 |
| `list_recent` | 列出最近条目，可按类型过滤 |
| `get_clip` | 通过 UUID 获取单条完整内容与元数据 |
| `list_tags` | 列出所有标签和使用次数 |
| `list_recent_activity` | 按 ISO 日期或 `30m`、`2h`、`3d`、`1w` 等相对时间列出最近活动 |
| `tag_clip` / `untag_clip` | 添加或移除标签 |
| `favorite_clip` / `pin_clip` | 更新收藏或置顶状态 |
| `delete_clip` / `restore_clip` | 软删除、彻底删除或恢复条目 |
| `create_snippet` | 创建带标题和标签的片段 |

</details>

受保护条目在 MCP 返回中默认脱敏并带 `isProtected` 元数据；返回原文需在 设置 → 数据 → 隐私 中显式开启。MCP 仍会把其它剪贴板内容暴露给你配置的客户端，敏感工作流启用前建议先阅读 [PRIVACY.md](PRIVACY.md)。

## 安装

从官网 [clipth.app](https://clipth.app) 下载最新 DMG，打开后将 Clipth 拖入「应用程序」。

<details>
<summary>macOS 提示无法打开？</summary>

当前公开版本使用稳定的自签名身份签名，以便更新后仍能保留辅助功能权限。尚未公证，公证在路线图中。Gatekeeper 可能会提示无法验证开发者。

先把剪迹放进 `/Applications`，然后右键点按并选择**打开**，或清除下载隔离标记：

```bash
xattr -dr com.apple.quarantine /Applications/Clipth.app
```

也可以按下面的说明从源码构建。

</details>

## 系统要求

- macOS 14.0 Sonoma 或更高版本
- 推荐使用 Xcode 16.0 或更高版本开发

## 从源码构建

用 Xcode 打开 `Clipth.xcodeproj`，选择 "My Mac"，点击运行。

命令行构建：

```bash
xcodebuild \
  -project Clipth.xcodeproj \
  -scheme Clipth \
  -configuration Debug \
  -destination 'platform=macOS' \
  -derivedDataPath build \
  -skipMacroValidation \
  CODE_SIGN_IDENTITY="-" \
  CODE_SIGNING_REQUIRED=NO \
  CODE_SIGNING_ALLOWED=NO \
  build
```

维护者的发布签名说明见 [CONTRIBUTING.md](CONTRIBUTING.md#code-signing)。

## 快捷键

| 快捷键 | 功能 |
|---|---|
| `⌘⇧V` | 打开主窗口 |
| `⌘,` | 打开设置 |
| `⌘N` | 新建片段 |
| `⌘⏎` | 保存片段 |
| `Esc` | 关闭预览、返回或取消 |

## 项目文档

- [隐私说明](PRIVACY.md)
- [安全策略](SECURITY.md)
- [贡献指南](CONTRIBUTING.md)
- [路线图](ROADMAP.md)
- [行为准则](CODE_OF_CONDUCT.md)

## 参与贡献

欢迎提交 issue 和 PR。适合起步的方向包括文档、翻译、MCP resources/prompts、URL sanitizer 测试、搜索解析测试、隐私体验优化。

贡献前请阅读 [CONTRIBUTING.md](CONTRIBUTING.md)。涉及私密安全或隐私问题时，请按照 [SECURITY.md](SECURITY.md) 处理，不要在公开 issue 里粘贴敏感剪贴板内容。

## 许可证

剪迹使用 [MIT License](LICENSE) 开源。

本仓库是开源版本；Clipth Pro 是独立的商业产品，Pro 专属功能不包含在这里。
