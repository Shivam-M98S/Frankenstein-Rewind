# Frankenstein Rewind

A click-wheel music player for Android. Spin through your Spotify Liked Songs, hold the center button to queue a track, or pin a playlist to the home menu under a name of your choice. Night Drive switches the player to a graphite shell with amber text and album art.

**[Download the Galaxy S10 test APK](https://github.com/Shivam-M98S/Frankenstein-Rewind/releases/download/v0.1.0-alpha.1/Frankenstein-Rewind-S10.apk)**

This ARM64 debug build targets early testers. The build and APK signature have been verified. Playback on a physical Galaxy S10 is awaiting confirmation.

## Try it on Android

1. Download and open the APK on your phone. Android may ask you to allow installation from the app that opened it.
2. Open **Spotify  Night Drive** to try the theme.
3. Open **Spotify  Pin playlist link**, paste a playlist link and give it a name. Return to the main menu to find your shortcut.

## Connect Spotify

Spotify plays the audio through its Android app. Install Spotify and sign in on the same device. This alpha uses a public client ID supplied by the tester. For library access, use a Premium developer account and allowlist your tester account if it differs from the app owner.

In the [Spotify Developer Dashboard](https://developer.spotify.com/dashboard), register an app for Android SDK and Web API access with these settings.

| Setting | Value |
| --- | --- |
| Android package | `com.adeeteya.classipod.frankensteinrewind` |
| Redirect URI | `frankensteinrewind://auth` |
| Signing certificate SHA-1 | `9F:46:B5:3F:9E:06:31:4A:DF:4B:AE:95:AE:BF:5B:36:20:AA:ED:1B` |

Open **Spotify  Spotify setup** in Rewind and paste your **public client ID**. Open **Liked Songs** to grant access and choose a track. Hold the center button on another track to add it to the queue.

## Build from source

The source changes for this alpha are in [Rewind.patch](Rewind.patch). From a checkout of this repository, use Flutter 3.47.6 and the Android SDK to build your own debug APK.

```sh
git clone https://github.com/adeeteya/Classipod.git player
git -C player checkout --detach 772a6d3533677bfa78f9251a40df8fa8ca3e6180
git -C player apply ../Rewind.patch
cd player
flutter pub get
flutter gen-l10n
dart run build_runner build --delete-conflicting-outputs
flutter build apk --debug --flavor dev --target-platform android-arm64
```

For a self-built APK, register your own signing certificate fingerprint with Spotify.

## Library upgrade preview

The 0.2 preview installs alongside the original S10 alpha. Look for the new package `io.github.shivamm98s.frankensteinrewind` in Android App info. The two installs keep separate settings.

- **Settings → Library → Spotify setup** stores your public client ID on the device. Register the new Android package and the certificate SHA-1 supplied with your specific build. Keep the original redirect URI. Android may ask which installation should open the callback.
- **Home Server** browses an SMB shared folder. Add its address and credentials in Library settings. Selected tracks are copied to the Android cache before playback. Music servers using Subsonic or Navidrome have their own setup in Library.
- **Radio** opens a country directory, station search, favorites, and custom URLs. Long-press a station to toggle its favorite status. Individual broadcasters control their streams.
- Long-press a Home item to move, pin or hide it. Restore default order from Settings’ Home row. Library settings include album and track sorting and optional online artwork lookup. Turning artwork lookup on submits album and artist names to Apple’s catalog.
- **Experimental** includes a glass-style bezel, narrower side margins and an opt-in local-audio spectrum. The spectrum requires Android audio permission and uses the local player’s audio session.
- **Now Playing** follows the active player. Liked Songs queues subsequent tracks from the loaded list. Use Load more before playing to extend it.

## Support Rewind

Rewind is free. You can support development by testing a build, starring the repository or reporting a playback issue. A payment link will appear here once the maintainer supplies a verified destination.

## Feedback

[Report a test result](https://github.com/Shivam-M98S/Frankenstein-Rewind/issues) with your phone model, Android version, the action you tried, and what happened. If playback worked, tell us which controls you tested.

## Credits

Frankenstein Rewind builds on [ClassiPod](https://github.com/adeeteya/Classipod). This product includes software developed by Aditya R. See [LICENSE](LICENSE).
