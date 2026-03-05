# GitHub Download Page

A single-file, zero-dependency download page for GitHub releases. Drop `index.html` into your repo (or serve it via GitHub Pages) and it instantly becomes a polished, platform-aware download landing page for your app.

## Sample

 ![Sample download page](https://github.com/user-attachments/assets/ba704f43-59eb-491c-a529-c6257f889482)

## Features

- **Platform detection** — detects the visitor's OS and CPU architecture (x64 / arm64) and highlights the best download automatically.
- **Smart Linux support** — detects distro family (DEB vs RPM) to suggest the right package format.
- **Live release data** — fetches the latest release from the GitHub API and classifies assets by OS, architecture, and file type.
- **Caching** — uses `sessionStorage` + ETags so repeated visits avoid redundant API calls.
- **Fully self-contained** — one HTML file, no build step, no external dependencies.

## Usage

1. Copy `index.html` into your project (e.g. the `docs/` folder, or a dedicated `gh-pages` branch).
2. Edit the `CONFIG` object near the top of the `<script>` tag:

```js
const CONFIG = {
  repo:        'user/repo',       // GitHub repo in "owner/repo" format
  name:        'My App',          // Display name shown in the hero
  tagline:     'Short description of your app',
  icon:        'icon.png',        // Path to app icon (or set to null to hide)
  license:     'MIT License',     // Shown in the footer (or set to null to hide)
  accent:      '#1da0c3',         // Primary brand colour (hex)
  accentHover: '#25b8de',         // Hover colour (optional)
};
```

1. Publish the file. That's it.

## Asset Naming Convention

The page classifies release assets automatically based on their filenames. For best results, name your assets using the following patterns:

| Platform | Pattern examples |
|----------|-----------------|
| Windows  | `app-windows-x64.exe`, `app-windows-arm64.msi` |
| macOS    | `app-mac-x64.dmg`, `app-macos-arm64.dmg` |
| Linux    | `app-linux-x64.AppImage`, `app-linux-arm64.deb`, `app-linux-x64.rpm` |
| Android  | `app.apk`, `app.aab` |
| iOS      | `app.ipa` |

Formats that are automatically skipped (not shown as downloads): `.blockmap`, `.yml`, `.yaml`, `.zsync`, `.zip`.

## Preferred Download Formats

The hero CTA button and per-platform card ordering favour these formats by default:

| OS      | Preferred format |
|---------|-----------------|
| Windows | `.exe`          |
| macOS   | `.dmg`          |
| Linux   | `.AppImage` (or `.deb` / `.rpm` when a matching distro is detected) |
| Android | `.apk`          |

## GitHub Pages Setup

1. Go to **Settings → Pages** in your repo.
2. Set the source to the branch/folder that contains `index.html`.
3. The page will be live at `https://<owner>.github.io/<repo>/`.

## License

MIT
