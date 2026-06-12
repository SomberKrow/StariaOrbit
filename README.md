# StariaOrbit

A focused Vue 3 creator hub for **Staria_VT** built around a soft purple Social Galaxy.

The site is intentionally small and polished: a central identity core, orbiting social planets on desktop, a clean constellation-style link queue on mobile, and a minimal signal card for atmosphere.

## Stack

- Vue 3
- Vite
- SCSS
- ESLint
- Component-based structure
- No Tailwind
- No CMS
- No backend

## Install

```bash
npm install
npm run dev
```

## Scripts

```bash
npm run dev      # local development server
npm run build    # production build
npm run preview  # preview production build
npm run lint     # eslint pass
```

## Project Shape

```txt
src/
  assets/
    icons/        # platform SVGs
    images/       # Staria core / visual identity assets
    styles/       # global tokens and base styles
  components/     # focused Vue components
  data/           # editable site copy and social link data
```

## Editing Staria's Links

The main editable content lives in:

```txt
src/data/inSocialLinks.js
```

That file controls:

- Site text
- Social URLs
- Platform descriptions
- Planet size
- Orbit spacing
- Accent colors
- Featured signal copy

## Design Direction

The current direction is:

- Soft purple and darker space
- Slightly mysterious
- Calm orbital motion
- Desktop-first Social Galaxy
- Mobile-friendly link queue
- Minimal Staria-authored copy

## Asset Notes

- `src/assets/images/staria-core.svg` is temporary until Staria has a final logo/core mark.
- Platform icons are clean in-project SVGs. Before public launch, verify brand compliance or replace with official brand assets.
- Desktop uses the orbiting Social Galaxy. Mobile intentionally switches to cards instead of forcing a cramped orbit.
- Reduced motion preferences are respected through CSS.

## Current Goal

Make the first impression feel like opening a quiet little galaxy built around Staria.
