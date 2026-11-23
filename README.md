# Audio Trimmer

A simple, private audio trimmer that runs entirely in your browser. Pick a file, choose where it starts and ends, add a fade in and fade out, polish the sound with echo, reverb, EQ and a compressor, then save the result. Nothing is uploaded anywhere.

## Features

- Load most audio files your browser can play (MP3, M4A, WAV, AAC, and more)
- Drag the start and end handles on the waveform, or type exact times in seconds
- Fade in and fade out sliders, with the fade shown on the waveform
- Effects: echo (delay), reverb, a simple EQ (low cut, bass, mid, treble) and a compressor to even out loud and quiet parts
- Ready-made effect presets (Smooth voice, Warm, Small room, Concert hall, Quick echo, Long echo)
- Preview the trimmed and faded result with your effects before saving. You can move the effect sliders while it plays
- Export as MP3, WAV, or M4A (AAC)
- Type your own file name before exporting (Vietnamese and other accented letters are kept). It starts as `yourfile-trimmed`, and the ending (`.mp3`, `.wav`, `.m4a`) is added for you
- Works on iPhone and desktop

## How to use

1. Tap **Choose audio file** and pick a recording.
2. Drag the orange handles to set the start and end. Tapping the waveform moves the nearest handle.
3. Set **Fade in** and **Fade out** if you want them.
4. Pick an **Effects preset**, or open Echo, Reverb, EQ and Compressor and move the sliders yourself. **Reset** turns all effects off.
5. Tap **Preview** to listen. Tap again to stop.
6. Choose an **Export format** (and a quality for MP3 and M4A), edit the **File name** if you like, then tap **Export** to save the trimmed file.

## Effects

| Effect | What it does |
| --- | --- |
| Echo | Repeats the sound after a short delay. **Amount** is how loud the echoes are, **Delay time** is the gap between repeats, and **Repeats** is how long they keep going. Each repeat is a bit darker and quieter. |
| Reverb | Adds the feel of a room. **Amount** is how much you hear, and **Room size** is how long it rings out (0.3 s is a small room, 6 s is a big hall). |
| EQ | **Low cut** removes rumble and hum below the chosen pitch. **Bass**, **Mid** and **Treble** make low, middle and high sounds louder or softer by up to 12 dB. |
| Compressor | **Smoothing** evens out loud and quiet parts so voices and music feel steadier and fuller. Higher is stronger. |

Effects are applied in this order: EQ, compressor, then echo and reverb. A gentle safety limiter keeps the result from distorting. The effects apply to every export format, and the fades are applied before the effects.

Echo and reverb ring out after the clip ends, so the saved file is a little longer than the selection. The page shows how much longer.

## Export formats

| Format | Best for | Notes |
| --- | --- | --- |
| MP3 | Sharing and playing almost anywhere | Fast. Quality from 96 to 320 kbps (192 by default). |
| WAV | Editing in other apps, full quality | Lossless 16-bit, but the biggest files. |
| M4A (AAC) | Small files for Apple devices | Records in real time, so it takes as long as the clip. Keep the screen on. Only shown if your browser supports it. Browsers without M4A offer WebM or Ogg (Opus) instead. |

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The whole app (HTML, CSS, JavaScript, and the MP3 encoder in one file) |
| `audio-trimmer-icon.png` | 180x180 Home Screen icon for iPhone |
| `README.md` | This file |

## Publish on GitHub Pages

1. Put `index.html` and `audio-trimmer-icon.png` in the root of a GitHub repo.
2. Commit both files. Editing a local copy alone changes nothing until it is committed.
3. In the repo, go to **Settings > Pages**, set the source to your main branch (root folder), and save.
4. Wait a minute or two, then open the Pages URL.

## Add to iPhone Home Screen

1. Open the Pages URL in Safari.
2. Tap Share, then **Add to Home Screen**.

If the icon shows a gray placeholder letter instead of the waveform icon:

1. Confirm `audio-trimmer-icon.png` is committed in the same folder as `index.html`.
2. Wait 1-2 minutes for GitHub Pages to update.
3. Delete the old Home Screen shortcut and quit Safari.
4. Reload the page and add it to the Home Screen again.

## Notes

- MP3 export uses [lamejs](https://github.com/zhuker/lamejs) (LGPL-3.0), bundled inside `index.html`. MP3 files are always 44.1 or 48 kHz and at most 2 channels.
- M4A export uses your browser's built-in recorder, which is why it runs in real time. If the screen locks or you switch apps while it records, iOS may stop it, so use MP3 or WAV for long clips.
- Very long files use more memory, since the browser decodes the whole file to trim it.
- Effects are processed in your browser, so they can sound a little different between Safari, Chrome and other browsers. Preview what you hear and adjust to taste.
- Echo and reverb tails make the saved file longer. M4A (real-time recording) also takes that extra time to save.
- The fade length can never be longer than the selected section. If the two fades together would be longer, the other one shortens.
- Everything happens on your device. The page itself still needs an internet connection to load, since there is no offline mode.
