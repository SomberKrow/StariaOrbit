# Staria VT — First Orbit Alpha

A clean `v1.0.0-alpha.0` Vue 3 prototype for Staria VT's cosmic creator hub.

This build is intentionally focused: one polished page, one strong Social Galaxy, one clean foundation for redesign and iteration.

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
npm run build    # production build when ready
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
  data/           # editable social link data
```

## Important Alpha Notes

- Social links live in `src/data/inSocialLinks.js`.
- Replace the placeholder URLs with Staria's verified links before production.
- Replace `src/assets/images/staria-core.svg` with her final logo/favicon when available.
- The platform icons are clean in-project alpha SVGs. For public launch, verify brand compliance or replace with official brand assets.
- Desktop uses the orbiting Social Galaxy.
- Mobile switches to constellation cards instead of forcing a broken orbit.
- Reduced motion preferences are respected through CSS.

## Version Target

`v1.0.0-alpha.0 — First Orbit Alpha`

Goal: establish the real foundation for the Staria VT site before expanding scope.
