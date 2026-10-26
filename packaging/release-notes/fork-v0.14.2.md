This personal build brings everything in Spotifast 0.14.2 together with smart shuffle. Spotifast 0.14.2 starts with your computer, plays the local files in your playlists, fills Home with what you played last, reconnects playback after a network drop and fixes signing in for the first time. On top of it, the shuffle button in a playlist or album now matches the player's, and a smart-shuffled playlist shows its Pause button.

**Download:** [Windows](https://github.com/MickaelFioretti/spotifast/releases/download/v0.14.2/spotifast-v0.14.2-x86_64-pc-windows-msvc.msi) · [Windows setup program](https://github.com/MickaelFioretti/spotifast/releases/download/v0.14.2/spotifast-v0.14.2-x86_64-pc-windows-msvc-setup.exe) · [Linux](https://github.com/MickaelFioretti/spotifast/releases/download/v0.14.2/spotifast-v0.14.2-x86_64-unknown-linux-gnu.tar.gz)

## New

- **One shuffle button.** The shuffle button next to a playlist's or album's Play button, and the one on New Releases, are now the player's own: the same setting, the same sparkle for smart shuffle, and a press moves through off, shuffle and smart shuffle in the same order. Before, turning shuffle back on there could quietly bring smart shuffle back under the plain shuffle icon.
- **Pause for a smart-shuffled playlist.** A playlist or album playing in smart shuffle now shows Pause on its page, and the button pauses it instead of starting it over.
- **Everything in Spotifast 0.13.1 to 0.14.2:** start with your computer, local files in playlists, what the people you follow are listening to, a fuller Home, skips that start at once, playback that keeps going through a dropped connection, this computer's audio output in the device picker, Korean, Play next, your own equalizer presets, and a first sign-in that works again. See the release notes for [0.13.1](https://github.com/crmne/spotifast/releases/tag/v0.13.1), [0.13.2](https://github.com/crmne/spotifast/releases/tag/v0.13.2), [0.13.3](https://github.com/crmne/spotifast/releases/tag/v0.13.3), [0.14.0](https://github.com/crmne/spotifast/releases/tag/v0.14.0), [0.14.1](https://github.com/crmne/spotifast/releases/tag/v0.14.1) and [0.14.2](https://github.com/crmne/spotifast/releases/tag/v0.14.2) for the full list and their contributors.

## Known limits

- Signing in for the first time now needs your own free Spotify app, made from a Premium account, as in Spotifast 0.14.2; the sign-in screen guides you through it. If you are already signed in, nothing changes.
- Smart shuffle weaves the songs already loaded, so a very long playlist weaves its loaded page.
- Switching to smart shuffle while something plays applies from the next playlist or album you start.
- Playback starts once the suggestions have arrived.
- Only Windows x64 and Linux x64 are built. The installer is not signed for Windows, so SmartScreen may ask for confirmation the first time.

## Thanks

@themazim for smart shuffle, @crmne and everyone who contributed to Spotifast 0.13.1 to 0.14.2.

**Full changelog**: https://github.com/MickaelFioretti/spotifast/compare/v0.13.0...v0.14.2
