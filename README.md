# Music Player

A single-file music player for Mac Miller's *Swimming*, built as a design exercise in HTML, CSS, and vanilla JS.

**[Live demo →](https://thinhngx.github.io/music-player/)**

---

## Features

**Player**
- Full and mini player modes with animated expand/collapse transitions
- Play / pause, previous / next, shuffle
- Queue panel — inline in mini mode, side panel in full mode
- Smooth entrance animations (opacity + blur + translate) on every appearing element

**Background**
- Random photo from Unsplash loaded on each visit via [picsum.photos](https://picsum.photos)
- WebGL domain-warp shader slowly morphs the image in real time
- `backdrop-filter` blur layer + SVG fractal noise grain sit above the canvas
- Fades in once the image is ready

**Weather widget**
- Bottom-left corner, Geist Mono typeface
- Reads your location via the browser Geolocation API
- Fetches current temperature and conditions from [Open-Meteo](https://open-meteo.com) (no API key)
- Reverse-geocodes city and country via [Nominatim](https://nominatim.org)
- Format: `Now is 24°C, sunny. Ho Chi Minh City, VN.`

**App container**
- Fills the viewport with 16px margin on all sides, 10px corner radius
- Body background adapts to system light / dark mode preference
- 1px inset outline at 10% opacity

---

## Stack

| Concern | Approach |
|---|---|
| Audio | SoundCloud Widget API (hidden iframe) |
| Background warp | WebGL fragment shader — domain warping with value noise |
| Blur | CSS `backdrop-filter` |
| Grain | Inline SVG `feTurbulence` tiled via `background-image` |
| Weather | Geolocation API + Open-Meteo + Nominatim |
| Fonts | System UI + Geist Mono (Google Fonts) |
| Build | None — single `index.html` |

---

## Running locally

```bash
cd music-player
python3 -m http.server 3000
# open http://localhost:3000
```

The SoundCloud Widget API and weather geolocation both require a proper HTTP origin — opening `index.html` directly as a `file://` URL will not work.
