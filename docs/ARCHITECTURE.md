# 🏗️ Muziso Android Architecture Documentation

**Current Version:** v1.0.1 (CI Build #20, Commit [`4126588`](https://github.com/xtros/Muziso-Android/commit/4126588c43d27bc1a1865584b934931a0ef53190))  
**Repository:** [`xtros/Muziso-Android`](https://github.com/xtros/Muziso-Android)  
**Target Platform:** Android 8.0 (API 26) to Android 15 (API 35)  
**Primary Language:** Kotlin (Coroutines, StateFlow, Jetpack Media3, Room SQLite)

---

## 🌟 Architecture Overview

Muziso Android is engineered as a pure native Android application prioritizing low-latency 320 kbps audio streaming, background lifecycle resilience, hardware audio offload, synchronized multi-source lyrics, and battery conservation.

---

## 🏛️ High-Level System Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                     Native Kotlin UI Layer                      │
│        (Jetpack Compose / ViewBinding, MVI Architecture)        │
└────────────────────────────────┬────────────────────────────────┘
                                 │  ViewModel & Kotlin StateFlow
┌────────────────────────────────▼────────────────────────────────┐
│                   Foreground Audio Service                      │
│            (MediaSessionCompat, Audio Focus Manager)            │
├─────────────────────┬──────────────────┬────────────────────────┤
│ Playback Engine     │ Persistence      │ Network & Stream Hub   │
│ - Jetpack Media3    │ - Room Database  │ - JioSaavn 320kbps CDN │
│ - ExoPlayer 320kbps │ - Encrypted DAO  │ - Innertube / YouTube  │
│ - Hardware Offload  │ - Offline Cache  │ - KuGou / LrcLib Lyric │
│ - 10-Band EQ DSP    │ - DataStore Pref │ - Spotify 640x640 Art  │
└─────────────────────┴──────────────────┴────────────────────────┘
```

---

## 🎧 Audio Engine & Multi-Source Stream Resolvers

Muziso implements a robust, modular audio resolution pipeline:

1. **JioSaavn 320 kbps Direct CDN Resolver (`JioSaavnPlaybackResolver`)**:
   - Audio URLs are resolved in **<30ms** via direct API lookup.
   - Bitstreams are fetched directly from high-speed 320 kbps CDN endpoints without transcoding delay.

2. **Innertube & YouTube Streaming Engine with PO Token**:
   - Resilient stream resolution utilizing guest clients (`IPADOS`, `ANDROID_NO_SDK`, `ANDROID_VR_NO_AUTH`).
   - Integrated Proof-of-Origin (PO) token support for reliable bitstream retrieval.

3. **Jetpack Media3 & ExoPlayer Pipeline**:
   - Leverages hardware audio offloading and gapless buffer preloading.
   - Coordinates with `MediaSessionCompat` to keep background music active when screen is locked or other apps are open.

4. **Audio Focus & Noisy Audio Intent**:
   - Listens for `ACTION_AUDIO_BECOMING_NOISY` to automatically pause when wired headphones or Bluetooth devices disconnect.
   - Automatically handles incoming phone calls and transient audio focus shifts.

---

## 📜 Lyrics & Metadata Recognition Engines

- **LrcLib & KuGou**: Synchronized line-by-line and syllable-by-syllable timed lyrics parser (`TTMLParser`).
- **Musixmatch & SimpMusic**: Extended crowdsourced lyrics fallback.
- **ShazamKit**: In-app acoustic fingerprinting and audio song recognition.
- **LastFM**: Real-time scrobbling and playback statistics sync.
- **Spotify Cover Enrichment**: Resolves verified **640x640 album artwork** automatically.

---

## 💾 Local Storage & Database Schema (Room SQLite)

All user data is stored strictly on the local device:
- **Database**: Room SQLite database with typed DAOs and Kotlin Flow observers.

### Key Entities:
- **Tracks**: Title, artist, album, duration, file path / stream URL, bitrate, cover art blob reference, and local checksum.
- **Playlists**: Custom user-ordered playlists and tags.
- **Play History**: Local play counts and playback timestamps for smart autoplay recommendations.
- **Offline Cache**: Registry of downloaded audio files stored in sandboxed local application directories.
