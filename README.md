# moodcase-quote-cards

Public image host for moodcase Instagram voice-anchor (VA) quote cards.

This repo exists for one reason: to give each quote-card PNG a stable public
URL so it can be attached to a Buffer idea automatically. Buffer pulls post
images by URL, and `raw.githubusercontent.com` serves these files directly.

**This repo is intentionally public** — it contains only finished quote-card
images that are published to Instagram anyway. No strategy, voice, or product
files live here. Those stay in the private `moodcase-content-hub` repo, which
is where the cards are generated.

## Folder convention

A card's location tells you its Buffer status:

- **Repo root** — a new card, generated but NOT yet pushed to Buffer.
- **`_pushed/`** — the card has been pushed to the Buffer Idea Inbox. Once an
  idea exists in Buffer, Buffer keeps its own copy of the image, so moving the
  PNG here does not affect the idea.

The `instagram-quote-batch` task adds new cards at the root, pushes the Buffer
idea, then moves the PNG into `_pushed/`.

## Contents

18 quote slugs, each in two colorways:

- `quote-cloud-{slug}.png` — light (Cloud) variant
- `quote-midnight-{slug}.png` — dark (Midnight) variant

## URL pattern

A card already pushed to Buffer (in `_pushed/`):

```
https://raw.githubusercontent.com/thez-dm/moodcase-quote-cards/main/_pushed/quote-cloud-{slug}.png
https://raw.githubusercontent.com/thez-dm/moodcase-quote-cards/main/_pushed/quote-midnight-{slug}.png
```

A brand-new card not yet pushed sits at the root (no `_pushed/` segment). The
Buffer idea is created using the root URL, then the file is moved to `_pushed/`.
