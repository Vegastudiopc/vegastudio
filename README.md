# Vega Studio · Pitch

A self-contained HTML pitch deck. No build step, no dependencies.

## Live

`https://pitch.vega.earth`

## Local preview

Open `index.html` directly in a browser, or serve the folder:

```bash
npx serve .
# or
python3 -m http.server 8080
```

## Structure

```
.
├── index.html                  ← the deck (single file, all CSS + JS inline)
├── assets/
│   ├── videos/                 ← .mp4 video clips
│   └── images/                 ← team photos, partner logo cards, community stills
├── VegaStudio_Deck_v1.html     ← versioned source master (same as index.html)
└── VegaStudio_VideoSpec_v1.md  ← spec doc for the video slots
```

## Deploy

Auto-deploys on push (Vercel / Netlify watch the `main` branch).

## Updating

Edit `index.html` and push. Asset paths are relative, so dropping new files into `assets/videos/` or `assets/images/` with the existing filenames hot-swaps the content.

## Keyboard

- `↑ ↓` / `Space` — navigate slides
- `Home` / `End` — jump to first / last
- `F` — toggle fullscreen
