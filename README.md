# app-updates
Self-updater backend for my Android apps.

Each app has its own folder containing:
- `version.json` — `versionCode`, `versionName`, `file`, `notes`
- the latest APK, base64-encoded (`.apk.b64`) — the GitHub API here only accepts text, so the app downloads and base64-decodes it on-device

The app checks its `version.json` on launch (at most once a day) and from
Sync > Check for updates. When `versionCode` is higher than the installed
build, it downloads, decodes, and prompts install.

To ship a new version: bump the app, drop the new `.apk.b64` in its folder,
and update `version.json`.
