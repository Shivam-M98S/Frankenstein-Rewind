# Frankenstein Rewind public release plan

The Music Home preview is the baseline for S10 testing. This branch stages source changes. Building the public APK is a separate decision.

## First listen

A new user should be able to play a station or a file on their phone before creating an account. On first use of device music, explain Android's music permission. If access is declined, keep Radio and Home Server available and offer a retry from Music. Ask for the server address only when someone adds a server.

Spotify should have a single Connect playback action for testers. Distribute the public client ID with the build once a release identity has been registered. The branch supports the compile-time value `SPOTIFY_CLIENT_ID` and honors a tester's saved override. Spotify library authorization has its own action and is also available when someone actually browses their library. The current SDK uses the older Android token flow. Migrate library sign-in to authorization code with PKCE, with secure refresh-token storage and invalid-grant recovery, before relying on it for public use.

## Android release identity

Keep the current previews available for testers. Before a production release, choose one permanent Android package and one backed-up release signing key, managed outside Git. Register that package, certificate fingerprint and production callback once. Build releases with the production flavor, increment the version code, and check that one signed release installs over another with playlists and settings intact. Existing disposable-key alphas will need a one-time migration. Keep the signed test apps until migration has been verified.

Public GitHub downloads and Spotify API access have different requirements. Local files, radio and home servers can be the public features. Label Spotify library support as a limited beta while the developer app remains in development mode. Spotify documents a maximum of five authenticated accounts in that mode.

## Visual direction

Keep the dashboard layout, click wheel, center-button actions, row heights and Menu/back behavior. Use an optional Liquid theme throughout the screen contents. Centralize its colors, selected-row treatment, title bars and panel surfaces. Keep menus readable over album art, provide a solid fallback, and check scrolling on the S10 with Night Drive and Edge both enabled.

Use one preview rule across sections. Music and Now Playing show the current cover when available. Radio shows a station logo with a radio icon fallback. Home Server shows a drive icon and server name. Settings shows a gear. Test these previews before commissioning full-screen wallpapers.

## Features worth testing

1. Add a wheel-accessible Up Next view. Start with local files and home-server playback, where Rewind owns the queue. Keep Spotify actions within the controls available for the current session.
2. Add named playback bookmarks for long mixes and audiobooks, including track, position and source. Offer Resume from a long press on the item.
3. Give Now Playing more space for the album art. Test a single translucent transport strip, accessible with both touch and the wheel.

## Code and device checks

The existing Rewind screen handles Spotify browsing, SMB folders, radio, experimental settings and Now Playing in one widget. This branch extracts Spotify library HTTP requests and setup messages. Future splits should follow these features while keeping the routes and wheel behavior stable. The current public repository uses a patch against a pinned upstream commit. For outside contributions, move to a normal browsable Flutter source tree with upstream attribution and reproducible release instructions.

Test first launch with local music permission granted and denied. Check Spotify missing, logged out, authorization cancelled, library access denied, network offline and expired session. Test Spotify Home artwork, automatic next track, S10 contrast, wheel response, and installation over a previous stable-signed build.

## References

- [Tanner Villarete's iPod.js](https://github.com/tvillarete/ipod-classic-js)
- [Doppi's artwork and Up Next](https://doppi.app/)
- [Rockbox iPod Classic manual, bookmarks](https://device.report/m/1c66d368245b4a64d703db6ee5a6732d56128672fe014357c721250e319df522.pdf)
- [Spotify quota modes](https://developer.spotify.com/documentation/web-api/concepts/quota-modes)
- [Spotify Android authorization migration](https://developer.spotify.com/documentation/android/tutorials/migration-token-code)
- [Android application signing](https://developer.android.com/studio/publish/app-signing)
