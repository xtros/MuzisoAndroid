# 🏗️ Muziso Android Architecture Documentation

**Current Version:** v0.1.8  
**Target Platform:** Android 8.0 (API 26) to Android 15 (API 35)  
**Primary Language:** Kotlin  

---

## 🌟 Architecture Overview

Muziso Android is engineered as a pure native Android application prioritizing low-latency 320 kbps audio streaming, background lifecycle resilience, hardware audio offload, and battery conservation.

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
│ Playback Engine     │ Persistence      │ Network & CDN          │
│ - Jetpack Media3    │ - Room Database  │ - OkHttp Client        │
│ - ExoPlayer 320kbps │ - Encrypted DAO  │ - JioSaavn API Engine  │
│ - Hardware Offload  │ - Offline Cache  │ - Spotify Art Resolver │
└─────────────────────┴──────────────────┴────────────────────────┘
```

---

## 🎧 Audio Engine & Stream Resolvers

Muziso implements a dedicated Android audio resolution pipeline:

1. **JioSaavn 320 kbps Direct CDN Resolver**:
   - Audio URLs are resolved in **<30ms** via Strategy 0 direct API lookup (`song.getDetails&pids={id}`).
   - Bitstreams are fetched directly from high-speed 320 kbps CDN endpoints without transcoding delay.

2. **Jetpack Media3 & ExoPlayer Pipeline**:
   - Leverages hardware audio offloading and gapless buffer preloading.
   - Coordinates with `MediaSessionCompat` to keep background music active when screen is locked or other apps are open.

3. **Audio Focus & Noisy Audio Intent**:
   - Listens for `ACTION_AUDIO_BECOMING_NOISY` to automatically pause when wired headphones or Bluetooth devices disconnect.
   - Automatically handles incoming phone calls and transient audio focus shifts.

---

## 🎨 Guaranteed Official Cover Image Engine

1. **Deep Metadata Extraction**:
   - Parses `item["image"]`, `item["more_info"]["image"]`, and `item["album_image"]`, scaling thumbnails up to **500x500 official high-res album covers**.

2. **Spotify Cover Enrichment Resolver**:
   - Any track lacking a verified cover image is enriched asynchronously via Spotify's official Web API, returning verified **640x640 album artwork**.

---

## 🔄 Smart Version-Preserving Deduplication Engine

- **Compilation Collapse**: Strips redundant album compilation prefixes to collapse duplicate entries of the same song across compilation albums into 1 clean listing.
- **Version Protection**: Preserves version descriptor keywords (`Remix`, `Reprise`, `Unplugged`, `Acoustic`, `Lofi`, `Extended`, `Instrumental`, `Tamil`, `Telugu`, `Hindi`, `Malayalam`, `Kannada`) so alternate studio recordings remain distinct.

---

## 💾 Local Storage & Database Schema (Room SQLite)

All user data is stored strictly on the local device:
- **Database**: Room SQLite database with typed DAOs and Kotlin Flow observers.

### Key Entities:
- **Tracks**: Title, artist, album, duration, file path / stream URL, bitrate, cover art blob reference, and local checksum.
- **Playlists**: Custom user-ordered playlists and tags.
- **Play History**: Local play counts and playback timestamps for smart autoplay recommendations.
- **Offline Cache**: Registry of downloaded audio files stored in sandboxed local application directories.
