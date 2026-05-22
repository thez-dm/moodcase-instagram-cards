# moodcase-quote-cards

Public image host for moodcase Instagram voice-anchor (VA) quote cards.

This repo exists for one reason: to give each quote-card PNG a stable public
URL so it can be attached to a Buffer idea automatically. Buffer pulls post
images by URL, and `raw.githubusercontent.com` serves these files directly.

**This repo is intentionally public** — it contains only finished quote-card
images that are published to Instagram anyway. No strategy, voice, or product
files live here. Those stay in the private `moodcase-content-hub` repo.

## Contents

36 PNGs — 18 quote slugs, each in two colorways:

- `quote-cloud-{slug}.png` — light (Cloud) variant
- `quote-midnight-{slug}.png` — dark (Midnight) variant

## URL pattern

```
https://raw.githubusercontent.com/thez-dm/moodcase-quote-cards/main/quote-cloud-{slug}.png
https://raw.githubusercontent.com/thez-dm/moodcase-quote-cards/main/quote-midnight-{slug}.png
```

## How it stays current

The `instagram-quote-batch` scheduled task (defined in `moodcase-content-hub`)
generates new quote cards every ~2 weeks. It commits each new PNG here and then
pushes a matching image idea to the Buffer Idea Inbox.
