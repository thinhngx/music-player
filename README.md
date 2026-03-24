# Conditional®

A single-file music player with a weather-aware daily playlist. **[Live →](https://thinhngx.github.io/conditional-player/)**

---

## How it works

Each day the player fetches Hanoi's 7 AM weather, maps it to a genre, and pulls 12 tracks from Jamendo. Tracks don't repeat for 7 days. The playlist is cached locally and refreshes at midnight.

| Weather | Genre |
|---|---|
| Clear | happy / pop |
| Breezy | indie / folk |
| Overcast | chill / indie |
| Foggy | dreamy / atmospheric |
| Drizzle | jazz / café |
| Rain | blues / soul |
| Snow | classical / piano |
| Storm | instrumental / post-rock |

To block a genre, add it to `GENRE_BLACKLIST` in `index.html`. Each condition has a fallback chain so the player always finds something to play.

## Stack

- **Audio** — Jamendo API (CC-licensed, 96kbps streams, no key needed beyond a free client ID)
- **Weather** — Open-Meteo + Nominatim (no API keys)
- **Background** — WebGL domain-warp shader on a random picsum.photos image, `backdrop-filter` blur layer, SVG grain
- **UI** — Vanilla HTML/CSS/JS, no build tools

## Run locally

```bash
python3 -m http.server 3000
# open http://localhost:3000
```

> Opening as `file://` won't work — geolocation and audio APIs require HTTP.
