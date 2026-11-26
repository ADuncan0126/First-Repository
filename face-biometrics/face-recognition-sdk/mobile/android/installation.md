---
icon: box
---

# Installation

## Requirements

- Android Studio with JDK 17 selected as the Gradle JVM.
- Android SDK Platform 33. The sample compiles and targets API 33, with minimum API 24 (Android 7.0).
- A physical ARM Android phone (`arm64-v8a` or `armeabi-v7a`) for camera testing. Enable USB debugging for deployment from Android Studio.
- Network access on first sync for Gradle and dependencies. The project pins Gradle 7.5, Android Gradle Plugin 7.4.1, and Kotlin 1.8.0.

## Build the sample

1. Extract the project ZIP and open the directory containing `settings.gradle` in Android Studio.
2. Keep the edition’s bundled `libfacesdk/facesdk.aar` in place. The Core and Pro libraries should stay with their respective projects. The camera module uses the bundled `libfotoapparat/fotoapparat-2.7.0.aar`.
3. Add your [license asset](licensing-and-activation.md) and sync Gradle.
4. Select the `app` run configuration and deploy to the connected phone. For a command-line debug build from the project root, run `./gradlew :app:assembleDebug` on macOS or Linux, or `gradlew.bat :app:assembleDebug` on Windows. The APK is under `app/build/outputs/apk/debug/`.

If Gradle 7.5 times out on first sync, check access to the Gradle distribution URL and its redirects, Google Maven, and Maven Central, then retry. Keep the HTTPS wrapper URL so the project works on other machines.

## Integrate the SDK into another project

Add the matching local `libfacesdk` module and declare it in your app dependencies as `implementation project(':libfacesdk')`. Mirror the demo’s camera permission and runtime permission handling if you use live capture, and [activate the SDK](licensing-and-activation.md) before processing inputs.

## <i class="fa-arrow-right">:arrow-right:</i> Verify your build

Launch the app on the phone and check SDK status. Once it is ready, run the sample workflow. [Sample Application](sample-application.md).
