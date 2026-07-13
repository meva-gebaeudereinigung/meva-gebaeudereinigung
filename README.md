# MEVA Gebäudereinigung & Hausmeisterservice — Website

Single-page, trilingual (🇩🇪 Deutsch / 🇹🇷 Türkçe / 🇬🇧 English) brochure site for
MEVA-Gebäudereinigung & Hausmeisterservice in Münster.

## Files

| File | Purpose |
|------|---------|
| `index.html` | Page structure. Every text node is keyed with `data-i18n` for translation. |
| `styles.css` | All styling. The colour palette lives in `:root` at the top — see below. |
| `script.js` | Language switching, mobile menu, scroll animations, contact-form → email. |
| `assets/logo.svg` | Header/footer logo. **Placeholder** — replace with the real logo (see below). |
| `assets/favicon.svg` | Browser-tab icon. |

## Run it locally

Just open `index.html` in a browser, or serve the folder:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Hosting & deployment

The site is hosted **free on Netlify** (site `meva-gebaeudereinigung`,
`meva-gebaeudereinigung.netlify.app`). Source code lives in the GitHub repo
[`meva-gebaeudereinigung/meva-gebaeudereinigung`](https://github.com/meva-gebaeudereinigung/meva-gebaeudereinigung)
(owned by the `meva-gebaeudereinigung` GitHub org).

- **Live domain:** `mevagebäudereinigung.de` (punycode `xn--mevagebudereinigung-mwb.de`),
  HTTPS via an auto-renewing Let's Encrypt certificate. `www` and `http` redirect to it.
- **To update the live site** (current setup = manual deploy of the web files):
  ```bash
  netlify deploy --prod --dir . --site meva-gebaeudereinigung --no-build
  ```
  (Or, if Git auto-deploy is later connected in the Netlify dashboard, a plain
  `git push` will publish automatically.)

> GitHub Pages was used initially but **abandoned** because it can't issue SSL
> certificates for internationalized (ä / punycode) domains. Pages is now disabled.

### DNS (set once, in GoDaddy)
Apex `@` → one A record: `75.2.60.5` (Netlify). `www` → CNAME
`meva-gebaeudereinigung.netlify.app`. Netlify provisions/renews HTTPS automatically.

## The contact form

The form builds a pre-filled email and opens the visitor's mail app addressed to
`mevagebaeudereinigung@gmail.com` (no server needed). To switch to a service that
delivers submissions without the visitor's mail app (e.g. Formspree), replace the
`mailto:` block near the bottom of `script.js`.

## Logo

`assets/logo.svg` is a faithful SVG recreation of the real MEVA logo (teal water
droplet with ripples + wordmark), rebuilt from the brief PDF. `assets/favicon.svg`
matches it. Brand colors (teal `#15C8C4`, navy `#1A2635`) live in `:root` in `styles.css`.

## Adjusting the colours

Open `styles.css` and edit the variables at the very top (`:root`). Currently a
placeholder blue/teal palette — swap `--brand`, `--brand-2`, `--brand-3` to the
logo's real colours and the whole site updates.

## Editing text

All copy lives in the `I18N` object in `script.js`, grouped by language
(`de`, `tr`, `en`). Edit the value for a key and it updates everywhere that key
is used. The German values in `index.html` are just the initial render — the
`I18N` object is the source of truth once the page loads.

## Contact details on the site

- MEVA-Gebäudereinigung & Hausmeisterservice — Vahit Alacacioglu
- Bremer Straße 55, 48155 Münster
- 0176 47679162
- mevagebaeudereinigung@gmail.com
