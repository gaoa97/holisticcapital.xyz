# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

The public marketing website for [Holistic Capital](https://holisticcapital.xyz).
It is a **static site with no build step and no framework** — hand-written HTML,
CSS, and vanilla JS. There is no `package.json`, no bundler, no test suite.

## Commands

```bash
# Serve locally (no build needed)
python -m http.server 8000   # then open http://localhost:8000
```

Use a real `http://` server (not `file://`) so the Humanitix checkout and Tally
form embeds on `luminous.html` load correctly.

Deploy is **zero-config on Vercel**: the repo root is the output directory, no
build command. `vercel.json` only sets `cleanUrls` (so `/luminous` serves
`luminous.html`) and disables trailing slashes.

## Architecture

Each page is a **single self-contained `.html` file** with all CSS in one inline
`<style>` block in the `<head>` and all JS in one inline `<script>` at the end of
`<body>`. There are no shared/external `.css` or `.js` files — when you change a
shared concern (header, brand lockup, button styles), it must be edited in **both**
`index.html` and `luminous.html` to stay consistent.

- `index.html` — main landing page (the Field, Eight Forms of Capital, Hubs, Team, join).
- `luminous.html` — the Luminous event page (Genesis Gathering, 1–2 Aug 2026) with
  Humanitix checkout + a Tally modal form (`aQlvJb`) for $111 Supported Places.

Folders prefixed with `_` (`_team`, `_people`, `_path`, `_events`, `_hubs`, `_walk`)
hold **only optimized WebP/JPG image assets** — they are not Jekyll collections or
code. Reference them with root-absolute paths.

### Conventions to preserve

- **Design tokens** live in the `:root` CSS custom properties block (`--blue:#07b0e8`,
  the warm eight-capital spectrum `--c-spiritual`…`--c-intellectual`, fonts
  `--display` Newsreader / `--ui` Inter). Style with these variables, not raw hex.
- **No em-dashes** in copy (see the header comment in `index.html`).
- The fixed header restyles on scroll: it toggles a `.solid` class (white background)
  via a scroll listener, and the brand mark recolors through the `--mark-bg` variable.
  Section reveal-on-scroll uses an `IntersectionObserver` adding an `.in` class to
  `.reveal` elements.
- Team cards and the eight-capital legend are rendered client-side from JS data
  arrays (`CAPS8`, team data) — update the array, not hand-written markup.
- A versioned changelog comment sits at the top of `index.html`'s `<head>`; bump/note
  significant page changes there as has been the pattern.
