# 🤖 Muziso Android

<p align="center">
  <img src="assets/logo.png" alt="Muziso Official Logo" width="160" />
</p>

<p align="center">
  <img src="assets/dashboard.png" alt="Muziso Android Dashboard" width="70%" />
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Android%208.0+-3DDC84?style=for-the-badge&logo=android&logoColor=white" alt="Android 8.0+" />
  <img src="https://img.shields.io/badge/Architecture-Kotlin%20%7C%20Jetpack%20Media3-7F52FF?style=for-the-badge&logo=kotlin&logoColor=white" alt="Kotlin Android" />
  <a href="https://github.com/xtros/Muziso-Android/releases"><img src="https://img.shields.io/github/v/release/xtros/Muziso-Android?color=ffffff&label=Release%20v1.0.1&style=for-the-badge" alt="Latest Release v1.0.1" /></a>
  <a href="https://github.com/xtros/Muziso-Android/commit/9f38a405f7e8e002a3653ef7c604f29e2e5fa870"><img src="https://img.shields.io/badge/Build%20%2327-9f38a40-ffffff?style=for-the-badge&logo=githubactions&logoColor=black" alt="Build 27" /></a>
  <a href="https://github.com/xtros/Muziso-Android/blob/main/LICENSE"><img src="https://img.shields.io/badge/License-MIT-ffffff?style=for-the-badge" alt="MIT License" /></a>
</p>

<p align="center">
  <b>Muziso Android</b> is a high-performance native music player engineered for <b>Android 8.0 (Oreo) to Android 15</b>. Built with <b>Native Kotlin</b>, <b>Jetpack Media3 ExoPlayer</b>, and a multi-source resolver pipeline, Muziso delivers sub-30ms 320 kbps streaming, YouTube/Innertube streaming with PO tokens, system-wide lockscreen playback controls, official Spotify 640x640 artwork, synchronized lyrics, and 100% offline local playback.
</p>

---

## 📚 Documentation & Guides

- 🏗️ **[Architecture Guide](docs/ARCHITECTURE.md)**: Deep dive into Android Audio Service, MediaSessionCompat, ExoPlayer, and Room SQLite database.
- ⚡ **[Installation & Sideload Guide](docs/INSTALLATION.md)**: Step-by-step APK sideloading instructions and Gradle compilation.
- 🤝 **[Contributing & Bug Hunter Program](docs/CONTRIBUTING.md)**: Android contribution standards and issue templates.
- 🔒 **[Privacy Policy](docs/PRIVACY.md)**: 100% offline-first privacy architecture, zero telemetry.
- ⚖️ **[Terms & Conditions](docs/TERMS.md)**: Open-source licensing terms and third-party media disclaimers.

---

## 🌟 Key Features (v1.0.1)

- 🚀 **Sub-30ms 320 kbps Streaming**: Direct JioSaavn bitstream resolution with zero buffering delay.
- 📺 **Innertube & YouTube Engine**: Seamless background stream resolution with fallback client profiles (`IPADOS`, `ANDROID_NO_SDK`) and PO tokens.
- 🔔 **Foreground MediaSession & Lockscreen**: Android `MediaSessionCompat` foreground service with persistent notification tray controls, lockscreen artwork, and WearOS / Android Auto support.
- 🎧 **Smart Audio Focus & Bluetooth**: Auto-pause on headphone disconnect / incoming calls; auto-resume on Bluetooth reconnect (`ACTION_AUDIO_BECOMING_NOISY`).
- 🔄 **Smart Version-Preserving Deduplication**: Automatically collapses redundant compilation album entries while preserving legitimate alternate recordings (`Remix`, `Unplugged`, `Acoustic`, `Lofi`, `Tamil`, `Telugu`, `Hindi`, `Malayalam`, `Kannada`).
- 🎨 **Official 640x640 Spotify Artwork Engine**: Automatic high-resolution album cover fetching across search queries, discographies, and local music files.
- 📜 **Multi-Engine Timed Lyrics**: Syllable and line synchronized lyrics powered by LrcLib, KuGou, Musixmatch, and SimpMusic.
- 🔍 **ShazamKit Audio Recognition**: Acoustic fingerprint recognition to identify playing songs directly inside the app.
- 🎚️ **10-Band Graphic Equalizer**: 31Hz–16kHz frequency faders with live frequency curve and acoustic presets.
- 📥 **Offline Download & Local Caching**: Save streaming tracks locally for immediate offline playback with custom metadata and artwork indexing.
- 🔒 **100% Local Privacy**: Zero telemetry, zero analytics scripts. All library data and playlists remain sandboxed on your device inside an encrypted Room SQLite database.

---

## ⚡ APK Downloads Matrix (Build #27)

Compiled from commit **[`9f38a40`](https://github.com/xtros/Muziso-Android/commit/9f38a405f7e8e002a3653ef7c604f29e2e5fa870)** in [`xtros/Muziso-Android`](https://github.com/xtros/Muziso-Android):

| Variant | Target Architecture | Description | Download |
| :--- | :--- | :--- | :--- |
| **`Muziso-arm64.apk`** | ARM64-v8a | **Recommended for all modern phones** | [Download ARM64](https://github.com/xtros/Muziso-Android/releases/download/v1.0.1/Muziso-arm64.apk) |
| **`Muziso.apk`** | Universal FOSS | All devices, 100% open source dependencies | [Download Universal](https://github.com/xtros/Muziso-Android/releases/download/v1.0.1/Muziso.apk) |
| **`Muziso-with-Google-Cast.apk`** | Universal GMS | Universal build with Google Cast support | [Download Google Cast](https://github.com/xtros/Muziso-Android/releases/download/v1.0.1/Muziso-with-Google-Cast.apk) |
| **`Muziso-armeabi.apk`** | ARMv7 (32-bit) | Older 32-bit ARM Android devices | [Download ARMv7](https://github.com/xtros/Muziso-Android/releases/download/v1.0.1/Muziso-armeabi.apk) |
| **`Muziso-x86_64.apk`** | x86_64 | Android Studio Emulators, WSA, ChromeOS | [Download x86_64](https://github.com/xtros/Muziso-Android/releases/download/v1.0.1/Muziso-x86_64.apk) |
| **`Muziso-x86.apk`** | x86 (32-bit) | Legacy 32-bit x86 emulators | [Download x86](https://github.com/xtros/Muziso-Android/releases/download/v1.0.1/Muziso-x86.apk) |

---

## 🛠️ Developer Build Instructions

```bash
# 1. Clone the repository
git clone https://github.com/xtros/Muziso-Android.git
cd Muziso-Android

# 2. Compile ARM64 release APK
./gradlew :app:assembleStandaloneMobileArm64Release

# 3. Compile Universal FOSS release APK
./gradlew :app:assembleFossMobileUniversalRelease
```

---

## 📜 License & Legal

- **Software License**: Distributed under the MIT License. See [`LICENSE`](https://github.com/xtros/Muziso-Android/blob/main/LICENSE) for details.
- **Privacy Policy**: See **[Privacy Policy](docs/PRIVACY.md)** for data handling details.
- **Terms & Conditions**: See **[Terms & Conditions](docs/TERMS.md)** for user agreements and media disclaimers.
