# HB SUPER APP 7.5

All-in-one Android app by **HB Software** — downloads, a real WebView browser, a media player, a file manager, a converter, smart tools and a status saver in one premium dark interface.

[![Latest release](https://img.shields.io/github/v/release/HBSoftware63/hb-aio?label=download)](https://github.com/HBSoftware63/hb-aio/releases/latest)

- Package: `com.example.videodownloader` (kept from 7.4 so updates install over the old app)
- Version: `7.5` (`versionCode 26`)
- Android 10 (API 29) or newer, targets Android 14 (API 34), compiled with SDK 35
- Credit: **Hakim Zaib**

## What's new in 7.5

- Complete redesign: dark navy / black surfaces, HB Blue accent, rounded cards, light / dark / system themes, responsive layouts.
- New five-tab shell: **Home · Downloads · Browser · Tools · Library**, with Settings, global search, notifications and the update center.
- **HB Browser** built in, now with a Chrome-style layout: one top toolbar (lock icon + address pill, tab counter, three-dot menu), Chrome-style start page with shortcuts, tab grid with thumbnails, incognito theme, auto-hiding toolbar, pull-to-refresh, bookmarks, history, search engines, find-in-page, reader mode, desktop mode, dark pages, permission prompts, ad/tracker blocking and hardened WebView settings.
- **Browser video downloader**: download from YouTube, Instagram, TikTok, Facebook, X, Reddit, Vimeo, Dailymotion, Pinterest, Snapchat, Threads, Twitch, Likee and LinkedIn through yt-dlp — Video / Audio (MP3), a real quality picker, automatic detection of `.mp4`/`.m3u8`/`.mpd`/`.webm` links with a count badge, "Download all" for playlists and channels, a download icon on every video element, and optional browser-login cookies (never logged, deleted when the download ends). Browser-started downloads appear in the Downloads tab.
- **Media Player** rebuilt on Media3 ExoPlayer: video and music, queue/playlist, subtitles, speed, aspect ratio, screen lock, gestures, PiP, background audio and resume position.
- **Library** screen with videos, music, photos, recent playback and bookmarks.
- **File Manager** using modern SAF APIs: browse, search, sort, multi-select, rename, copy, move, delete with confirmation, ZIP create/extract, categories and storage overview.
- **Converter Studio**: video → MP3, audio conversion (MP3/M4A/WAV), audio/video trim, video compression, video → GIF, image conversion/compression (JPG/PNG/WEBP), images → PDF; all real FFmpeg / on-device work with progress and cancel.
- **Tools**: QR scan and generate, offline PDF viewer, image viewer, ringtone maker, clipboard link detector, storage analyzer, file search and text tools.
- **Status Saver** improved (WhatsApp / WhatsApp Business / already-saved statuses, with direct folder access through SAF).
- Settings for theme, download folders, quality, Wi-Fi only, browser search engine / home / text size / downloads / ad blocking / tab restore / private data, player, storage, notifications, privacy and updates. The interface is English-only.
- Update system kept and hardened: background APK download survives app close, HTTP Range resume, SHA-256 verification, one-tap install, mandatory updates.

## Install

Download `app-release.apk` from the [Releases page](https://github.com/HBSoftware63/hb-aio/releases/latest) and install it. You may need to allow *Install unknown apps* for your browser or file manager. Updates install over 7.4 without uninstalling because the package name and signing key are unchanged.

## Feature tour

### Home

Branded dashboard with global search, quick actions (customizable), active download queue with pause / resume / cancel, recent downloads, recently opened media, favorite tools, storage usage with Analyze / Files shortcuts, and a rotating set of browser/player/file-manager/converter/QR shortcuts.

### Downloads Pro

- Video and audio downloads through yt-dlp + FFmpeg (youtubedl-android).
- Multiple links at once, queue, duplicate protection, background service, notifications.
- Pause / resume / cancel from the app or notification. Pause stops the yt-dlp process and keeps the `.part` file; resume continues it.
- Wi-Fi-only mode that also re-pauses if Wi-Fi drops mid-download, weak-internet wait and retry, integrity/size checks, clipboard link detection.
- History with search, file sizes, open/share/re-download/delete, custom save folders.
- yt-dlp engine self-update; FFmpeg bundled with the downloader library.

### HB Browser

Real WebView browser with a premium start page.

- Tabs overview, switch, close; tabs restore after restart (normal tabs only, never private ones).
- Back / forward / refresh / stop / home / desktop / fullscreen, progress, URL bar with search.
- Search engines: Google, Bing, DuckDuckGo, Yahoo.
- Downloads through Android DownloadManager (cookies, user agent and referer forwarded), SAF download folder, duplicate file names handled, retry and cancel.
- Bookmarks and history with folders, search, add/edit/delete.
- Private tabs: never saved, never written to history; cookies/storage/cache cleared when private tabs close, when leaving the browser (optional setting) and always after the last private tab; a crash marker clears leftover private data on the next launch.
- Security hardening: SSL errors are **always cancelled**, no file/content URL access from pages, pop-ups require a user gesture, JavaScript and DOM storage limited to normal browsing, `clipboard`/`geo`/`camera`/`mic` prompts controlled by permission rules, narrow ad/tracker host block list, cleartext HTTP only for user-typed pages.
- Find in page, reader mode, share / copy / open link in new tab / download link, text zoom, algorithmic darkening, page permission prompts.

### Media Player

Media3 ExoPlayer with MediaSessionService, video and music playback, queue/playlist, MediaStore library picker, subtitles from local files, speed (0.5×–2×), aspect ratio modes, screen lock, tap/double-tap gestures, PiP, background audio toggle, resume position, recent list and decoder fallback.

### Library

Videos, music, photos and documents categories, recent playback with resume position, saved bookmarks, downloads shortcut, and storage overview. Files open in the player, image viewer or PDF viewer as appropriate.

### File Manager

Browse internal storage and SAF folders, categories (videos, music, photos, documents, downloads, APK, other), search, sort, multi-select, rename, copy, move, delete confirmation, share, new folder, ZIP create/extract, open with another app, and a storage bar.

### Converter Studio

All options are working conversions on local files:

| Tool | Output |
|---|---|
| Video → MP3 | MP3 |
| Trim video / audio | MP4 / MP3 |
| Compress video | smaller H.264 MP4 (three strengths) |
| Video → GIF | GIF (first 10 s or whole video) |
| Convert audio | MP3, M4A/AAC, WAV |
| Convert / compress image | JPG, PNG, WEBP with quality slider |
| Images → PDF | one page per image |

Progress uses FFmpeg's `-progress` stream; Cancel destroys the process. Results are published to the media library (Music/Movies/Pictures/Downloads → HB Converter) or copied to a chosen SAF folder.

### Smart tools

QR scanner (camera + gallery decode), QR generator, offline PDF viewer, image viewer, ringtone maker, clipboard URL detector, storage analyzer, file search and text tools. Everything runs on-device.

### Status Saver

WhatsApp and WhatsApp Business statuses plus the ones already saved on the phone. Access is granted by the user through Android's folder picker (SAF) or "All files access"; saved copies go to the phone's own storage. The app does not read private WhatsApp databases or bypass app security.

### Settings

Appearance, download preferences, browser preferences, player, storage and cache, notification settings, permissions explanation, privacy, about, update check, yt-dlp update and update source. Firebase/Admin Panel is documented as a future, optional integration.

## Permissions

| Permission | Why it is used |
|---|---|
| `INTERNET`, `ACCESS_NETWORK_STATE` | Downloads, browser pages, update checks, yt-dlp |
| `FOREGROUND_SERVICE`, `FOREGROUND_SERVICE_DATA_SYNC`, `FOREGROUND_SERVICE_MEDIA_PLAYBACK`, `POST_NOTIFICATIONS` | Download/update progress and media playback in the background |
| `READ_MEDIA_VIDEO`, `READ_MEDIA_AUDIO`, `READ_MEDIA_IMAGES` (and legacy storage read) | Library, player, image viewer, ringtone maker |
| `MANAGE_EXTERNAL_STORAGE` | Direct access to the WhatsApp `.Statuses` folder (optional; SAF is offered instead) |
| `WRITE_SETTINGS` | Set a downloaded MP3 as ringtone / notification / alarm |
| `REQUEST_INSTALL_PACKAGES` | Install app updates |
| `CAMERA` | QR scanning only; websites are blocked from camera/microphone by the app |

Backups are disabled (`allowBackup=false`) so history, bookmarks, cookies and settings are not uploaded to cloud backup.

## Privacy and security

- Downloads, history, bookmarks, playlists and settings stay on the device. Browsing history is **never** uploaded.
- The only network traffic is: pages the user opens, downloads the user starts, update metadata/APK, and optional yt-dlp engine updates.
- The app does not bypass DRM, paywalls or access restrictions. Download only content you are authorized to use.
- SSL certificate errors are never ignored.
- Websites cannot read local files: `allowFileAccess` and `allowContentAccess` are off, and only http/https navigations are allowed in the browser.
- No Firebase SDK, service account key or server secret is included in this build.
- Private browsing limitation: Android WebView shares one cookie jar across all WebViews in the process. The app clears cookies, local storage, form data and cache when private sessions end (and after an app kill via a crash marker), which is the strongest isolation WebView allows — but it can also sign the user out of normal tabs. This is explained in-app under Settings → Private browsing.

## Updates

On launch the app reads [`update.json`](update.json) from this repository and compares `versionCode` with its own. A higher number triggers the mandatory update flow.

- `UpdateService` downloads the APK in a foreground service; closing the app, switching away or locking the phone does not stop it.
- A partial file resumes with HTTP `Range`, also after a process kill or reboot.
- SHA-256 from `update.json` is verified before install; a mismatch discards the file.
- The APK is kept in `filesDir/app_update`, so reopening the app offers **Install** with no new download.
- Android always shows at least one installer confirmation; `USER_ACTION_NOT_REQUIRED` removes the extra in-app confirmation where Android allows it.
- Signing keys and the package name never change, so updates install over the previous version.

The live repository URL is `https://raw.githubusercontent.com/HBSoftware63/hb-aio/main/update.json` (set in `Updater.kt`). The committed `update.json` is now set to 7.5 / 26, but it must only be pushed after `app-release.apk` for `v7.5` is actually uploaded to Releases — this app treats any newer `versionCode` in `update.json` as a compulsory update, so a pushed JSON with a dead APK link locks 7.4 users out until a working link appears.

### `update.json` example for 7.5

See [`update.example.json`](update.example.json). The real `sha256` is filled by the release workflow.

```json
{
  "versionCode": 26,
  "versionName": "7.5",
  "apkUrl": "https://github.com/HBSoftware63/hb-aio/releases/download/v7.5/app-release.apk",
  "minVersionCode": 26,
  "notes": "HB SUPER APP 7.5 ...",
  "sha256": "<filled automatically by the release workflow>"
}
```

## Build

Requirements: JDK 17, Android SDK (platform 35, build-tools), internet for dependencies.

```bash
export KEYSTORE_PATH=/path/to/hbkey.jks
export KEYSTORE_PASSWORD=...
export KEY_ALIAS=hbkey
export KEY_PASSWORD=...
./gradlew assembleRelease
```

Debug build without signing:

```bash
./gradlew assembleDebug
```

Output:

- Debug: `app/build/outputs/apk/debug/app-debug.apk`
- Signed release (with `KEYSTORE_*`): `app/build/outputs/apk/release/app-release.apk`
- Unsigned release (no keystore): `app/build/outputs/apk/release/app-release-unsigned.apk`

Release builds are signed from the `KEYSTORE_*` environment variables (same keystore as 7.4). Without them the release APK is unsigned and cannot be installed over an existing copy. If Maven resolution is slow or fails, add `-Djava.net.preferIPv4Stack=true`.

## Release with GitHub Actions

`.github/workflows/release.yml` builds, signs, publishes the GitHub Release and updates `update.json`.

**One-time setup**

1. Repository → Settings → Secrets and variables → Actions:
   - `KEYSTORE_BASE64` (keystore encoded with base64)
   - `KEYSTORE_PASSWORD`
   - `KEY_ALIAS`
   - `KEY_PASSWORD`
2. Settings → Actions → General → Workflow permissions → **Read and write permissions**.

**Each release**

1. Increase `versionCode` and change `versionName` in `app/build.gradle.kts`, update `release_notes.txt`, push.
2. Actions → **Build APK + Release + Update JSON** → **Run workflow**. Optionally type notes; force update is always on.
3. The workflow checks the version, builds the signed APK, creates release `v<versionName>`, uploads the APK, then rewrites `update.json` with the real URL and SHA-256.

Do not edit `update.json` by hand before the APK exists, and never change the signing key.

## Project structure

```
app/src/main/java/com/example/videodownloader/
├── MainActivity.kt, HbApp.kt, Prefs.kt
├── screens/        Home, Downloads, Tools, Library (tab screens)
├── browser/        BrowserScreen, BrowserStore, BrowserUrl, BrowserDownloads(+Activity)
├── player/         PlayerActivity, PlaybackService (Media3)
├── files/          FileManagerActivity, FileSearchActivity, StorageAnalyzerActivity
├── converter/      ConverterActivity (FFmpeg)
├── tools/          QR, PDF, image, text, clipboard
├── settings/       SettingsActivity
├── ui/             Hb design system, BaseActivity, Screen, locale
├── util/           Tool registry, Format, MediaIndex, Launcher, RecentStore
└── update layer    Updater, UpdateStore, UpdateService, InstallUpdateActivity, UpdateInstallReceiver
```

New features should be added as activities/screens behind the `Tool` registry or a tab screen, which keeps the app ready for a future Admin Panel / remote configuration layer without restructuring.

## Known limitations (7.5)

- No Admin Panel and no Firebase integration; the app is fully local.
- Android WebView shares one cookie jar across the process. Private tabs never write history and their data is cleared, but clearing can also sign the user out of normal tabs; this is documented in-app.
- DRM-protected playback is not supported in the browser or player, and the downloader does not bypass DRM, paywalls, logins or access restrictions. Site support depends on yt-dlp.
- Ad/tracker blocking uses a small, transparent host list, not a full filter engine.
- Video → GIF produces a silent GIF (no audio track).
- Browser history, bookmarks, downloads and settings are stored only on the device; there is no sync or cloud backup.
- No runtime/device testing was possible in the development environment (see below).

## Testing status

Only compile/build verification was possible in the development environment (no Android emulator, AVD or physical device was available). **No runtime/UI behavior was tested on a device in this build.** See [`TESTING_7.5.md`](TESTING_7.5.md) for the exact test matrix and a manual checklist for the browser and the rest of the app.

## Firebase (future, optional)

7.5 works fully without Firebase. No SDK, key or secret is included. Planned optional modules and the rules for adding them are documented in [`FIREBASE_INTEGRATION.md`](FIREBASE_INTEGRATION.md). An Admin Panel is planned for a future version and is not part of this build.

## Tech stack

Kotlin, AndroidX AppCompat, programmatic View UI, ViewModel-free lifecycle-aware coroutines, Media3 ExoPlayer 1.5.1, AndroidX WebKit 1.11.0, youtubedl-android 0.18.1 (yt-dlp + FFmpeg), ZXing, DocumentFile/MediaStore, Gradle 8.7, AGP 8.5.2, JDK 17.

## Disclaimer

Download only content you own or have permission to download, and respect each site's terms of service. The app does not bypass DRM, paywalls or access restrictions.

---

Publisher: **HB Software** · Credit: **Hakim Zaib**
