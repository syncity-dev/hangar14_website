# Hangar 14 — Marketing Website

Static marketing website for **Hangar 14**, a functional fitness gym located at Paviljon 14, Avenija Dubrovnik 15, Zagreb, Croatia.

Live at: [hangar14.fit](https://hangar14.fit)

---

## Pages

| File | URL | Description |
|------|-----|-------------|
| `index.html` | `/` | Homepage — hero slider, training programs, pricing, class schedule, trainer profiles, contact |
| `boarding.html` | `/boarding` | Boarding Pass — free one-week trial offer for new members |
| `b2b.html` | `/b2b` | B2B Boarding Pass — corporate team fitness program (3–10 people) |
| `gabrijela.html` | `/gabrijela` | Personal trainer page for Gabrijela Bađun — packages and booking |
| `qr.html` | `/qr` | QR code landing page for printed materials (flyers, posters) |

---

## Tech Stack

- **HTML5 / CSS3 / Vanilla JS** — no framework, no build pipeline beyond SASS
- **SASS** — source in `assets/scss/`, compiled to `assets/css/style.css`
- **jQuery 2.2.4** — DOM manipulation and plugin dependencies
- **Slick.js** — hero image carousel and content sliders
- **Parallax.js** — section parallax scrolling
- **Fancybox** — lightbox/modal
- **Isotope** — masonry grid layout
- **rx-lazy** — image lazy loading
- **Bootstrap Grid** — 12-column responsive grid (CSS only, no JS)
- **Font Awesome** — icon fonts
- **PHP** — `assets/php/contact.php` handles contact form submission
- **GitHub Pages** — deployment via GitHub Actions, custom domain via `CNAME`

---

## Project Structure

```
hangar14_website/
├── index.html
├── boarding.html
├── b2b.html
├── gabrijela.html
├── qr.html
├── CNAME                        # GitHub Pages custom domain
├── assets/
│   ├── css/                     # Compiled stylesheets (do not edit directly)
│   │   ├── style.css            # Main compiled CSS
│   │   ├── index-page.css       # Homepage-specific styles
│   │   ├── boarding-pages.css   # Shared boarding/B2B/trainer styles
│   │   ├── b2b-page.css
│   │   └── gabrijela-page.css
│   ├── scss/                    # SASS source (edit these)
│   │   ├── style.scss           # Entry point — imports all partials
│   │   ├── _structure.scss
│   │   ├── _normalize.scss
│   │   ├── _typography.scss
│   │   ├── _header.scss
│   │   ├── _forms.scss
│   │   ├── _footer.scss
│   │   └── _site.scss
│   ├── js/
│   │   ├── scripts.js           # Custom JS (navigation, sliders, map, forms)
│   │   └── [vendor libs]
│   ├── img/                     # Site images (WebP preferred)
│   ├── fonts/                   # Font Awesome icon fonts
│   └── php/
│       └── contact.php          # Contact form backend
└── .github/workflows/           # GitHub Actions deployment
```

---

## Local Development

No npm or build tools required beyond SASS.

**1. Compile SASS (watch mode)**

```bash
sass --watch assets/scss/style.scss:assets/css/style.css
```

**2. Serve locally**

Open any HTML file directly in a browser, or use a simple local server:

```bash
# Python
python3 -m http.server 8080

# VS Code
# Use the Live Server extension
```

> Note: The contact form (`contact.php`) requires a PHP server to function. It will not work when opening files directly from the filesystem.

---

## Deployment

The site deploys automatically to GitHub Pages on every push to `main` via the workflow in `.github/workflows/`. The custom domain `hangar14.fit` is configured in the `CNAME` file.

---

## Content Notes

- **Pricing** — membership prices and package details are in `index.html` and `gabrijela.html`
- **Timetable** — class schedule table is in `index.html`
- **B2B slots** — monthly slot count and team size limits are in `b2b.html`
- **Contact** — phone (+385 91 560 9234), email (team@hangar14.fit), WhatsApp, Instagram (@hangar14.fit)
- **Analytics** — Microsoft Clarity (tag `pq6kf678a9`) is loaded on all pages
