# moodcase-instagram-cards

Public image host for moodcase Instagram cards — both voice-anchor (VA) quote
cards and moodcase-hack cards.

This repo exists for one reason: to give each card PNG a stable public URL so it
can be attached to a Buffer post automatically. Buffer pulls post images by URL,
and `raw.githubusercontent.com` serves these files directly.

**This repo is intentionally public** — it contains only finished card images
that are published to Instagram anyway. No strategy, voice, or product files
live here. Those stay in the private `moodcase-content-hub` repo, which is where
the cards are generated.

## Commits are automatic — GitHub API, no manual push

This repo is managed entirely via the GitHub REST API, using
`moodcase-content-hub/scripts/github_push.py --repo thez-dm/moodcase-instagram-cards`
— same pattern as `moodcase-media` for AP photos. A card's raw URL is live the
moment it is staged, so a card can be generated, staged, and scheduled in Buffer
in a single run. Never run local git here; if a manual commit is ever needed
(edge case), do it in GitHub Desktop.

## Folder convention

A card's location tells you its Buffer status:

- **Quote cards (VA)** — repo root = staged (NOT yet in Buffer); `_pushed/` =
  scheduled as a Buffer post.
- **Hack cards** — `hacks/` = staged; `hacks/_pushed/` = in Buffer.

Once a post exists in Buffer, Buffer keeps its own copy of the image, so moving
the PNG into a `_pushed/` folder afterward does not affect the post.

The VA workflow (`moodcase-content-hub/social/instagram/va-workflow/moodcase-va/SKILL.md`)
stages new quote cards at the root, schedules the Buffer post, then moves each
PNG into `_pushed/` — all in one run.

## Naming

There is **one card design** — no colorway variants, no colorway naming.

- Quote cards: `quote-{slug}.png`
- If a card is re-rendered after its Buffer post exists (Buffer caches by URL),
  version the filename: `quote-{slug}-v{N}.png`

Files with the legacy colorway names (`quote-midnight-…`, `quote-cloud-…`,
`hack-…-…`) predate July 2026 and stay as they are in `_pushed/` — history is
not renamed.

## URL pattern

```
https://raw.githubusercontent.com/thez-dm/moodcase-instagram-cards/main/quote-{slug}.png            (staged)
https://raw.githubusercontent.com/thez-dm/moodcase-instagram-cards/main/_pushed/quote-{slug}.png    (in Buffer)
```

The Buffer post is created using the root URL, then the file is moved to `_pushed/`.
