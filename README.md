# Frankenstein Rewind

A click-wheel music player for Android. Spin through your Spotify Liked Songs, hold the center button to queue a track, or pin a playlist to the home menu under a name of your choice. Night Drive switches the player to a graphite shell with amber text and album art.

The first Android test release is being prepared.

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

## Feedback

[Report a test result](https://github.com/Shivam-M98S/Frankenstein-Rewind/issues) with your phone model, Android version, the action you tried, and what happened. If playback worked, tell us which controls you tested.

## Credits

Frankenstein Rewind builds on [ClassiPod](https://github.com/adeeteya/Classipod). This product includes software developed by Aditya R. See [LICENSE](LICENSE).
