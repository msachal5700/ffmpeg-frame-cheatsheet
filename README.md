# ffmpeg: extract frames from video — cheatsheet

Copy-paste `ffmpeg` recipes for the most common frame-extraction jobs.

**Don't want the command line?** Do it in your browser, free, no uploads:
**[videotoimagesequence.online](https://www.videotoimagesequence.online)**

---

## 1 frame per second as JPG

```bash
ffmpeg -i input.mp4 -vf fps=1 frame_%04d.jpg
```

## 1 frame every 5 seconds

```bash
ffmpeg -i input.mp4 -vf fps=1/5 frame_%04d.jpg
```

## Every frame as PNG (lossless)

```bash
ffmpeg -i input.mp4 frame_%04d.png
```

## High-quality JPG (q:v 2 = best, 31 = worst)

```bash
ffmpeg -i input.mp4 -q:v 2 frame_%04d.jpg
```

## Frames between 10s and 20s only

```bash
ffmpeg -ss 10 -to 20 -i input.mp4 frame_%04d.jpg
```

## Single frame at an exact timestamp (e.g. 00:01:23.500)

```bash
ffmpeg -ss 00:01:23.500 -i input.mp4 -frames:v 1 thumbnail.jpg
```

## Frame as WebP

```bash
ffmpeg -i input.mp4 -vf fps=1 frame_%04d.webp
```

## Extract + scale down to 1280px wide (smaller files)

```bash
ffmpeg -i input.mp4 -vf "fps=1,scale=1280:-1" frame_%04d.jpg
```

---

## Notes

- `%04d` numbers the output: `frame_0001.jpg`, `frame_0002.jpg`, …
- `-ss` before `-i` seeks fast (less accurate); after `-i` seeks accurately but slower. For thumbnails, accurate seeking matters.
- JPG quality: `-q:v 2` ≈ visually lossless; `-q:v 5` is a good size/quality trade-off.

## No-install alternative

[videotoimagesequence.online](https://www.videotoimagesequence.online) —
drag & drop a video, pick FPS or every-N-seconds, download frames as
JPG/PNG/WebP. Free, private (files never leave your browser), no signup.

## License

MIT — use these recipes anywhere.
