# ⚡ Muziso Android Installation & Build Guide

Official installation and developer build guide for **Muziso Android** (v1.0.1, CI Build #20).

Source & Release repository: **[`xtros/Muziso-Android`](https://github.com/xtros/Muziso-Android)**  
Build #20 Commit Reference: **[`4126588`](https://github.com/xtros/Muziso-Android/commit/4126588c43d27bc1a1865584b934931a0ef53190)**

---

## 📥 End-User APK Installation Matrix (Build #20)

| Package Name | Architecture / Flavor | Recommended For | Download Link |
| :--- | :--- | :--- | :--- |
| **`Muziso-arm64.apk`** | ARM64-v8a (Standalone) | **All modern Android devices** (Pixel, Galaxy, OnePlus, Xiaomi) | [Download ARM64](https://github.com/xtros/Muziso-Android/releases/download/v1.0.1/Muziso-arm64.apk) |
| **`Muziso.apk`** | Universal FOSS | All devices, 100% Free & Open Source build | [Download Universal FOSS](https://github.com/xtros/Muziso-Android/releases/download/v1.0.1/Muziso.apk) |
| **`Muziso-with-Google-Cast.apk`** | Universal GMS + Google Cast | Devices with Google Cast / Chromecast audio | [Download Google Cast APK](https://github.com/xtros/Muziso-Android/releases/download/v1.0.1/Muziso-with-Google-Cast.apk) |
| **`Muziso-armeabi.apk`** | ARMv7 (32-bit Standalone) | Legacy 32-bit Android phones | [Download ARMv7](https://github.com/xtros/Muziso-Android/releases/download/v1.0.1/Muziso-armeabi.apk) |
| **`Muziso-x86_64.apk`** | x86_64 Standalone | Android Studio Emulator, WSA, ChromeOS | [Download x86_64](https://github.com/xtros/Muziso-Android/releases/download/v1.0.1/Muziso-x86_64.apk) |
| **`Muziso-x86.apk`** | x86 (32-bit Standalone) | Legacy 32-bit x86 emulators | [Download x86](https://github.com/xtros/Muziso-Android/releases/download/v1.0.1/Muziso-x86.apk) |

---

### 📱 Sideloading Instructions:
1. Download **`Muziso-arm64.apk`** (or your target architecture) on your Android phone or tablet.
2. Open the downloaded `.apk` file from your notification tray or Downloads folder.
3. If prompted with *"Install unknown apps"*, navigate to **Settings** &rarr; toggle on **"Allow from this source"**.
4. Tap **Install** and launch Muziso!

---

## 🛠️ Developer Build Instructions (Kotlin + Gradle)

### Prerequisites:
- **JDK**: Java Development Kit 21 (`openjdk-21`)
- **Android SDK**: Platform SDK 34 / 35
- **Gradle**: Included Gradle wrapper (`./gradlew`)

### Build Commands:
```bash
# 1. Clone the repository
git clone https://github.com/xtros/Muziso-Android.git
cd Muziso-Android

# 2. Build FOSS Universal Release APK
./gradlew :app:assembleFossMobileUniversalRelease

# 3. Build Standalone ARM64 Release APK
./gradlew :app:assembleStandaloneMobileArm64Release

# 4. Build GMS Google Cast Universal Release APK
./gradlew :app:assembleGmsMobileUniversalRelease
```
