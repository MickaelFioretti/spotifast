This personal build brings everything in Spotifast 0.13.0 together with smart shuffle. Spotifast 0.13.0 plays on Google Cast speakers, checks a release signature before it installs an update, removes one song from the queue, polls your other devices less often and fixes much more. On top of it, the shuffle button gains a smart setting that weaves Spotify's suggestions into what you play.

**Download:** [Windows](https://github.com/MickaelFioretti/spotifast/releases/download/v0.13.0/spotifast-v0.13.0-x86_64-pc-windows-msvc.msi) · [Windows setup program](https://github.com/MickaelFioretti/spotifast/releases/download/v0.13.0/spotifast-v0.13.0-x86_64-pc-windows-msvc-setup.exe) · [Linux](https://github.com/MickaelFioretti/spotifast/releases/download/v0.13.0/spotifast-v0.13.0-x86_64-unknown-linux-gnu.tar.gz)

## New

- **Smart shuffle.** Press the shuffle button a second time for smart shuffle: the playlist or album plays in a random order with one song Spotify suggests after every three of its own. A suggested song carries a sparkle in the queue, the track list and the player, so it is never mistaken for one you chose. Smart shuffle needs playback on this computer; on another device the button offers shuffle on and off only. By @themazim.
- **Updates come from this build and carry its signature.** The in-app updater checks this fork's releases, so an upstream release without smart shuffle never replaces it. From this release on, an update installs only when its `checksums.txt` is signed with this build's own key.
- **Everything in Spotifast 0.13.0:** Google Cast speakers and groups, a Windows Installer package, Ukrainian, upcoming albums and Pre-save, removing one song from the queue, a By You playlist filter, less motion when the system asks for it, a faster start, lower battery use, and playback checked at most every 15 seconds instead of every 4. See the [Spotifast 0.13.0 release notes](https://github.com/crmne/spotifast/releases/tag/v0.13.0) for the full list and its contributors.

## Known limits

- Smart shuffle weaves the songs already loaded, so a very long playlist weaves its loaded page.
- Switching to smart shuffle while something plays applies from the next playlist or album you start.
- Playback starts once the suggestions have arrived.
- Only Windows x64 and Linux x64 are built. The installer is not signed for Windows, so SmartScreen may ask for confirmation the first time.

## Thanks

@themazim for smart shuffle, @crmne and everyone who contributed to Spotifast 0.13.0.

**Full changelog**: https://github.com/MickaelFioretti/spotifast/compare/v0.12.0...v0.13.0
