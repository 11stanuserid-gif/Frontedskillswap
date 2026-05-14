# SwapSkill Frontend v2 — Upgrade Instructions

## ✅ Backend Live
- **URL**: https://skillbg-3.onrender.com
- **Health**: https://skillbg-3.onrender.com/health
- **API Base**: https://skillbg-3.onrender.com/api/v1

## 🔧 What Was Fixed
1. `pubspec.yaml` — All package versions made Codemagic-compatible (no conflicts)
2. `lib/config/app_config.dart` — Backend URL set to Render production
3. `lib/services/api_service.dart` — Connected to live backend
4. `codemagic.yaml` — Flutter 3.24.0 pinned, no-tree-shake-icons fix
5. `android/app/build.gradle` — namespace = com.swapskil, multidex enabled
6. `android/build.gradle` — Gradle 7.4.2, Kotlin 1.9.10, Google Services 4.4.0
7. `android/gradle.properties` — 4GB heap (no OOM during build)
8. `gradle-wrapper.properties` — Gradle 7.6.3 (stable with AGP 7.4)
9. `AndroidManifest.xml` — Package = com.swapskil (matches Firebase)
10. `MainActivity.kt` — Correct package path
11. `google-services.json` — Firebase config (your actual keys)

## 📂 Files to Replace in Your Repo
```
pubspec.yaml
lib/config/app_config.dart
lib/services/api_service.dart
codemagic.yaml
android/build.gradle
android/settings.gradle
android/gradle.properties
android/gradle/wrapper/gradle-wrapper.properties
android/app/build.gradle
android/app/google-services.json
android/app/src/main/AndroidManifest.xml
android/app/src/main/kotlin/com/swapskil/MainActivity.kt
android/app/src/main/res/values/styles.xml
android/app/src/main/res/drawable/launch_background.xml
```

## ⚠️ IMPORTANT — Old MainActivity.kt को DELETE करो
पुराने path `android/app/src/main/kotlin/com/swapskill/app/MainActivity.kt` को **delete** करो
नया path: `android/app/src/main/kotlin/com/swapskil/MainActivity.kt`

(पुराने में `swapskill/app` था, नए में `swapskil` है — Firebase से match)

## 🚀 Codemagic पर Build करने के Steps
1. Push सारी files GitHub repo में
2. Codemagic dashboard → app → "Start new build"
3. Workflow: `SwapSkill Android Build`
4. Build ~15-20 min लेगा, APK + AAB मिलेगा

## 🔑 Bad में करना (Optional)
- Agora App ID: `lib/config/app_config.dart` में `agoraAppId` update करो
- iOS के लिए: `ios/Runner/GoogleService-Info.plist` add करो
