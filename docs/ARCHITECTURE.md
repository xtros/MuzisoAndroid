# 🏗️ Muziso Android Architecture Documentation

**Current Version:** v1.0.0 (CI Build #27, Commit [`9f38a40`](https://github.com/xtros/Muziso-Android/commit/9f38a405f7e8e002a3653ef7c604f29e2e5fa870))  
**Repository:** [`xtros/Muziso-Android`](https://github.com/xtros/Muziso-Android)  
**Target Platform:** Android 6.0 (API 23) to Android 15 (API 35)  
**Primary Language:** Kotlin 2.1 (Coroutines, StateFlow, Jetpack Compose, Jetpack Media3, Dagger Hilt, Room SQLite)

---

## 🌟 Architecture Overview

Muziso Android is engineered as a pure native Android application prioritizing low-latency 320 kbps audio streaming, background lifecycle resilience, hardware audio offload, synchronized multi-source lyrics, on-device AI voice control, real-time social listening, and battery conservation.

---

## 🏛️ High-Level System Architecture

```
┌────────────────────────────────────────────────────────────────────────┐
│                        Jetpack Compose UI Layer                        │
│             (Material 3 / Material You / AMOLED Dark Mode)             │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │  ViewModels (Dagger Hilt & Flow)
┌───────────────────────────────────▼────────────────────────────────────┐
│                    Foreground Audio MediaSession                       │
│              (MediaSessionCompat, Audio Focus Manager)                 │
├─────────────────────┬──────────────────┬───────────────────────────────┤
│ Audio Engine & DSP  │ Persistence      │ Streaming & Lyrics Resolvers  │
│ - Jetpack Media3    │ - Room SQLite DB │ - YouTube Music (Innertube)   │
│ - ExoPlayer 320kbps │ - Encrypted DAOs │ - JioSaavn 320kbps Bitstream  │
│ - 10-Band Graphic EQ│ - Offline Cache  │ - 6 Lyrics Providers (Sync)   │
│ - ReplayGain / LUFS │ - DataStore Pref │ - SponsorBlock & ShazamKit    │
│ - VOSK Voice AI     │ - Sandboxed Storage│ - MuzisoServer (WebSocket) │
└─────────────────────┴──────────────────┴───────────────────────────────┘
```

---

## 📦 Submodules & Multi-Project Structure

| Submodule / Directory | Layer | Purpose & Responsibilities |
| :--- | :--- | :--- |
| **`:app`** | Core Android | Jetpack Compose UI, MediaSessionService, Navigation, Equalizer DSP, and VOSK Voice AI integration. |
| **`:innertube`** | Streaming Engine | YouTube Music API client with PO Token generation, account login sync, and client profile fallback (`IPADOS`, `ANDROID_NO_SDK`). |
| **`:flow`** | Stream Extractor | High-speed YouTube audio stream URL and format extraction. |
| **`:betterlyrics`** | Synced Lyrics | Syllable-by-syllable and word-level synchronized karaoke lyrics parser. |
| **`:musixmatch`** | Lyrics Provider | Rich synchronized lyrics and translations fallback. |
| **`:lrclib`** | Lyrics Provider | Open-source synchronized LRC lyrics client. |
| **`:kugou`** | Lyrics & Catalog | Asian and translated lyrics provider. |
| **`:rush`** | Lyrics Provider | RushLyrics engine for extended coverage. |
| **`:simpmusic`** | Lyrics & Media | Additional lyrics and metadata source. |
| **`:paxsenix`** | Stream Proxy | Stream resolver fallback adapter. |
| **`:shazamkit`** | Audio Recognition| Acoustic audio fingerprinting to identify songs playing nearby. |

---

## 🎧 Dual-Engine Streaming Pipeline

Muziso implements a dual-engine audio pipeline:

1. **YouTube Music & Innertube (`:innertube`, `:flow`)**:
   - Stream any track, album, artist, mood, or community playlist.
   - Proof-of-Origin (PO) token generation and client profile fallback to ensure uninterrupted playback.
   - Account login support to sync personal libraries, liked tracks, and playlists.

2. **JioSaavn 320 kbps Direct CDN Resolver**:
   - Audio URLs are resolved in **<30ms** via direct API lookup.
   - Fetches pure 320 kbps bitstreams directly from CDN endpoints without transcoding.

3. **Jetpack Media3 ExoPlayer Engine**:
   - Hardware audio offloading and gapless buffer preloading.
   - Background playback managed via `MediaSessionCompat` foreground service.
   - Audio focus handling (`ACTION_AUDIO_BECOMING_NOISY` auto-pause on headphone disconnect).

---

## 🎙️ Offline Voice Control AI ("Hey Aura")

- **VOSK On-Device Speech Recognizer**: Runs completely offline with no network dependencies.
- **Acoustic Echo Cancellation (AEC)**: Hardware noise suppression enables hands-free wake word recognition even while music is blasting.
- **Spoken TTS Feedback**: Native Text-to-Speech confirmations for track changes, queue updates, and volume controls.

---

## 🎛️ Audio DSP Engine

- **10-Band Graphic Equalizer**: Custom frequency faders from 31Hz to 16kHz with live visual curve.
- **Loudness Normalization**: ReplayGain & LUFS standard normalization.
- **Silence Skipping**: Seamless gapless playback transitions.
- **Pitch & Speed Shifter**: Real-time tempo (0.5x to 2.0x) and pitch adjustment.

---

## 👥 Real-Time "Listen Together" & Social

- **MuzisoServer WebSocket Client**: Sub-second synchronized group listening rooms with shared queue management.
- **Discord Rich Presence**: Live playback status, album art, and progress bar broadcasted to Discord.
- **Last.fm Scrobbling**: Automatic scrobbler integration for listening history tracking.

---

## 💾 Local Persistence & Database Schema (Room SQLite)

All user data is stored strictly on the local device:
- **Database**: Room SQLite database with typed DAOs and Kotlin Flow observers.
- **Zero Telemetry**: No third-party tracking, analytics, or remote telemetry scripts.
- **Sandboxed Storage**: Offline cached songs and official 640x640 album artwork stored securely in app-private directories.
