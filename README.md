# Jiunge Upate SACCO — Website

A complete, production-ready static website for **Jiunge Upate SACCO Society Ltd (J.U.S.S Ltd)** — a Christian-based savings and credit cooperative society established in 2015 by members of PCEA Dandora Church, Nairobi.

The site is built with plain HTML, CSS, and vanilla JavaScript — no frameworks, no build step. Just open `index.html` in a browser and it runs.

---

## File & folder structure

```
jiunge-upate-sacco/
│
├── index.html              ← Homepage (hero, values strip, about teaser, services preview, CTA)
├── about.html              ← About page (story, vision/mission, 9 core values, future projections)
├── services.html           ← Services page (4 loans, 3 savings products, insurance, withdrawal policy)
├── membership.html         ← Membership page (tabbed Individual / Corporate / Self-Help requirements)
├── contact.html            ← Contact page (info, contact form, location card)
│
├── css/
│   └── styles.css          ← All site styles (design tokens, components, page-specific styles)
│
├── js/
│   └── main.js             ← Sticky nav, mobile menu, scroll reveal, tab switcher, form handler
│
├── assets/
│   └── logo.svg            ← Standalone SVG logo mark (used as favicon)
│
└── README.md               ← This file
```

Every HTML page links to the same `css/styles.css` and `js/main.js`, so editing those files updates the entire site at once.

---

## Pages — what's on each one

### `index.html` — Homepage
- Animated word-by-word hero headline with three layered floating cards (Instant Loan, Own Deposit Loan, Holiday Savings) and a green disc backdrop.
- Three top-level stats: *10+ years, 7 products, 9 core values*.
- Continuous scrolling marquee of all nine core values.
- About teaser with a vision/mission pillar pair.
- Six-card services preview (one featured in dark green).
- CTA banner with phone number callout.

### `about.html` — About
- Full origin story with **2015** as a giant editorial date.
- Vision and Mission cards (one light, one dark).
- 3×3 grid of the nine core values with Roman numerals.
- Three "Future Projections" cards — land/housing finance, insurance & investments, financial literacy.

### `services.html` — Services
- Four loan products as detailed list rows with hover animation.
- Three savings products as colored cards (Normal, Corporate, Holiday).
- Featured insurance contribution panel (KES 150 monthly).
- Two-card withdrawal policy section (shares vs. deposits).

### `membership.html` — Membership
- Three-way tabbed interface: **Individual / Corporate / Self-Help Group** — each tab swaps requirements and fee tables.
- Numbered requirements list and fee breakdown for each path.
- Four-step process timeline (Visit → Submit → Begin Contributing → Welcome).

### `contact.html` — Contact
- Three contact methods (visit, call, email) with icons.
- Pull-quote block with the SACCO's tagline.
- Multi-field contact form with success state on submit.
- Stylized location card for PCEA Dandora Church.

---

## Design system

The whole visual language lives in CSS variables at the top of `css/styles.css`. To rebrand or theme, change the tokens — everything cascades.

**Colour palette**
| Token | Value | Use |
| --- | --- | --- |
| `--bg` | `#f6f1e6` | Warm cream — primary background |
| `--bg-soft` | `#ede4cf` | Deeper cream — alternating sections |
| `--green` | `#1c4a35` | Deep forest green — primary brand |
| `--green-deep` | `#0f2e21` | Almost-black green — dark sections |
| `--terra` | `#c2410c` | Terracotta — accent / highlights |
| `--gold` | `#d4a437` | Warm gold — sun accents in logo |
| `--ink` | `#18201b` | Body text |

**Typography**
- **Display:** [Fraunces](https://fonts.google.com/specimen/Fraunces) — variable serif with optical sizing, soft and wonk axes used for italic emphasis.
- **Body:** [Plus Jakarta Sans](https://fonts.google.com/specimen/Plus+Jakarta+Sans) — clean, modern sans-serif.

Both fonts load from Google Fonts at the top of `styles.css`.

**Motion**
- Hero headline: word-by-word fade-up with staggered animation delays.
- Sections: `.reveal` class fades elements up as they enter the viewport (via `IntersectionObserver` in `main.js`).
- Marquee values strip: continuous CSS scroll.
- All hovers use `cubic-bezier(0.22, 1, 0.36, 1)` easing.

**Visual details**
- Subtle SVG noise overlay across the entire body (`body::before`).
- Soft-blurred coloured "blobs" behind the hero echoing the brochure's organic shapes.
- Each section gets a numbered eyebrow (`— 01 / Loans`).
- Italic display lettering (Fraunces SOFT/WONK axes) used as accent throughout.

---

## How to run

This is a static site. There is no build step, no package manager, no server requirement.

**Option 1 — Just open it.**
Double-click `index.html` and it opens in your browser. Done.

**Option 2 — Use a local server (recommended for development)**

Pick whichever you have:

```bash
# Python 3
python3 -m http.server 8000

# Node.js (with npx)
npx serve .

# PHP
php -S localhost:8000
```

Then visit `http://localhost:8000` in your browser.

---

## How to deploy

The site is fully static — drop the entire `jiunge-upate-sacco/` folder onto any static host:

- **Netlify** — drag-and-drop deploy at app.netlify.com/drop
- **Vercel** — `vercel deploy` from the project folder
- **GitHub Pages** — push to a repo, enable Pages on the `main` branch
- **Cloudflare Pages**, **Surge.sh**, **Render**, etc.

Or simply upload the folder via FTP/cPanel to traditional web hosting.

---

## Browser support

Tested patterns work in all evergreen browsers (Chrome, Edge, Firefox, Safari) released in the last two years. The site uses:

- CSS custom properties
- CSS Grid and Flexbox
- `backdrop-filter` (with `-webkit-` fallback)
- Variable fonts
- `IntersectionObserver`
- `prefers-reduced-motion` honoured for accessibility

---

## Customizing content

All content lives directly inside the HTML files — no CMS. To update copy:

1. Open the relevant `.html` file.
2. Find the text you want to change.
3. Edit and save.

Common things to update:

| What | Where |
| --- | --- |
| Phone number | Search `+254 113 575 539` across all pages |
| Email address | Search `jiungeupatesacco@gmail.com` across all pages |
| Postal address | Search `P.O. Box 77098` across all pages |
| Loan rates / amounts | `index.html` (preview cards) and `services.html` (full list) |
| Membership fees | `membership.html` — inside the `.fee-breakdown` blocks |

---

## Connecting the contact form

The form on `contact.html` currently shows a client-side success state for demo purposes. To wire it to a real backend, edit the form handler in `js/main.js` (around line 60) — you can:

- POST to a [Formspree](https://formspree.io) endpoint
- POST to a [Netlify Forms](https://docs.netlify.com/forms/setup/) handler (just add `netlify` attribute to the `<form>`)
- POST to your own API
- Send via [Web3Forms](https://web3forms.com) or similar

---

## Credits

- **Design & build:** Custom — refined editorial aesthetic, warm earth tones inspired by the SACCO's brand and Christian-community context.
- **Logo mark:** Original SVG inspired by the brochure (sun, ascending growth arrow, house, cradle).
- **Fonts:** Fraunces & Plus Jakarta Sans (Google Fonts, Open Font License).
- **Icons:** Inline SVGs, original stroke-style.

---

## License

The codebase is provided as a complete deliverable to Jiunge Upate SACCO Society Ltd. Fonts retain their original Open Font License. All written copy, the SVG logo, and design choices are part of this deliverable.
