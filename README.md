# Frankenstein Rewind

Frankenstein Rewind is Shivam-M98S’s free click-wheel music player for Android. This preview focuses on Spotify, music stored on your phone, and one Now Playing screen. [Android downloads and release notes](https://github.com/Shivam-M98S/Frankenstein-Rewind/releases)

## Your first listen

For local files, grant Android music access and open **Music**. For Spotify, open **Settings → Library → Spotify setup**, enter your public client ID, and choose **Allow library access**. Return to **Music → Spotify** for playlists and Liked Songs. The browser returns to Rewind after authorization and Rewind stores the refresh token in Android secure storage.

Choose **Connect playback** to control the Spotify app. If the native connection is unavailable, Rewind can control an active Spotify Connect device with an eligible Premium account. Start a song in Spotify first to make that device available. Spotify plays its own audio. Offline downloads inside Spotify stay in Spotify.

## Spotify registration for Rewind Preview

| Setting | Value |
| --- | --- |
| Package | `io.github.shivamm98s.frankensteinrewind.preview` |
| Redirect URI | `frankensteinrewindpreview://auth` |
| Preview signing certificate SHA-1 | `47:23:05:B9:04:A9:FA:9A:14:8F:13:74:F2:9D:54:24:5E:45:98:E5` |

Use a public client ID from the Spotify Developer Dashboard. Development-mode apps require eligible accounts and tester access. These registration values also apply to the signed 0.2.2 preview.

## Testing

Try reopening a playlist after restarting Rewind, letting one track finish, and switching from Spotify to a local file. Include the phone model, Android version, and displayed error when [reporting an issue](https://github.com/Shivam-M98S/Frankenstein-Rewind/issues). Radio and home-server setup are deferred in this preview.

<details>
<summary>Build from source</summary>

The source changes for this preview are in [Rewind.patch](Rewind.patch). From a checkout of this repository, use Flutter 3.47.6 and the Android SDK to build your own debug APK.

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

</details>

## Credits

Frankenstein Rewind builds on ClassiPod. This product includes software developed by Aditya R. [Upstream project](https://github.com/adeeteya/Classipod) · [License](LICENSE)
