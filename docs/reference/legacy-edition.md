# PPSSPP Legacy Edition for Android

![Legacy Logo](/static/img/platform/ppsspp-icon-legacy.png)

## Features

The PPSSPP Legacy Edition is really just the same as a regular PPSSPP build, except it has been built specifying an old target Android SDK version (29, specifically).

This means that it's not affected by the Scoped Storage requirement of Android 11+, meaning that it can work without a folder browser app being available on your device, which helps on Android TV devices.

## Installation

Legacy Edition is only available as an APK. You'll need to figure out how to install APKs on your device.

When you install it, you may be asked to confirm that you really want to install it, since this app does not live up to modern Android security requirements. This is fine.

However, PPSSPP built this way cannot be uploaded to the Play Store due to Google's restrictions, and must be side-loaded.

## Download

The Legacy Edition can be downloaded from the [buildbot](/devbuilds), the AndroidLegacy build, starting at version 1.17.1-980. Later it might be made available on the main Downloads page.

Alternatively, the Legacy Edition can be built from source code using the gradle subcommand `assembleLegacyOptimized`.
