# HO Browser — Android starter

A native Android browser starter branded as **HO Browser**, using Mozilla GeckoView as its browser engine. It is designed to be built from an Android phone using GitHub Actions; Android Studio and a local computer are not required.

## Latest source fix
- Fixed the GeckoView session type mismatch by explicitly referencing `MainActivity.session` inside the `GeckoView.apply` block. The unqualified `session` name could resolve to GeckoView's nullable session property instead of the Activity's non-null session.

## Included in this build
- GeckoView-powered web browsing, address/search field, back, forward and reload.
- HO Browser home screen with Google, YouTube, Facebook, Instagram, X, Wikipedia and Amazon shortcuts.
- Glass-inspired panels, blue/purple/orange dark gradient, rounded controls and spring-like button feedback.
- Settings and a working local customization screen for glass opacity and accent selection.
- Preferred 60/90/120 Hz display refresh-rate request (Android/device policy may ignore or clamp it).
- Fullscreen callback for compatible website video players.
- GitHub Actions workflow that builds a debug APK and uploads it as an artifact.

## Not implemented yet
This is a first functional foundation, not a finished commercial browser. Multi-tab session management, persistent bookmarks/history, download interception/manager, ad/content blocking, private browsing isolation, extensions, sync, account services, AI features, microphone voice search and QR scanning are not implemented. The corresponding settings are informational placeholders where indicated. The accent selection currently stores the chosen color for the current activity session; broader recoloring will be expanded in a later phase.

YouTube is loaded as a website in GeckoView. Playback, DRM, autoplay, quality and fullscreen behavior depend on YouTube, Android and device support. This app does not promise background playback.

## Build on an Android phone
1. Create a new GitHub repository named `HO-Browser`.
2. Extract this ZIP on your phone.
3. Upload the **contents** of the `ho-browser` folder to the repository root. Do not upload the ZIP itself or create an extra nested project folder.
4. Open the repository's **Actions** tab and enable Actions if prompted.
5. Open **Build HO Browser APK**, choose **Run workflow**, and start it. A push to `main` also triggers a build.
6. When the workflow finishes successfully, open its run, scroll to **Artifacts**, and download `HO-Browser-debug`.
7. Extract the artifact ZIP and install `app-debug.apk`. Android may ask you to allow installation from your browser or file manager.

## Technical details
- Kotlin / Android Views
- Mozilla GeckoView dependency pinned in `app/build.gradle.kts`
- Min SDK 26 (Android 8.0)
- Compile/target SDK 35
- JDK 17 and Gradle 8.9 in GitHub Actions

Keep GeckoView updated to a current supported security release before public distribution. Debug APKs are for testing, not Play Store release signing.
