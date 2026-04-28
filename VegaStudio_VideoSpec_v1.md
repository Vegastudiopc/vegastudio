# VEGA STUDIO — Pitch Deck v1
## Video Content Specification

This is the delivery spec for every video slot in `VegaStudio_Deck_v1.html`. Drop files named exactly as listed into:

```
CLAUDE OUTPUTS/VEGA STUDIO/assets/videos/
```

Once a file is in place, its placeholder pattern disappears and the video auto-plays muted/looped in the slide.

---

### Global specs (apply to every video unless noted)

| Property | Spec |
|---|---|
| Container | `.mp4` (H.264, yuv420p) |
| Resolution | 1920×1080 min (deck scales responsively) |
| Frame rate | 24 or 30 fps |
| Duration | 6–12s loop (seamless in/out recommended) |
| Audio | Muted / stripped (browsers block autoplay with audio) |
| Bitrate | ~4–8 Mbps (balance quality + web weight) |
| Compression tip | `ffmpeg -i in.mov -c:v libx264 -pix_fmt yuv420p -crf 22 -an out.mp4` |
| Poster fallback | Optional `.jpg` with the same filename if you want a first-frame image |

> **Performance note:** Aim for each video file ≤ 8MB. Total deck weight ≤ 80MB. Compress aggressively — no one watches a pitch deck buffer.

---

## Slide-by-slide video map

### `10` — GEN-SYNTH Hero (full-bleed)
- **File:** `gensynth-hero.mp4`
- **Aspect:** 16:9 full-bleed (cover)
- **Duration:** 10–15s
- **Source candidate:** AI-generated anime establishing shot (cyberpunk city, protagonist reveal) OR compiled title sequence
- **Vibe:** Cinematic establishing. Slow camera move. Neon city. Character back-of-head moving into frame.
- **Treatment:** Video plays behind a coral/black gradient — no subtitles needed. Color-graded teal/amber.
- **Fallback:** If no video, the placeholder card already shows the GEN-SYNTH mark in brand colors.

### `11` — GEN-SYNTH: The World (right panel, 16:9 card)
- **File:** `gensynth-pilot.mp4`
- **Aspect:** 16:9
- **Duration:** 6–10s loop
- **Source candidate:** Clip from the 48-hour pilot — the most striking shot of the protagonist or environment
- **Vibe:** Style bible. Motion should feel hand-crafted anime, not generic AI gloss.

### `13` — GEN-SYNTH: The Game + Marketplace (right panel)
- **File:** `gensynth-game.mp4`
- **Aspect:** 16:9 (or 9:16 crop inside a 16:9 frame if only mobile capture exists)
- **Duration:** 8–12s loop
- **Source candidate:** Screen capture of the endless-runner loop OR marketplace UI pan
- **Vibe:** Gameplay + UI. Energy forward. Show the economy layer working.

### `14` — GEN-SYNTH: The Product / PRESQ (right panel)
- **File:** `gensynth-product.mp4`
- **Aspect:** 16:9
- **Duration:** 6–10s loop
- **Source candidate:** Shelving final.mov (in your Videos folder!) — the shelving render is perfect for a product-IP visual. Trim + compress.
- **Cash wrap sequence test_08.mp4** would also work here as a retail/physical context piece.
- **Vibe:** Digital IP becoming physical. Slow product hero shot, turntable or dolly.

### `15` — GEN-SYNTH: Community (6-tile gallery)
- **Files:** `assets/images/community-01.jpg` … `community-06.jpg` (static stills, not video)
- **Aspect:** Cell aspect ~3:2, so 1200×800 works
- **Source candidate:** Photos from the Gen-Synth arcade activations (slide 23 in original deck)
- **If you want motion instead:** Swap the gallery to 6 short 3–4s loops (`community-01.mp4` etc.). Otherwise stills are crisper here.

### `19` — Proof Wall (5 brand cells)
- **File list:**
  - `jordan-brand.mp4` — hero cell (large left, 2x height)
  - `nike-airmax.mp4`
  - `hov.mp4`
  - `amazon-drake.mp4`
  - `mcdonalds.mp4`
- **Aspect:** Varies by cell. All videos cover-cropped, so deliver 16:9 and let CSS handle.
- **Duration:** 4–8s seamless loops (these play simultaneously — keep short)
- **Source candidate for Jordan hero:** The Jordan retail CGI render you already have in the deck PDF. Request clip from the agency edit.
- **Nike:** `Timeline transition draft_14 (1).mp4` from your Videos folder may fit here — it's already cut and short.
- **HOV:** Capture from the Book of HOV install (Brooklyn Library, 2023)
- **Amazon × Drake:** The isometric warehouse render animated — even a slow parallax pan works
- **McDonald's:** HBCU car scene clip (from the campaign final cut)
- **Vibe note:** Keep these muted, fast, punchy. They should feel like a TV wall of proof.

---

## Existing video files I found in your `/Videos` folder

These are already in the project and worth mapping:

| File | Size | Recommended slot |
|---|---|---|
| `AF08C31D-3DFD-48A9-9D9E-5D4514C0D56D.MP4` | 101 MB | Compress + consider for Slide 10 (Gen-Synth hero) — is this the game trailer? |
| `Cash wrap sequence test_08.mp4` | 59 MB | Slide 14 (Gen-Synth product, retail context) or Slide 19 (Jordan hero cell) |
| `Shelving final.mov` | 3.2 GB | Slide 14 (PRESQ product) — needs heavy compression. Try 8 Mbps mp4. |
| `Timeline transition draft_14 (1).mp4` | 76 MB | Slide 19 (Nike cell) or as an inter-slide transition |
| `DTLR-ANNAPOLIS-6748 2.jpg` | 6 MB | Slide 19 (add a DTLR cell) or community |
| `IMG_3369.jpg` | 946 KB | Reference / B-roll still |

### One-liner to batch-compress:
```bash
cd "/Users/vega/Desktop/Claude Cowork/PROJECTS/VEGA STUDIO /PITCH DECK/ASSETS/Videos"
for f in *.mov *.mp4 *.MP4; do
  ffmpeg -i "$f" -c:v libx264 -pix_fmt yuv420p -vf "scale=1920:-2" -crf 23 -preset fast -an \
    "../../../../CLAUDE OUTPUTS/VEGA STUDIO/assets/videos/$(basename "${f%.*}").mp4"
done
```

---

## Production priorities (if you only shoot/edit 3 things)

1. **GEN-SYNTH hero reel** — single most important asset in the deck. 10–15s cinematic cut. Use Runway for new shots if needed.
2. **GEN-SYNTH game capture** — mobile screen rec of the endless-runner + a marketplace scroll. 2-cam edit.
3. **Jordan or Nike hero clip** — the proof wall needs at least ONE video playing. Jordan is the stronger anchor for Slide 19.

Everything else can ship with the static placeholders (they're already styled and don't break the deck).

---

## Aspect ratio cheatsheet

| Slide context | Aspect |
|---|---|
| Hero full-bleed (Slide 10) | 16:9, cover-crop |
| Right-panel media card (11, 13, 14) | 16:9 |
| Proof-wall hero cell (Slide 19 Jordan) | Tall 3:4 or 2:3 works better; deliver 16:9 and CSS crops |
| Proof-wall side cells | 16:9 |
| Community gallery (Slide 15) | 3:2 stills |

---

## Filename checklist

Copy these filenames into your videos folder exactly:

```
gensynth-hero.mp4
gensynth-pilot.mp4
gensynth-game.mp4
gensynth-product.mp4
jordan-brand.mp4
nike-airmax.mp4
hov.mp4
amazon-drake.mp4
mcdonalds.mp4
```

Optional / community stills:
```
community-01.jpg … community-06.jpg
gensynth-poster.jpg   (first-frame poster for the hero slide)
```

When these files land in `assets/videos/` (or `assets/images/`), the placeholders auto-hide and the real media takes over.
