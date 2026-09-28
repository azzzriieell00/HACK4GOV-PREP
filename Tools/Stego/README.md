# Steganography Tools — Red Team Guide

## 60-Second Decision Tree

    ├── Image → exiftool, strings, binwalk, zsteg, steghide
    ├── Audio → Audacity spectrogram
    ├── Video → ffmpeg extract frames
    └── Text → zero-width chars

## Images — Full Sequence

    exiftool image.jpg
    strings image.jpg | grep -i flag
    binwalk -e image.jpg
    steghide extract -sf image.jpg
    zsteg -a image.png

## Audio Files

    exiftool audio.wav
    audacity audio.wav
    # Track → Spectrogram
    steghide extract -sf audio.wav

## Video Files

    ffmpeg -i video.mp4 frames/frame_%04d.png
    ffmpeg -i video.mp4 -vn audio.wav

## Text Files

    cat -A text.txt
    xxd text.txt

## Quick Reference

| Task | Command |
|------|---------|
| Metadata | exiftool image.jpg |
| Strings | strings image.jpg |
| Embedded files | binwalk -e image.jpg |
| Steghide | steghide extract -sf image.jpg |
| LSB (PNG) | zsteg -a image.png |
| Audio stego | Audacity spectrogram |

## Critical Tips
1. Always exiftool first
2. Always strings
3. Always binwalk -e
4. Audio → check spectrogram
5. If "password" in challenge → steghide

## Links
- StegOnline: https://stegonline.georgeom.net/
- Aperi'Solve: https://www.aperisolve.com/
