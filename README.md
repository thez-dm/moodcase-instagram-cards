# moodcase-instagram-cards

Public image host for moodcase Instagram cards — both voice-anchor (VA) quote
cards and moodcase-hack (MH) cards.

This repo exists for one reason: to give each card PNG a stable public URL so it
can be attached to a Buffer idea automatically. Buffer pulls post images by URL,
and `raw.githubusercontent.com` serves these files directly.

**This repo is intentionally public** — it contains only finished card images
that are published to Instagram anyway. No strategy, voice, or product files
live here. Those stay in the private `moodcase-content-hub` repo, which is where
the cards are generated.

## Folder convention

A card's location tells you its Buffer status:

- **Quote cards** — repo root = staged (NOT yet pushed to Buffer); `_pushed/` =
  already pushed to the Buffer Idea Inbox.
- **Hack cards** — `hacks/` = staged (NOT yet pushed); `hacks/_pushed/` =
  already pushed.

Once an idea exists in Buffer, Buffer keeps its own copy of the image, so moving
the PNG into a `_pushed/` folder afterward does not affect the idea.

The `instagram-quote-batch` task stages new quote cards (at the root), pushes the
Buffer idea, then moves each PNG into `_pushed/`. Hack cards follow the same
staged → pushed flow under `hacks/`.

## Contents

Each slug is produced in two colorways:

- `quote-cloud-{slug}.png` / `hack-cloud-{slug}.png` — light (Cloud) variant
- `quote-midnight-{slug}.png` / `hack-midnight-{slug}.png` — dark (Midnight) variant

## URL pattern

Quote card already pushed to Buffer (in `_pushed/`):

```
https://raw.githubusercontent.com/thez-dm/moodcase-instagram-cards/main/_pushed/quote-cloud-{slug}.png
https://raw.githubusercontent.com/thez-dm/moodcase-instagram-cards/main/_pushed/quote-midnight-{slug}.png
```

A brand-new quote card not yet pushed sits at the root (no `_pushed/` segment).
The Buffer idea is created using the root URL, then the file is moved to `_pushed/`.

Hack card (staged in `hacks/`, then `hacks/_pushed/` once pushed):

```
https://raw.githubusercontent.com/thez-dm/moodcase-instagram-cards/main/hacks/hack-cloud-{slug}.png
https://raw.githubusercontent.com/thez-dm/moodcase-instagram-cards/main/hacks/hack-midnight-{slug}.png
```
