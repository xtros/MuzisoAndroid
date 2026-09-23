# 🤖 Muziso Android

<p align="center">
  <img src="assets/logo.png" alt="Muziso Official Logo" width="160" />
</p>

<p align="center">
  <img src="assets/dashboard.png" alt="Muziso Android Dashboard" width="70%" />
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Android%206.0+-3DDC84?style=for-the-badge&logo=android&logoColor=white" alt="Android 6.0+" />
  <img src="https://img.shields.io/badge/Kotlin-2.1-7F52FF?style=for-the-badge&logo=kotlin&logoColor=white" alt="Kotlin 2.1" />
  <img src="https://img.shields.io/badge/UI-Jetpack%20Compose%20%7C%20Material%203-4285F4?style=for-the-badge&logo=jetpackcompose&logoColor=white" alt="Jetpack Compose" />
  <a href="https://github.com/xtros/Muziso-Android/releases"><img src="https://img.shields.io/badge/Release-v1.0.0-ffffff?style=for-the-badge&logo=github&logoColor=black" alt="Release v1.0.0" /></a>
  <a href="https://github.com/xtros/Muziso-Android/commit/9f38a405f7e8e002a3653ef7c604f29e2e5fa870"><img src="https://img.shields.io/badge/Build%20%2327-9f38a40-ffffff?style=for-the-badge&logo=githubactions&logoColor=black" alt="Build 27" /></a>
  <a href="https://github.com/xtros/Muziso-Android/blob/main/LICENSE"><img src="https://img.shields.io/badge/License-GPL--3.0-059669?style=for-the-badge" alt="GPL-3.0 License" /></a>
</p>

<p align="center">
  <b>Muziso Android</b> is a modern, powerful, and privacy-friendly Android music player engineered for <b>Android 6.0 to Android 15</b>. Built with <b>Native Kotlin 2.1</b>, <b>Jetpack Compose Material 3</b>, <b>Jetpack Media3 ExoPlayer</b>, and a dual streaming engine (YouTube Music &amp; JioSaavn 320 kbps), Muziso delivers synchronized word-by-word lyrics, offline "Hey Aura" voice control, real-time Listen Together rooms, Google Cast, SponsorBlock, 10-band hardware DSP Equalizer, and 100% offline encrypted privacy.
</p>

---

## 📚 Documentation & Guides

- 🏗️ **[Architecture Guide](docs/ARCHITECTURE.md)**: Deep dive into Android Audio Service, ExoPlayer Media3, VOSK Voice AI, and Room SQLite database.
- ⚡ **[Installation & Sideload Guide](docs/INSTALLATION.md)**: Step-by-step APK sideloading instructions and Gradle compilation.
- 🤝 **[Contributing & Bug Hunter Program](docs/CONTRIBUTING.md)**: Android contribution standards and issue templates.
- 🔒 **[Privacy Policy](docs/PRIVACY.md)**: 100% offline-first privacy architecture, zero telemetry.
- ⚖️ **[Terms & Conditions](docs/TERMS.md)**: Open-source licensing terms and third-party media disclaimers.

---

## 🌟 Comprehensive Native App Features (v1.0.0)

### 🎵 Playback & Dual Streaming
- **YouTube Music & JioSaavn Dual Engine**: Stream any track, album, artist, or playlist with direct 320 kbps bitstream resolution.
- **YouTube Music Account Sync**: Log in with your YouTube Music account to sync your personal library, liked songs, albums, and custom playlists.
- **Innertube PO Token Engine**: Automatic PO Token generation and iOS/Android fallback client profiles (`IPADOS`, `ANDROID_NO_SDK`) to bypass throttling.
- **SponsorBlock Integration**: Crowdsourced segment skipping to automatically bypass non-music intros, dialogue interludes, and sponsor segments.
- **Smart Deduplication**: Collapses duplicate compilation albums while strictly preserving legitimate alternate studio recordings (Acoustic, Lofi, Tamil, Telugu, Hindi, etc.).

### 📜 Synchronized Word-by-Word Lyrics
- **Word & Syllable Highlighting**: Real-time karaoke-style syllable highlighting accurate to the millisecond.
- **6-Provider Aggregation Network**: Aggregates lyrics from **BetterLyrics**, **Musixmatch**, **LRCLib**, **KuGou**, **RushLyrics**, and **SimpMusic**.
- **Romanization & Live Translations**: Phonetic romanization for non-Latin scripts (Japanese, Korean, Chinese, Hindi) and real-time multi-language translation.

### 🎙️ Offline Voice Control AI ("Hey Aura")
- **VOSK On-Device Speech Engine**: 100% private, on-device wake-word detection (*"Hey Aura"*) and natural voice command parser.
- **Acoustic Echo Cancellation (AEC)**: Hardware noise suppression and echo cancellation for reliable voice detection even while loud music is playing.
- **Text-to-Speech (TTS) Voice Feedback**: Spoken feedback confirmations for track selection, queue management, and volume changes.

### 🎛️ Audio Engine & Hardware DSP
- **10-Band Graphic Equalizer**: 31Hz–16kHz frequency faders with live visual EQ curve, bass boost, and acoustic presets.
- **ReplayGain & Volume Normalization**: Consistent LUFS loudness normalization across diverse audio sources.
- **Silence Skipping**: Seamless gapless transitions by trimming silent intros and outros.
- **Real-Time Pitch & Tempo Shifter**: Adjust playback speed (0.5x to 2.0x) and pitch on the fly without distortion.
- **Sleep Timer with Fadeout**: Schedule playback shutdown with smooth audio fadeout.

### 📡 Casting, Social & Tools
- **Real-Time "Listen Together"**: Synchronized group listening rooms with friends over WebSocket powered by **MuzisoServer**.
- **Discord Rich Presence**: Live playback status, album art, and progress bar broadcasted directly to your Discord profile.
- **Last.fm Scrobbling**: Automatic scrobbler integration for listening history and scrobble tracking.
- **Google Cast & Android Auto**: Chromecast / Nest Audio streaming, Android Auto in-car dashboard controls, and WearOS smartwatch controls.
- **ShazamKit / ACRCloud Song Identifier**: Acoustic fingerprint recognition to identify songs playing nearby in the room.
- **Muziso Wrapped**: Interactive monthly and annual listening statistics recap.

### 🎨 Material 3 UI & Privacy
- **Dynamic Material You**: Wallpaper-driven dynamic color adaptation, Pure Black AMOLED mode, and customizable player canvases.
- **100% Local Privacy**: Encrypted local Room SQLite database with zero telemetry, zero analytics scripts, and sandboxed offline caching.

---

## ⚡ APK Downloads Matrix (Build #27)

Compiled from commit **[`9f38a40`](https://github.com/xtros/Muziso-Android/commit/9f38a405f7e8e002a3653ef7c604f29e2e5fa870)** in [`xtros/Muziso-Android`](https://github.com/xtros/Muziso-Android):

| Variant | Target Architecture | Description | Download Link |
| :--- | :--- | :--- | :--- |
| **`Muziso-arm64.apk`** | ARM64-v8a | **Recommended for all modern phones** (Pixel, Galaxy, OnePlus, Xiaomi) | [Download ARM64](downloads/Muziso-arm64.apk) |
| **`Muziso.apk`** | Universal FOSS | All devices, 100% open-source dependencies | [Download Universal](downloads/Muziso.apk) |
| **`Muziso-with-Google-Cast.apk`** | Universal GMS | Universal build with Google Play Services and Google Cast support | [Download Google Cast](downloads/Muziso-with-Google-Cast.apk) |
| **`Muziso-armeabi.apk`** | ARMv7 (32-bit) | Older 32-bit ARM Android devices and budget hardware | [Download ARMv7](downloads/Muziso-armeabi.apk) |
| **`Muziso-x86_64.apk`** | x86_64 | Android Studio Emulators, WSA, ChromeOS | [Download x86_64](downloads/Muziso-x86_64.apk) |
| **`Muziso-x86.apk`** | x86 (32-bit) | Legacy 32-bit x86 emulators and virtual machines | [Download x86](downloads/Muziso-x86.apk) |

---

## 🛠️ Developer Build Instructions

```bash
# 1. Clone the repository
git clone https://github.com/xtros/Muziso-Android.git
cd Muziso-Android

# 2. Compile ARM64 release APK
./gradlew :app:assembleStandaloneMobileArm64Release

# 3. Compile Universal FOSS release APK
./gradlew assembleFossMobileUniversalRelease

# 4. Compile Google Cast GMS release APK
./gradlew assembleGmsMobileUniversalRelease
```

---

## 📜 License & Legal

- **Software License**: Distributed under the **GNU General Public License v3.0 (GPL-3.0)**. See [`LICENSE`](https://github.com/xtros/Muziso-Android/blob/main/LICENSE) for details.
- **Privacy Policy**: See **[Privacy Policy](docs/PRIVACY.md)** for data handling details.
- **Terms & Conditions**: See **[Terms & Conditions](docs/TERMS.md)** for user agreements and media disclaimers.
