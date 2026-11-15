# [**Multi POV Viewer**](https://rachmawan123.github.io/multi-pov-viewer/)

A lightweight multi-screen YouTube viewer for watching several player perspectives at once, with manual timeline alignment, drift correction, and flexible audio mixing.

**Watch every POV. Keep the right conversation audible.**

## Features

- **Multi-stream grid** — Load multiple YouTube videos, VODs, and embeddable live streams.
- **Master POV** — Choose the reference video used by the synchronization engine.
- **Per-POV offsets** — Align streams that started at different times.
- **Capture current alignment** — Pause on the same gameplay moment and calculate each stream's offset automatically.
- **Prepare & Start** — Briefly wait for buffering, apply offsets, and send play commands to the synchronized group together.
- **Drift correction** — Periodically compare playback positions and seek streams back into alignment when they drift significantly.
- **Three audio modes** — Smart Focus, Single POV / Discord, and Proximity / Manual Mix.
- **Individual volume and mute** — Fine-tune every POV independently.
- **Quick audio focus** — Select a POV's audio directly from its player tile.
- **Responsive grid** — Auto, 1, 2, 3, or 4 columns.
- **Convenience controls** — Individual playback, fullscreen, rename, Follow sync, and global controls.
- **Local settings** — POV links, names, offsets, volume, and preferences are saved in the current browser.

## Getting Started

1. Open the [Live Demo](https://rachmawan123.github.io/multi-pov-viewer/).
2. Paste YouTube links, one per line, and select **Add POVs**.
3. Choose a **Master POV**. This is the reference timeline; it does not have to be the earliest stream.
4. Pause all streams when they show the same gameplay event.
5. Select **Capture current alignment**. The app records each POV's time difference from the Master.
6. Use **Apply offsets** to seek all synchronized POVs to the corresponding moment.
7. Select **Prepare & Start** to wait briefly for buffering and start the group.
8. Leave **Drift correction** enabled to correct larger playback differences while the Master is playing.

### Understanding offsets

An offset is the difference between a POV's playback timestamp and the Master's timestamp at the same gameplay moment.

- Positive offset: seek further into that POV.
- Negative offset: seek earlier in that POV.
- The Master always has an offset of zero.

You can also edit offsets manually in seconds or adjust them in 5-second steps. If you change the Master, the app rebases the offsets to preserve the existing alignment.

## Audio Modes

| Mode | Behavior | Best for |
|---|---|---|
| **Smart Focus** | The selected POV stays at its normal volume; other POVs are reduced to the Background Volume setting. | Proximity chat when you want to hear quieter conversations from other players. |
| **Single POV / Discord** | Only the selected Focus POV is audible. | Everyone shares the same Discord voice channel. |
| **Proximity / Manual Mix** | Every unmuted POV plays at its own volume. | Listening to several separate proximity-chat conversations. |

Use **Focus** on a tile or the Focus POV selector to switch the selected audio source. Individual mute and volume settings remain available in every mode. Master Audio can mute or unmute all POVs.

## Keyboard Shortcuts

| Shortcut | Action |
|---|---|
| SPACE | Play / pause the Follow sync group |
| F11 | Browser fullscreen |
| ESC | Exit fullscreen |

## Important Limitations

- The app synchronizes YouTube playback timestamps using offsets; it does not recognize gameplay events automatically.
- YouTube's IFrame Player API does not expose frame-accurate synchronization or a guaranteed buffer-ready signal. Start timing is therefore approximate.
- Drift correction uses playback-time comparisons and seeks when a playing POV differs from the target by more than approximately 2.2 seconds.
- Live stream seeking depends on YouTube's DVR/seek availability. Some live streams cannot seek far enough, or at all.
- Audio mixing is based on the selected POV and volume levels. The app cannot detect who is speaking or automatically identify which conversation matters.
- Some videos block embedded playback. This is controlled by the video owner and YouTube.
- An internet connection is required for YouTube playback.

## Technology

- HTML5, CSS3, vanilla JavaScript
- YouTube IFrame Player API
- GitHub Pages

## Privacy and Storage

Playback preferences and the list of added POVs are stored in local browser storage on the device where the app is used. They are not synchronized between devices. Clearing browser site data removes these saved settings.

## License

Personal project. All rights to YouTube videos belong to their respective owners.
