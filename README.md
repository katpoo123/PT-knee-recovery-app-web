# JointOps

Expo / React Native app for your post-meniscectomy rehab protocol. Check off exercises per session; progress is saved on device.

## Requirements

- **Node.js** 18+ ([nodejs.org](https://nodejs.org) or `brew install node`)
- **iOS (physical device):** Mac, [Xcode](https://developer.apple.com/xcode/), iPhone on iOS 16+ with **Developer Mode** on, free **Apple ID** for signing (or paid Apple Developer account)
- **Android (physical device):** [Android Studio](https://developer.android.com/studio) (SDK + platform tools), USB debugging enabled on the phone

Full environment setup (simulators, SDKs, troubleshooting): [Expo — Set up your environment](https://docs.expo.dev/get-started/set-up-your-environment/).

## Quick start (both platforms)

```bash
cd PT-knee-recovery-app   # or your clone path
npm install
npm start
```

Scan the QR code with **Expo Go** ([iOS](https://apps.apple.com/app/expo-go/id982107779) / [Android](https://play.google.com/store/apps/details?id=host.exp.exponent)) to preview the UI. Expo Go does **not** install **JointOps** on your home screen with your custom icon — use a dev build below for that.

## Install on your phone (dev build)

Generate native projects once (or after changing `app.json` identifiers or icons):

```bash
npx expo prebuild
```

Then build and run on a connected device:

| Platform | Command | Official guide |
|----------|---------|----------------|
| **iOS** | `npx expo run:ios --device` | [Run on iOS device](https://docs.expo.dev/workflow/ios/#running-on-a-physical-device) |
| **Android** | `npx expo run:android --device` | [Run on Android device](https://docs.expo.dev/workflow/android/#running-on-a-physical-device) |

**iOS notes (brief):**

1. **Settings → Privacy & Security → Developer Mode** → On (restart if prompted).
2. In Xcode (`open ios/*.xcworkspace` after prebuild): set **Signing & Capabilities** → **Team** to your Apple ID; use a unique bundle ID if needed.
3. First install: **Settings → General → VPN & Device Management** → trust your developer certificate.
4. Free Apple ID builds expire after **7 days** — run from Xcode or `npx expo run:ios --device` again to refresh.

**Android notes (brief):**

1. Enable **Developer options** and **USB debugging** on the phone; connect via USB and accept the debugging prompt.
2. Android Studio should install the SDK; `npx expo run:android --device` builds and installs the debug APK.
3. More detail (emulator, JDK, `adb`): [Expo Android workflow](https://docs.expo.dev/workflow/android/).

**Open native IDEs (optional):**

```bash
open ios/*.xcworkspace    # macOS + Xcode
# Android Studio → Open → android/
```

## Project layout

| Path | Purpose |
|------|---------|
| `App.js` | Entry point |
| `src/KneeRehab.js` | Main UI |
| `src/phases.js` | Phase 1–3 exercises and unlock criteria |
| `app.json` | App name (**JointOps**), icons, bundle IDs |
| `assets/` | App icon, splash, favicon |

## Customize app ID / icon

Edit `app.json`:

- **iOS:** `expo.ios.bundleIdentifier` (e.g. `com.poole.jointops`)
- **Android:** `expo.android.package` (same style, must be unique)

After changing IDs or `assets/icon.png`:

```bash
npx expo prebuild --clean
```

Regenerate only one platform if you prefer: `--platform ios` or `--platform android`.

## Publish web demo (GitHub Pages)

The web build is deployed to [PT-knee-recovery-app-web](https://github.com/katpoo123/PT-knee-recovery-app-web) at **https://katpoo123.github.io/PT-knee-recovery-app-web/**.

1. On that repo: **Settings → Pages** → branch **`github-pages`**, folder **`/ (root)`**.
2. From this repo:

```bash
npm run deploy:web
```

`experiments.baseUrl` in `app.json` must match the GitHub Pages path (`/PT-knee-recovery-app-web`). A `.nojekyll` file is included so the `_expo/` assets are published.

## Medical disclaimer

This app is a workout tracker based on your rehab plan. It is not medical advice. Follow your surgeon and physical therapist’s guidance.
