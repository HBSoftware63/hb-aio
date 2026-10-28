# HB AIO Downloader v21

A powerful Android downloader designed to make downloading and sharing content simple and convenient.

## Features

- One-click download workflow
- Easy-to-use interface
- Quick sharing and download handling
- Automatic update checking through `update.json` (if configured)
- Android APK distribution through GitHub Releases

## Download

Download the latest APK from the [GitHub Releases](https://github.com/HBSoftware63/hb-aio/releases) page.

## Installation

1. Download the APK from Releases.
2. Open the downloaded APK on your Android device.
3. Allow installation from this source if Android asks.
4. Install and launch the app.

## Automatic APK Build

This project can use GitHub Actions to build the Android APK automatically.

1. Open the repository on GitHub.
2. Go to the **Actions** tab.
3. Run the available build workflow or push a commit.
4. Download the generated APK from the workflow's **Artifacts** section.

*Automatic builds require a correctly configured GitHub Actions workflow and Android build environment.*

## Update Configuration

The `update.json` file can be used to provide update information to the app, provided the app's update-checking code supports the same JSON format.

Example:

```json
{
  "versionCode": 21,
  "versionName": "21",
  "downloadUrl": "https://github.com/HBSoftware63/hb-aio/releases/download/v4/app-release.apk",
  "releaseNotes": "Bug fixes and improvements"
}
```

**Important:** Update the version and APK URL whenever you publish a new release. The JSON field names must match the format expected by the app.

## Repository

Source code and releases:  
https://github.com/HBSoftware63/hb-aio

## Disclaimer

Use this application responsibly and respect the terms of service and copyright rules of the websites you access. Only download content you are authorized to download.

## License

Add the appropriate license file and license details for this project.
