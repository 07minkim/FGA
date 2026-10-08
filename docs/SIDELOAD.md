# Sideload FGA with APKMirror Installer

This guide shows how to install a custom FGA APK on an Android device or emulator. It uses APKMirror Installer, so Android does not block the FGA Accessibility service.

## Why use APKMirror Installer

- Android 13 and later have a feature named "Restricted settings". It blocks Accessibility and Notification Listener access for sideloaded apps. ([Android Authority](https://www.androidauthority.com/android-15-restricted-settings-sideloading-3481098/))
- Android decides if an app is "sideloaded" from the install method. Apps installed with the session-based install API (the API that app stores use) are not restricted.
- A file manager or browser uses the non-session install method. Then the FGA Accessibility toggle is greyed out.
- APKMirror Installer uses the session-based install API.

**Note:** If your device or emulator runs Android 12 or lower, Restricted settings do not exist. A normal install works. Check the Android version in **Settings → About phone**.

## Requirements

- An Android device or emulator with Google Play.
- The FGA APK file. Get it from this repo: **Actions → select a successful build → Artifacts**. Download and unzip the artifact.

## Procedure

1. Install [APKMirror Installer](https://play.google.com/store/apps/details?id=com.apkmirror.helper.prod) from Google Play.
2. Copy the FGA APK to the device. For an emulator, drag the file onto the emulator window, or use the shared-folder feature of the emulator.
3. Open APKMirror Installer.
4. Tap **Browse files**. Select the FGA APK.
5. Tap **Install package**. If the app shows an ad, wait for it to end.
6. When Android asks, allow APKMirror Installer to install unknown apps. Then approve the install prompt.
7. Open FGA. Tap **Start Service**.
8. Give all the permissions that FGA asks for. This includes the Accessibility service and screen capture.

## If the Accessibility toggle is still greyed out

1. Try to enable the FGA Accessibility service one time. Close the "Restricted setting" dialog.
2. Go to **Settings → Apps → FGA**.
3. Tap the **⋮** menu at the top-right corner.
4. Tap **Allow restricted settings**. Confirm with your PIN or pattern.
5. Enable the FGA Accessibility service again.

Reference: [DroidWin guide](https://droidwin.com/?p=28677)

## Known limits

- Android 15 makes Restricted settings mandatory for Accessibility, "Display over other apps", and default-app roles. ([Android Authority](https://www.androidauthority.com/android-15-restricted-settings-sideloading-3481098/))
- Android 15 also adds "Enhanced Confirmation Mode". It can block apps installed through the session-based loophole. ([Android Authority](https://www.androidauthority.com/android-15-enhanced-confirmation-mode-3436697/)) Thus APKMirror Installer may not work on all Android 15+ devices. Use the "Allow restricted settings" procedure above in this case.
- A custom build signed with a different key cannot install over the official FGA app. Uninstall the official app first, or give the custom build a different `applicationId`.
