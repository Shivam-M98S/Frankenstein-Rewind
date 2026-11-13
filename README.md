# Frankenstein Rewind

Frankenstein Rewind is a free click-wheel music player for Android by **Shivam-M98S**. Spin through albums on your phone, pin a Spotify playlist to Home, or tune into a live station from Suriname. Use **Now Playing** on the main menu to get back to the track.

**[Download the Android APK · 0.2.0 alpha 1 · 200 MB](https://github.com/Shivam-M98S/Frankenstein-Rewind/releases/download/v0.2.0-alpha.1/Frankenstein-Rewind-0.2.0-alpha.1.apk)** · [Read the changelog](https://github.com/Shivam-M98S/Frankenstein-Rewind/releases/tag/v0.2.0-alpha.1)

## Music Home preview for Android

[Download Rewind Preview · 0.2.1 alpha 1 · 200 MB](https://github.com/Shivam-M98S/Frankenstein-Rewind/releases/download/v0.2.1-alpha.1/Frankenstein-Rewind-Music-Preview.apk) · [Preview release notes and checksums](https://github.com/Shivam-M98S/Frankenstein-Rewind/releases/tag/v0.2.1-alpha.1)

Install **Rewind Preview** alongside 0.2.0 to try the new menus. Open **Music → Playlists** to choose Spotify or device playlists. Open **Music → Cover Flow → Spotify albums** to browse your saved album covers with the wheel. Start a track and press Menu to see its cover on Home. **Now Playing** shows the artist, album, playback time and transport controls. Settings is the last item on Home.

To use Spotify in this preview, add the following entries to your existing Spotify Developer app and save them. Keep the registrations for other builds you still use.

| Spotify setting | Preview value |
| --- | --- |
| Android package | `io.github.shivamm98s.frankensteinrewind.preview` |
| Package SHA-1 | `D3:C0:D0:1C:1C:79:87:E0:93:70:67:1F:6C:6F:EF:EC:0F:3B:39:4B` |
| Redirect URI | `frankensteinrewindpreview://auth` |

On the phone, open **Settings → Library → Spotify setup**, enter the same public client ID, and choose **Connect Spotify**. Allow Android music access for audio files stored on your phone. Spotify handles its own offline downloads.

## Your first listen in 0.2.0

Open the APK on your Android phone to install it. This test build installs alongside the first S10 alpha and keeps its own settings. For a quick first listen, open **Radio → Suriname**, pick a station, and long-press it to save it to Favorites.

| Where to go | What you can do |
| --- | --- |
| **Music** | Browse songs and albums stored on your phone. Choose your sort order under Library settings. |
| **Spotify** | Browse Liked Songs and playlists. Hold the center button on a track to add it to the queue, or pin a playlist to Home under a name you choose. Spotify plays the audio through its Android app. |
| **Home Server** | Browse an SMB shared folder on your PC or NAS. Rewind copies each selected track to the Android cache before playing it. Subsonic-compatible servers such as Navidrome have a separate setup option in Library settings. |
| **Radio** | Browse by country, search for a station by name, or add a broadcaster’s stream URL. |

## Make it yours

- **Arrange Home.** Long-press an item to move it, pin it to the top, or hide it. You can restore the default layout from the same menu.
- **Switch on Night Drive.** Open Spotify → Night Drive for a graphite shell and amber text. The Spotify section also follows the normal app theme.
- **Try the experimental display options.** Settings → Experimental includes a glass-style bezel, narrower S10 edge margins, and a live spectrum for local tracks. The spectrum uses Android audio permission.
- **Fill in missing artwork.** Rewind reads embedded art and checks the album folder for a cover image. Optional online lookup sends the artist and album names to Apple’s catalog and caches matching covers.

## Connect Spotify

Install Spotify and sign in on the same device. This alpha uses a public client ID supplied by the tester. For library access, use a Premium developer account and allowlist your tester account if it differs from the app owner.

In the [Spotify Developer Dashboard](https://developer.spotify.com/dashboard), register an app for Android SDK and Web API access with these settings.

| Setting | Value |
| --- | --- |
| Android package | `io.github.shivamm98s.frankensteinrewind` |
| Redirect URI | `frankensteinrewind://auth` |
| Signing certificate SHA-1 | `1A:D7:A1:80:CE:BA:2F:FF:22:66:7D:22:29:D6:7B:C2:BC:34:44:80` |

Open **Settings → Library → Spotify setup** in Rewind and paste your **public client ID**. Open **Liked Songs** to grant access and choose a track. Hold the center button on another track to add it to the queue.

## Testing and feedback

The APK build and signing certificate have been verified. Physical-device testing of this version is open. Useful reports include the phone model, Android version, music source, and what happened. To check Spotify playback, start a Liked Song, open Now Playing from Home, then lock the phone and let the next track begin. [Report a test result](https://github.com/Shivam-M98S/Frankenstein-Rewind/issues)

<details>
<summary>Build from source</summary>

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

</details>

## Credits

Frankenstein Rewind builds on ClassiPod. This product includes software developed by Aditya R. [Upstream project](https://github.com/adeeteya/Classipod) · [License](LICENSE)
