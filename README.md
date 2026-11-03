<p align="center">
  <img src="Clipth/Assets.xcassets/AppLogo.imageset/AppLogo@2x.png" width="96" alt="Clipth" />
</p>

<h1 align="center">Clipth</h1>

<p align="center">
  <strong>The local-first clipboard manager for macOS — with offline semantic search and a built-in MCP server for your AI tools.</strong>
</p>

<p align="center">
  <a href="https://clipth.app"><img src="https://img.shields.io/badge/Download-macOS%2014%2B-black?logo=apple" alt="Download for macOS" /></a>
  <a href="https://github.com/wavever/Clipth/stargazers"><img src="https://img.shields.io/github/stars/wavever/Clipth?style=flat" alt="Stars" /></a>
  <a href="https://github.com/wavever/Clipth/actions/workflows/ci.yml"><img src="https://github.com/wavever/Clipth/actions/workflows/ci.yml/badge.svg" alt="CI" /></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-yellow.svg" alt="MIT" /></a>
</p>

<p align="center"><strong>English</strong> · <a href="README.zh-CN.md">中文</a> · <a href="https://clipth.app">clipth.app</a></p>

## Get started

1. **[Download the DMG](https://clipth.app)** and drag Clipth to Applications.
2. Press **⌘⇧V** anywhere to open your history.
3. *(Optional)* Settings → AI → one click to connect Claude Code, Cursor, Codex, and 12 more via MCP.

## Why Clipth?

- **Local-first** — history, OCR text, tags, and embeddings stay on your Mac. Encrypted sync stays off until you turn it on.
- **Search by meaning, offline** — Apple `NLEmbedding`, no cloud embedding API.
- **AI-native** — the app binary is an MCP server your tools can call.
- **Secrets auto-redacted** — API keys and phone numbers are masked in the UI, exports, and MCP. The original stays on your Mac.
- **Encrypted sync that merges** — iCloud Drive, WebDAV, S3-compatible storage, or a folder you choose, with AES-256-GCM.
- **Truly native** — SwiftUI menu bar app, with Quick Paste, widgets, previews, and snippets.
- **Privacy controls** — pause capture, exclude source apps, ignore sensitive pasteboard markers, strip URL trackers, disable MCP tools, and delete history.

The name comes from “clip path”: a trail of things you copied.

## Preview

These screenshots show the Chinese interface.

<table>
  <tr>
    <td align="center" width="50%">
      <img src="assets/screenshots/board-mainpage-lits-cn-transparent.png" alt="Main window, list layout" width="380" /><br />
      <sub>Main window · list</sub>
    </td>
    <td align="center" width="50%">
      <img src="assets/screenshots/board-mainpage-list-cn-transparent.png" alt="Main window, grid layout" width="380" /><br />
      <sub>Main window · grid</sub>
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="assets/screenshots/board-quick-copy-cn-transparent.png" alt="Quick Paste" width="380" /><br />
      <sub>Quick Paste</sub>
    </td>
    <td align="center">
      <img src="assets/screenshots/board-mcp-cn-transparent.png" alt="MCP setup in Settings" width="380" /><br />
      <sub>MCP in Settings</sub>
    </td>
  </tr>
</table>

<details>
<summary>More screenshots</summary>

<table>
  <tr>
    <td align="center" width="33%">
      <img src="assets/screenshots/board-filter-cn-transparent.png" alt="Filters" width="280" /><br />
      <sub>Filters</sub>
    </td>
    <td align="center" width="33%">
      <img src="assets/screenshots/board-widget-cn-transparent.png" alt="macOS widgets" width="280" /><br />
      <sub>Widgets</sub>
    </td>
    <td align="center" width="33%">
      <img src="assets/screenshots/board-website-preview-cn-transparent.png" alt="Link preview" width="280" /><br />
      <sub>Link preview</sub>
    </td>
  </tr>
</table>

</details>

<details>
<summary>Features</summary>

### Capture and Reuse

- Auto-captures text, images, video, files, URLs, and rich text
- Double-click to copy an entry back to the clipboard
- Duplicate refresh keeps re-copied items at the top instead of creating duplicates
- Optional paste-as-plain-text and trailing-whitespace trimming
- Soft-delete trash with restore, permanent delete, and retention controls
- Global hotkeys for the main window and snippets
- Efficient image storage — clipboard images are kept compressed with external binary storage, so memory and disk usage stay low even with a long image history
- Switch between list and grid layouts: the main window uses a responsive grid, while Quick Paste and the menu bar panel offer independently configurable two-column grids in Settings. Grid image previews preserve their aspect ratio and show the image name as an in-place overlay.

### Search and Organization

- Full-text search with type filters
- Offline semantic search over text and OCR content
- Source-app and time filters such as `app:Safari`, `since:2d`, and `before:2026-05-01`
- Favorites, pinned clips, tags, custom titles, and tag autocomplete
- Multi-select merge for clips of the same type

### Content Awareness

- Rich preview popover
- OCR indexing for images
- Smart text parsing for timestamps, Base64, and JSON
- Video preview with thumbnail or inline player mode
- URL tracking-parameter stripping for `utm_*`, `fbclid`, `gclid`, and more
- Screen-recording hide mode for the app window

### Content Protection

- Automatic, conservative redaction of sensitive spans: Chinese mainland phone numbers (`13812345678` → `138****5678`) and API keys, tokens, secrets, and passwords — labeled values such as `appkey=…` plus high-confidence prefixes like `sk-`, `ghp_`, `AKIA`
- Masks only the sensitive value while keeping surrounding labels and structure; conservative enough to leave UUIDs, hashes, timestamps, and ordinary URLs untouched
- Redacted display across the history list, previews, menu bar, Dynamic Island, Quick Paste, Quick Look, and search snippets, with a lock badge on protected clips
- The original value is never modified in storage — copy, quick paste, paste-as-plain-text, and edits still use the raw clip
- Default exports and MCP responses return redacted content with `isProtected` metadata; raw egress requires an explicit opt-in
- Master switch and one editable rule list in Settings → Data → Privacy: the built-in phone/app-key rules can be edited, reset, or turned off, alongside your own keyword or regex rules

### Export and Stats

- JSON export with type, date, favorite, and pinned filters
- Per-item export to original formats such as text and PNG
- Copy statistics, 14-day chart, and GitHub-style yearly heatmap

</details>

<details>
<summary>Encrypted sync that merges, not overwrites</summary>

Clipth does not replace one Mac's entire database with another. It sends encrypted incremental operations, merges each field independently, and keeps a recoverable copy when two devices change non-mergeable content.

Choose automatic sync or keep it manual. The main window always exposes a compact sync state: one-click sync when automation is off, an immediate in-progress indicator, and explicit success or failure feedback when the run finishes.

| What happens | How Clipth protects it |
|---|---|
| Two Macs edit different fields | Hybrid logical clocks and field versions preserve both changes |
| Both devices write at once | Immutable encrypted journals survive the snapshot race |
| Tags or group membership change independently | Convergent set merging combines additions and preserves removals |
| A device returns with stale data | Acknowledged tombstones prevent deleted clips from silently reappearing |

Everything is encrypted locally with AES-256-GCM before it reaches iCloud Drive, WebDAV, S3-compatible storage, or your chosen sync folder. The losing version is retained as an encrypted conflict copy for 30 days, while old journals and orphan attachments are cleaned conservatively. [Read the sync architecture →](https://github.com/wavever/clipth-website/blob/main/docs/sync-architecture.md)

- Optional bidirectional sync through iCloud Drive, WebDAV, S3-compatible object storage, or a local folder (including folders managed by Dropbox, OneDrive, Syncthing, and network drives)
- Manual or automatic sync with a compact main-window status, immediate progress feedback, and clear success or failure notifications
- AES-256-GCM end-to-end encryption before data leaves the Mac; WebDAV passwords, S3 secret credentials, and the 256-bit recovery key are stored in Keychain
- Hybrid logical clocks merge independently edited fields; tags and group membership use convergent set merging, while losing content is retained as a 30-day conflict copy
- Encrypted incremental journals protect concurrent writers and compact into conditional-write snapshots; acknowledged deletion tombstones, old journals, and orphan attachments are garbage-collected conservatively
- Syncs history, images, tags, groups, favorites, pins, trash state, and individual file attachments up to 25 MB; device settings, statistics, and semantic vectors remain local
- Another Mac needs the same recovery key. Losing it makes existing remote data unrecoverable.
- Existing v1 manifests are upgraded in place on the next successful sync; the recovery key is reused and the remote `.clipth-sync-v1` location stays stable for Clipth releases.

</details>

## MCP Server

The app binary doubles as an MCP stdio server.

**One-click setup.** Settings → AI lists the agents actually installed on your Mac — CLIs and apps alike — and writes the entry into their config file for you. Supported: Claude Code, Codex CLI, Claude Desktop, Cursor, OpenClaw, VS Code, Zed, Windsurf, Gemini CLI, opencode, Qwen Code, Cline, Kiro, LM Studio, and Amazon Q CLI. The original file is backed up alongside it as `.clipth.bak`, comments and formatting are preserved, and each client's own syntax is used (Codex is TOML, VS Code keys the map `servers`, Zed uses `context_servers`, opencode takes `command` as an array). Restart the client afterwards so it picks Clipth up.

Import never writes straight away: it opens a confirmation dialog showing the exact edit — the affected lines of that config file, in that file's own syntax, with the additions highlighted — and nothing is written until you confirm. Each row can also open its config file in Quick Look or hand it to your editor.

To configure a client by hand instead:

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

Codex uses TOML rather than JSON — in `~/.codex/config.toml`:

```toml
[mcp_servers.clipth]
command = "/Applications/Clipth.app/Contents/MacOS/Clipth"
args = ["--mcp"]
```

<details>
<summary>MCP tools</summary>

| Tool | Description |
|---|---|
| `search_clipboard` | Keyword or semantic search over clipboard history |
| `list_recent` | List recent entries, optionally filtered by type |
| `get_clip` | Fetch one entry by UUID with full content and metadata |
| `list_tags` | List all tags and usage counts |
| `list_recent_activity` | List entries added since an ISO date or relative time such as `30m`, `2h`, `3d`, `1w` |
| `tag_clip` / `untag_clip` | Add or remove tags |
| `favorite_clip` / `pin_clip` | Update favorite or pinned state |
| `delete_clip` / `restore_clip` | Soft-delete, permanently delete, or restore entries |
| `create_snippet` | Create a snippet with optional title and tags |

</details>

Protected clips are redacted in MCP responses by default and carry `isProtected` metadata; returning raw protected content requires an explicit opt-in in Settings → Data → Privacy. MCP can still expose other clipboard contents to the client you configure — read [PRIVACY.md](PRIVACY.md) before enabling it for sensitive workflows.

## Install

Download the latest DMG from [clipth.app](https://clipth.app), open it, and drag Clipth into Applications.

<details>
<summary>macOS says the app can't be opened?</summary>

Public releases are signed with a stable self-signed identity so Accessibility permission can survive updates. They are not notarized yet; notarization is on the roadmap. Gatekeeper may say the developer cannot be verified.

Move Clipth to `/Applications`, then either right-click the app and choose **Open**, or clear the download quarantine flag:

```bash
xattr -dr com.apple.quarantine /Applications/Clipth.app
```

You can also build from source below.

</details>

## System Requirements

- macOS 14.0 Sonoma or later
- Xcode 16.0 or later recommended for development

## Build from Source

Open `Clipth.xcodeproj` in Xcode, select "My Mac", and run.

Command line:

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

Release signing for maintainers is documented in [CONTRIBUTING.md](CONTRIBUTING.md#code-signing).

## Keyboard Shortcuts

| Shortcut | Action |
|---|---|
| `⌘⇧V` | Open main window |
| `⌘,` | Open settings |
| `⌘N` | New snippet |
| `⌘⏎` | Save in snippet editor |
| `Esc` | Dismiss preview, go back, or cancel edit |

## Project Docs

- [Privacy](PRIVACY.md)
- [Security policy](SECURITY.md)
- [Contributing](CONTRIBUTING.md)
- [Roadmap](ROADMAP.md)
- [Code of Conduct](CODE_OF_CONDUCT.md)

## Contributing

Issues and pull requests are welcome. Good first areas include documentation, localization, MCP resources/prompts, URL sanitizer tests, search parser tests, and privacy polish.

Before contributing, read [CONTRIBUTING.md](CONTRIBUTING.md). For private security or privacy reports, follow [SECURITY.md](SECURITY.md).

## License

Clipth is released under the [MIT License](LICENSE).

This repository is the open-source edition; Clipth Pro is a separate commercial product, and Pro-only features are not included here.
