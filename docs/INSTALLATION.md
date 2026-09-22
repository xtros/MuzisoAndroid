# ⚡ Muziso Android Installation & Build Guide

Official installation and developer build guide for **Muziso Android** (v0.1.8).

---

## 📥 End-User APK Installation

Visit the **[Muziso GitHub Releases](https://github.com/xtros/Muziso/releases)** page to download the latest Android APK (`v0.1.8`).

### 🤖 Android Mobile
- **Downloads**: [Download `Muziso_v0.1.8.apk`](https://github.com/xtros/Muziso/releases/latest/download/Muziso_v0.1.8.apk) (Direct Sideload) or [Google Play Store](https://github.com/xtros/Muziso/releases)
- **Target OS**: Android 8.0 (Oreo / API 26) and above.

### 📱 Sideloading Instructions:
1. Download `Muziso_v0.1.8.apk` on your Android phone or tablet.
2. Open the downloaded `.apk` file from your notification tray or Downloads folder.
3. If prompted with *"Install unknown apps"*, navigate to **Settings** &rarr; toggle on **"Allow from this source"**.
4. Tap **Install** and launch Muziso!

---

## 🛠️ Developer Build Instructions (Kotlin + Gradle)

### Prerequisites:
- **JDK**: Java Development Kit 17 or higher (`openjdk-17`)
- **Android SDK**: Platform SDK 34 (Android 14) or 35 (Android 15)
- **Gradle**: Included Gradle wrapper (`./gradlew`)

### Build Commands:
```bash
# 1. Clone the repository
git clone https://github.com/xtros/MuzisoAndroid.git
cd MuzisoAndroid

# 2. Build Debug APK
./gradlew assembleDebug

# Output APK path:
# app/build/outputs/apk/debug/app-debug.apk

# 3. Build Production Signed Release APK
./gradlew assembleRelease

# Output APK path:
# app/build/outputs/apk/release/app-release.apk
```
