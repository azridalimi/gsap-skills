# 9:16 motion-graphic video (GSAP)

Audio-synced vertical video (1080×1920, 30fps) built with one paused `gsap.timeline()` + SplitText, rendered frame-by-frame with Playwright and encoded with ffmpeg.

- `index.html` — scenes, karaoke captions, emoji, colour-graded gradient type. `window.seek(t)` scrubs the master timeline deterministically.
- `spec.json` — per-frame audio spectrum (20 bands) driving the visualizer bars.
- `render.js` — `node render.js <startFrame> <endFrame> out.mp4` (serve this folder over HTTP first).

```bash
npm i gsap@3.13.0 @fontsource/anton @fontsource/space-grotesk
python3 -m http.server 8765 &
node render.js 0 2600 video.mp4
ffmpeg -i video.mp4 -i audio.wav -map 0:v -map 1:a -c:v libx264 -crf 23 -c:a aac -shortest final.mp4
```
