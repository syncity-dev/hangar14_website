# Hangar 14 Website — Claude Code Instructions

## Project overview

Static marketing website for Hangar 14 gym (Zagreb, Croatia). Vanilla HTML/CSS/JS — no framework, no npm, no build pipeline. Deployed via GitHub Pages to `hangar14.fit`.

## Architecture

- All pages are standalone HTML files at the root
- CSS is split per-page: `style.css` (global) + `index-page.css`, `boarding-pages.css`, `b2b-page.css`, `gabrijela-page.css`
- All CSS is plain vanilla CSS, edited directly — there is no SASS/build step
- Custom JS is in `assets/js/scripts.js` — vendor libraries (jQuery, Slick, etc.) are also in `assets/js/`
- Images use WebP format wherever possible

## CSS workflow

Edit the `.css` files directly. No compile step.

### Design tokens

Color is driven by CSS custom properties defined in `:root` at the top of `style.css` (loaded on every page):

- **Yellow** — Radix-style 12-step brand scale; `--yellow-9` (`#fad437`) is the brand accent. Includes a P3 wide-gamut `@supports` refinement.
- **Sand** — Radix-style 12-step neutral scale (dark column).
- **Semantic aliases** — reference these from page CSS, not the raw scales: `--color-accent`, `--color-accent-hover`, `--color-text`, `--color-text-secondary`, `--color-text-muted`, `--color-border`.

Use `var(--color-accent)` for the brand yellow — never hardcode `#fad437`. Native CSS nesting and custom properties are available; no preprocessor needed.

## Content locations

| Content | File | Notes |
|---------|------|-------|
| Homepage hero, programs, pricing | `index.html` | Pricing, timetable, program descriptions |
| Class timetable | `index.html` | HTML `<table>` in the schedule section |
| Membership prices | `index.html` | Drop-in, Student, 3x/week, Unlimited tiers |
| B2B program details | `b2b.html` | Team size, slots, challenge description |
| Personal trainer packages | `gabrijela.html` | 1:1, 2:1, 3:1 pricing |
| Contact info | All pages | Phone, email, WhatsApp, Instagram, Maps |

## Key conventions

- **No comments** unless the intent is genuinely non-obvious
- **Mobile-first** responsive design using Bootstrap 12-column grid (CSS only)
- **Images** — use `data-lazy` attribute for lazy-loaded images (rx-lazy.js)
- **Icons** — Font Awesome classes (`fa fa-*`)
- **WhatsApp links** use `https://wa.me/385...` with pre-filled `text=` param
- Contact email: `team@hangar14.fit`; trainer email: `gabrijela61@gmail.com`
- Phone: `+385 91 560 9234`
- Instagram: `@hangar14.fit`
- Analytics: Microsoft Clarity tag `pq6kf678a9` — present in `<head>` of every page

## Verification before pushing

**Always run `/verify` on every page affected by a change before suggesting or making a `git push`.** This is a visual marketing site — layout regressions are only caught by eyes, not by tests or type checks.

Verification checklist:
- Open the changed page(s) via a local server (`python3 -m http.server 8080`)
- Check the modified section at desktop (≥1200px), tablet (~900px), and mobile (~375px)
- Confirm no other sections on the page are broken

## Deployment

Push to `main` → GitHub Actions deploys automatically to GitHub Pages → live at `hangar14.fit`. No manual deploy step needed. The `CNAME` file must not be deleted.

## What NOT to do

- Do not add npm, package.json, SASS, or any build tooling — this project is intentionally dependency-free
- Do not hardcode brand colors — reference the design tokens (`var(--color-accent)`, etc.) in `style.css`
- Do not remove the `CNAME` file
- Do not add the Microsoft Clarity script to new pages if it's not already there — add it consistently or not at all
