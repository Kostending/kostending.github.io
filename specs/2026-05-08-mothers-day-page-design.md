# Mother's Day Page — Design Spec

**Date:** 2026-05-08
**Language:** Danish
**Deployment:** GitHub Pages (static)

## Purpose

A single-page, single-viewport website dedicated to the user's girlfriend for Mother's Day. Displays a YouTube video of their sons, a personal written message, a title, and two photos of the kids.

## Tech Stack

- **SvelteKit** with `@sveltejs/adapter-static` for static export
- **Tailwind CSS** for styling (via official SvelteKit integration)
- **Google Fonts** — Playfair Display (title), Inter (body)
- Output: `docs/` directory, served by GitHub Pages from master root

## Layout

Single viewport, no scrolling. Two-column split:

| Column | Width | Content |
|--------|-------|---------|
| Left | ~55% | YouTube iframe (fills column height) |
| Right | ~45% | Title → Message → Two photos side by side |

The right column is a vertically stacked card with three sections:
1. **Title** — e.g. "Tillykke med mors dag" in Playfair Display serif
2. **Message** — short personal paragraph in Inter, warm dark brown
3. **Photos** — two children's photos side by side, equal width, rounded corners

## Visual Design

- **Background:** warm cream `#FAF7F2`
- **Title/accents:** dusty terracotta `#C27A5E`
- **Body text:** warm dark brown `#3D2B1F`
- **Card background:** soft white `#FFFDF9` with a gentle box shadow
- **Photo corners:** `rounded-xl`
- **Overall feel:** warm, intimate, modern — no harsh blacks or cold blues

## Component Structure

```
src/
  routes/
    +page.svelte          — main two-column layout, title, message text
  lib/
    VideoEmbed.svelte     — YouTube iframe wrapper with aspect-ratio container
static/
  kids-1.svg              — user replaces with actual photo
  kids-2.svg              — user replaces with actual photo
```

### `VideoEmbed.svelte`
- Accepts a `url` prop (YouTube embed URL)
- Renders an iframe that fills its parent container
- `allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"` and `allowfullscreen`

### `+page.svelte`
- Imports `VideoEmbed` and passes a placeholder YouTube URL
- Contains hardcoded Danish title and message (user edits directly)
- References `kids-1.svg` and `kids-2.svg` from `/static`

## Deployment

- `svelte.config.js` uses `adapter-static` with `pages: 'docs'` and `assets: 'docs'`
- A `.nojekyll` file is placed in `static/` so GitHub Pages skips Jekyll
- GitHub Pages configured to serve from the `/docs` folder on the master branch
- To deploy: run `npm run build` (outputs to `docs/`) then commit and push `docs/` to master

## What the User Customises

1. YouTube URL in `src/routes/+page.svelte` (passed to `VideoEmbed`)
2. Title text and message body in `src/routes/+page.svelte`
3. Replace `static/kids-1.svg` and `static/kids-2.svg` with actual photo files
