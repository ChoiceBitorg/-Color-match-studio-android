# Color Match Studio – offline Android project

Everything the page needs is inside `www/` (page, three.js r128, Bricolage Grotesque fonts). No internet is required.

## Build the APK (Capacitor)
Requirements: Node.js 18+, Android Studio (with an SDK), JDK 17.

    npm install
    npx cap add android
    npx cap sync android
    npx cap open android

In Android Studio: Build > Build Bundle(s) / APK(s) > Build APK(s).
The debug APK appears in android/app/build/outputs/apk/debug/. Copy it to your phone and install it.

## Change the app id, name or icon
- Edit `appId` and `appName` in capacitor.config.json before running `npx cap add android`.
- Replace the launcher icons in android/app/src/main/res/mipmap-* (Android Studio: right-click res > New > Image Asset).

## Publish to Google Play
Create a signed release build (Build > Generate Signed Bundle / APK > Android App Bundle) and upload the .aab file.

## Quick test without building
Open www/index.html in a browser. After editing it, run `npx cap sync android` and rebuild.

## No-install alternative (Android Studio only)
New Project > Empty Views Activity. Copy the contents of www/ into app/src/main/assets/ and load it in a WebView:
    webView.settings.javaScriptEnabled = true
    webView.loadUrl("file:///android_asset/index.html")
