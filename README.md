# Stitchmaster ST 450 — Landing Page

Marketing landing page for the **professionally refurbished Heidelberg Stitchmaster ST 450**, sold and serviced by [Allaoui Graphic Machinery](https://allaoui.com).

The page presents the machine as a high-performance, fully refurbished alternative to buying a new saddle stitcher — backed by ex-Heidelberg engineers, original-spec spare parts, and worldwide service.

---

## Stack

A single-page static site — no framework, no build step.

| File             | Purpose                                                 |
| ---------------- | ------------------------------------------------------- |
| `index.html`     | All page content, sections, and inline JS               |
| `stylesheet.css` | Design tokens, type scale, all section styling          |
| `images/`        | Photography, logos, parts grid, refurbishment artwork   |

External dependencies are limited to the Allaoui font (loaded via CDN) and YouTube thumbnails for embedded video previews.

---

## Page sections

1. **Hero** — Headline, sub, CTAs, machine photo (overlaps the next section)
2. **The Opportunity** — Editorial intro: positioning vs. Müller Martini Primera
3. **Quick Stats** — 14,000 cph · up to 24 feeders · 6-month warranty
4. **Why We Recommend It** — Five feature cards with photos
5. **What Refurbished Actually Means** — Workshop process, factory-tour video, team quote
6. **Service & Parts** — Coverage messaging + original-spec parts grid
7. **vs. Competition** — Filterable comparison table (Primera, Bravo Plus, Prinova, iCE Stitchliner, Prima Plus)
8. **Upgrade Path** — From older Stitchmaster generations
9. **References** — Customer site cards
10. **Configure Your ST 450** — 7-step interactive configurator
11. **FAQ**

A floating right-side page nav (visible from desktop down to 1100px) lets users jump between sections; a top scroll-progress bar tracks reading position.

---

## Design system

Defined as CSS custom properties in `:root`:

- **Colors:** navy `#100C34`, blue `#007DFF`, red `#EB0050`, plus a steel/off-white neutral ramp
- **Type scale (3 sizes):** `--fs-body` `1rem` · `--fs-sub` `1.1rem` · `--fs-min` `0.875rem`
- **Headings:** fluid `clamp()` for h1 / h2; fixed for h3 / h4
- **Font:** `Allaoui` (CDN-hosted), system fallback
- **Easing:** `cubic-bezier(.16, 1, .3, 1)` shared by all transitions
- **Shadows:** `--sh-sm`, `--sh-md` reusable elevations

The type scale is enforced project-wide — avoid introducing arbitrary `font-size` values.

---

## Local development

No tooling required. Open the file directly:

```bash
open index.html
```

Or serve the directory with any static server (e.g. for live reload):

```bash
python3 -m http.server 8080
# then visit http://localhost:8080
```

---

## Conventions

- **Images:** real photos use `loading="lazy"` (the hero uses `fetchpriority="high"` instead). Missing photos show an `.img-ph` dashed placeholder; spare-parts cards fall back to an empty state via `onerror`.
- **Interactive elements:** all behavior is in inline `<script>` blocks at the bottom of `index.html` — page nav, configurator, scroll progress, mobile swipe hint.
- **Comparison table:** values are intentionally left empty when unverified rather than guessed — empty cells render a `—` via `:empty::after`.

---

## Deployment

Static hosting — drop `index.html`, `stylesheet.css`, and `images/` onto any CDN or web host. No server-side runtime needed.
