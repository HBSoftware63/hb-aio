# All In One Downloader (HB AIO)

Android app by **HBSoftware** to download videos and MP3 from many sites, save WhatsApp statuses, and set a downloaded MP3 as a ringtone.

[![Latest release](https://img.shields.io/github/v/release/HBSoftware63/hb-aio?label=download)](https://github.com/HBSoftware63/hb-aio/releases/latest)

## Download

Get the latest `app-release.apk` from the [Releases page](https://github.com/HBSoftware63/hb-aio/releases/latest) and install it. You may need to allow "Install unknown apps" for your browser or file manager.

Requires Android 10 (API 29) or newer.

## Features

- Download videos and MP3 (powered by yt-dlp and FFmpeg through youtubedl-android)
- Choose where videos and MP3 are saved, with a separate YouTube folder
- Set a downloaded MP3 as ringtone, notification or alarm
- WhatsApp status saver (reads the `.Statuses` folder directly, needs "Allow file access")
- Download history
- Share a link to the app to start a download
- "Download only on Wi-Fi" option (waits for Wi-Fi to save mobile data)
- yt-dlp updates itself in the background (every 3 days) so downloads keep working
- Paste several links at once, all of them download (the same link is never downloaded twice)
- Built-in updater: the app checks `update.json` on start, offers new versions and verifies the APK checksum

## Permissions

| Permission | Why |
|---|---|
| Internet / network state | Downloading and update checks |
| Foreground service (data sync) and notifications | Show download progress |
| All files access / read storage | WhatsApp status saver |
| Write settings | Set MP3 as ringtone |
| Install packages | Install updates from inside the app |

## How updates work

On launch the app reads [`update.json`](update.json) from this repo and compares `versionCode` with its own. If the JSON number is higher, an "Update available" dialog appears and the APK from `apkUrl` is downloaded and installed.

```json
{
  "versionCode": 22,
  "versionName": "7.1",
  "apkUrl": "https://github.com/HBSoftware63/hb-aio/releases/download/v5/app-release.apk",
  "minVersionCode": 0,
  "notes": "What's new",
  "sha256": "checksum of the APK (added automatically by the workflow)"
}
```

`versionCode` is the number the app compares (must grow with every release), `versionName` is only the text shown to users, and the `v5` in `apkUrl` is the Release tag you type when running the workflow (not the version). `minVersionCode` equal to `versionCode` makes the update mandatory. The JSON link is set in `Updater.kt` (`UPDATE_JSON_URL`).

## Build and release (GitHub Actions)

APK build, GitHub Release and `update.json` update are automated by `.github/workflows/release.yml`.

**One-time setup**

1. Repo **Settings > Secrets and variables > Actions**, add:
   - `KEYSTORE_BASE64` (your keystore file encoded with base64)
   - `KEYSTORE_PASSWORD`
   - `KEY_ALIAS`
   - `KEY_PASSWORD`
2. **Settings > Actions > General > Workflow permissions**: select *Read and write permissions*.

Always sign with the same keystore, otherwise users get "App not installed" when updating. Never commit the keystore.

**For every new version**

1. In `app/build.gradle.kts` increase `versionCode` and change `versionName`. Write the update text in `release_notes.txt`, then push.
2. Open **Actions > Build APK + Release + Update JSON > Run workflow**. Type the release tag (e.g. `v5`, use a new tag for every version) and optionally notes, or tick *force update*.
3. The workflow builds the signed APK, publishes it as the release tag you typed (e.g. `v5`), then updates and commits `update.json`.

Urdu step-by-step guide: [README_URDU.md](README_URDU.md)

## Local build

```bash
export KEYSTORE_PATH=/path/to/hbkey.jks
export KEYSTORE_PASSWORD=...
export KEY_ALIAS=hbkey
export KEY_PASSWORD=...
./gradlew assembleRelease
```

The APK is created at `app/build/outputs/apk/release/app-release.apk`. Without the `KEYSTORE_*` variables the release APK is unsigned. Requires JDK 17 and the Android SDK (compileSdk 34).

## Tech stack

Kotlin, AndroidX, Kotlin coroutines, [youtubedl-android](https://github.com/yausername/youtubedl-android) (yt-dlp + FFmpeg), Gradle 8.7, Android Gradle Plugin 8.5.2.

## Disclaimer

Download only content you own or have permission to download, and respect the terms of service of each site.

---

Publisher: HBSoftware
