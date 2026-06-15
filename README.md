# Holistic Capital — Website

The public website for [Holistic Capital](https://holisticcapital.xyz). A static
site, no build step, no framework — just HTML, CSS, and a little JavaScript.

## Pages

| File | Purpose |
|---|---|
| `index.html` | The main landing page — the Field, the Eight Forms of Capital, the Hubs, the Team, and how to join. |
| `luminous.html` | The Luminous event page — the Genesis Gathering (1 & 2 August 2026), with Humanitix checkout and a Tally application form for Supported Places. |

Image assets live in the folders prefixed with `_` (`_team`, `_path`, `_events`,
`_hubs`, `_walk`). All images are optimized WebP.

## Run locally

No build needed. Serve the folder with any static server, for example:

```bash
python -m http.server 8000
# then open http://localhost:8000
```

(Opening `index.html` directly as a `file://` works too, though the embedded
Humanitix checkout and Tally form load best over `http://`.)

## Deploy on Vercel

This is a zero-config static site.

1. Push this repository to your own GitHub account (or accept the invite to this one).
2. In Vercel, click **Add New → Project** and **Import** this repository.
3. Framework Preset: **Other**. Leave Build Command empty and set the Output
   Directory to the repository root (the default). Click **Deploy**.
4. Add the custom domain `holisticcapital.xyz` under the project's **Domains** tab
   when ready to go live.

## Third-party embeds

- **Humanitix** — the Luminous checkout (`luminous.html`) embeds event
  `luminous-holistic-capital` via the Humanitix inline widget.
- **Tally** — the Supported Place ($111) application is Tally form `aQlvJb`,
  opened as a modal from the "Apply for a Supported Place" button.
