<p align="center"><img src="fastlane/metadata/android/en-US/images/icon.png" width="150"></p>
<h1 align="center"><b>Sonaro</b></h1>
<h4 align="center">A local music player for Android, forked from <a href="https://github.com/OxygenCobalt/Auxio">Auxio</a>.</h4>
<p align="center">
    <a href="https://www.gnu.org/licenses/gpl-3.0">
        <img alt="License" src="https://img.shields.io/badge/license-GPL%20v3-0D9488.svg?style=flat">
    </a>
    <img alt="Minimum SDK Version" src="https://img.shields.io/badge/API-24%2B-14B8A6?style=flat">
    <a href="https://github.com/OxygenCobalt/Auxio">
        <img alt="Based on Auxio" src="https://img.shields.io/badge/based%20on-Auxio-2DD4BF?style=flat">
    </a>
</p>
<h4 align="center"><a href="/CHANGELOG.md">Changelog</a> | <a href="/FORK_CHANGES.md">Changes from Auxio</a> | <a href="#credits">Credits</a></h4>

## About

Sonaro is a hard fork of [Auxio](https://github.com/OxygenCobalt/Auxio), the local music player by
Alexander Capehart (OxygenCobalt). It keeps Auxio's fast, reliable UI/UX and its modern playback and
library stack, and keeps merging upstream changes.

Sonaro is a separate app with its own name, icon, and application ID (`app.sonaro`), so it installs
next to Auxio and shares no data with it. **It is not affiliated with or supported by the Auxio
project. Please report Sonaro problems [here](https://github.com/shear99/Sonaro/issues), not to Auxio.**

Right now Sonaro behaves like the Auxio development version it was forked from. Every change made to
upstream files is listed in [FORK_CHANGES.md](/FORK_CHANGES.md).

## Screenshots

These are upstream Auxio's screenshots. The interface is currently the same.

<p align="center">
    <img src="fastlane/metadata/android/en-US/images/phoneScreenshots/shot0.png" width=250>
    <img src="fastlane/metadata/android/en-US/images/phoneScreenshots/shot1.png" width=250>
    <img src="fastlane/metadata/android/en-US/images/phoneScreenshots/shot2.png" width=250>
    <img src="fastlane/metadata/android/en-US/images/phoneScreenshots/shot3.png" width=250>
    <img src="fastlane/metadata/android/en-US/images/phoneScreenshots/shot4.png" width=250>
    <img src="fastlane/metadata/android/en-US/images/phoneScreenshots/shot5.png" width=250>
</p>

## Features

- Playback based on [Media3 ExoPlayer](https://developer.android.com/guide/topics/media/exoplayer)
- Snappy UI derived from the latest Material Design guidelines
- Opinionated UX that prioritizes ease of use over edge cases
- Customizable behavior
- Support for disc numbers, multiple artists, release types,
precise/original dates, sort tags, and more
- Advanced artist system that unifies artists and album artists
- SD Card-aware folder management
- Reliable playlisting functionality
- Playback state persistence
- Android Auto support
- Automatic gapless playback
- Full ReplayGain support (On MP3, FLAC, OGG, OPUS, and MP4 files)
- External equalizer support (ex. Wavelet)
- Edge-to-edge
- Embedded covers support
- Search functionality
- Headset autoplay
- Stylish widgets that automatically adapt to their size
- Completely private and offline
- No rounded album covers (if you want them)

## Permissions

- Storage (`READ_MEDIA_AUDIO`, `READ_EXTERNAL_STORAGE`) to read and play your music files
- Services (`FOREGROUND_SERVICE`, `WAKE_LOCK`) to keep the music playing in the background
- Notifications (`POST_NOTIFICATION`) to indicate ongoing playback and music loading

## Credits

Sonaro exists because of Auxio. Nearly all of the code in this repository was written by
[Alexander Capehart (OxygenCobalt)](https://github.com/OxygenCobalt) and the
[Auxio contributors](https://github.com/OxygenCobalt/Auxio/graphs/contributors), and the full upstream
history is preserved in this repository.

If you like what Sonaro is built on, please consider
[sponsoring Auxio's author](https://github.com/sponsors/OxygenCobalt). Donations made there support
Auxio, not Sonaro.

## Building

Auxio relies on a patched version of Media3 that enables some extra playback features, alongside taglib for metadata
parsing. This adds some caveats to the build process:
1. `cmake` and `ninja-build` must be installed before building the project.
2. The project uses submodules, so when cloning initially, use `git clone --recurse-submodules` to properly
download the external code.
3. You are **unable** to build this project on windows, as the custom Media3 build runs shell scripts that
will only work on unix-based systems.

### Set up Android Studio

#### Install Android Studio.

```bash
pkg -S android-studio
```

#### Configuring Android Studio:

- Be sure to have NDK tools, version 28.2.13676358. You can search it on Languages & Frameworks > Android SDK.
- Install Java-21 with your system package manager

    ```bash
    sudo pkg -S jdk21-openjdk
    ```
    Additionally: Set java version to jdk21-openjdk

- Run ./gradlew assembleDebug

#### Connecting to your Android Device

You can connect your Mobile Phone through USB to run the app. 

1. **Enable Developer Options on your phone**
   - Go to **Settings > About phone**  
   - Tap **Build number** 7 times until you see *"You are now a developer!"*

2. **Enable USB debugging**
   - Go to **Settings > Developer options**  
   - Turn on **USB debugging**

3. **Connect your phone to the computer**
   - Use a USB cable  
   - On your phone, accept the *Allow USB debugging?* prompt

4. **Verify that your device is detected**
   ```bash
   cd ~/Android/Sdk/platform-tools
   ./adb devices
   ```

Android Studio also offers virtual devices that come with this pre-configured.

#### Install the app on the Android Phone
To install the app on your physical device or emulator, run this command:

```bash
./gradlew installDebug
```

Auxio should now appear in the list of Apps

#### Load music to Auxio (Optional)

You can move files from your pc to your device / emulator to test the music using this command:

```bash
cd ~/Android/Sdk/platform-tools
./adb push ~Music/ /sdcard/Music
```

## Contributing

Issues and pull requests for Sonaro are welcome in [this repository](https://github.com/shear99/Sonaro).
See the [Contribution Guidelines](/.github/CONTRIBUTING.md).

If a bug also happens in Auxio itself, it is best fixed upstream, and Sonaro will pick the fix up with
its next upstream merge. Translations of the strings inherited from Auxio are maintained in
[Auxio's Weblate project](https://hosted.weblate.org/engage/auxio/).

## License

[![GNU GPLv3 Image](https://www.gnu.org/graphics/gplv3-127x51.png)](http://www.gnu.org/licenses/gpl-3.0.en.html)

Sonaro is Free Software: You can use, study, share and improve it at your
will. Specifically you can redistribute and/or modify it under the terms of the
[GNU General Public License](https://www.gnu.org/licenses/gpl.html) as
published by the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

Sonaro is a modified version of Auxio, Copyright (c) Auxio Project, which is licensed under the same
terms. The original copyright and license notices are kept in every source file. Modifications began
in November 2026 and are recorded in the git history and in [FORK_CHANGES.md](/FORK_CHANGES.md).

Licenses of the bundled third-party components are listed on
[Auxio's wiki](https://github.com/OxygenCobalt/Auxio/wiki/Licenses).
