# Nova Home Launcher v2.0 — One UI 8.5 inspired

## Features in this version
- **Live clock + date** header (large, One UI style)
- **Swipeable home pages** with page-dot indicator
- **Swipe up anywhere** OR tap "Apps" button → opens App Drawer
- **App Drawer** with live search + "All / Games" tabs
- **Gaming Hub** — auto-detects installed games, RAM stats, Game Mode toggle
- **Long-press home wallpaper** → Edit Home Sheet:
  - Wallpaper picker
  - Widget picker
  - Themes (Samsung Theme Store if installed, else Play Store)
  - Home Settings (grid columns, dock size, hide apps)
- **Hide Apps** — select apps to hide from home + drawer
- **Dock size** — 3 or 4 icons configurable in Settings
- **Grid columns** — 3 / 4 / 5 configurable in Settings
- **Long-press any icon** → App info / Uninstall
- **Back button** closes drawer/sheet only — won't exit launcher
- **Performance**: all app loading on background thread (coroutines), DiffUtil in all RecyclerViews, itemAnimator disabled for silky scrolling even on laggy devices

## Why you can't directly convert the ZIP to APK
A ZIP of Kotlin/Java source code is NOT an APK. An APK needs to be **compiled** first. Online "zip to apk" tools don't work for source code — they only handle already-compiled bytecode JARs. You must use Android Studio (free):

## How to build the APK
1. Download & install **Android Studio** (free): https://developer.android.com/studio
2. Unzip `NovaHomeLauncher.zip`
3. Android Studio → **File → Open** → select the `NovaHomeLauncher` folder
4. Wait for Gradle sync (needs internet, ~2–5 min first time)
5. **Build → Build Bundle(s) / APK(s) → Build APK(s)**
6. Find the APK at: `app/build/outputs/apk/debug/app-debug.apk`
7. Transfer to phone → install → **Settings → Apps → Default apps → Home app → Nova Home**

## "Never uninstall" — honest answer
Making an app truly uninstallable requires it to be a **system app** (baked into the phone's ROM). That requires rooting the device or building a custom ROM — not possible from a normal APK. What you CAN do: in Android settings, set it as default home → it becomes very hard to accidentally remove.

## Customise
- **Dock apps**: `MainActivity.kt` → `setupHotseatIcons()` — add `if (app.packageName == "com.whatsapp")` logic to pin specific apps
- **Game detection**: `AppRepository.kt` → `GAME_KEYWORDS` list — add more keywords
- **Colors**: `res/values/colors.xml`
