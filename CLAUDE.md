# Hangar 14 Website — Claude Code Instructions

## Project overview

Static marketing website for Hangar 14 gym (Zagreb, Croatia). Vanilla HTML/CSS/JS — no framework, no npm, no build pipeline beyond SASS. Deployed via GitHub Pages to `hangar14.fit`.

## Architecture

- All pages are standalone HTML files at the root
- CSS is split per-page: `style.css` (global) + `index-page.css`, `boarding-pages.css`, `b2b-page.css`, `gabrijela-page.css`
- SASS source lives in `assets/scss/` — **always edit SCSS, never edit `style.css` directly**
- Custom JS is in `assets/js/scripts.js` — vendor libraries (jQuery, Slick, etc.) are also in `assets/js/`
- Images use WebP format wherever possible

## CSS workflow

Edit SCSS files, then compile:

```bash
sass --watch assets/scss/style.scss:assets/css/style.css
```

The page-specific CSS files (`index-page.css`, `boarding-pages.css`, etc.) are written directly — they are not compiled from SCSS.

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

## Deployment

Push to `main` → GitHub Actions deploys automatically to GitHub Pages → live at `hangar14.fit`. No manual deploy step needed. The `CNAME` file must not be deleted.

## What NOT to do

- Do not edit `assets/css/style.css` directly — it is compiled from SCSS and will be overwritten
- Do not add npm, package.json, or any build tooling — this project is intentionally dependency-free
- Do not remove the `CNAME` file
- Do not add the Microsoft Clarity script to new pages if it's not already there — add it consistently or not at all
