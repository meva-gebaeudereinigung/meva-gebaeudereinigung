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

The site is hosted **free on GitHub Pages** from the repo
[`meva-gebaeudereinigung/meva-gebaeudereinigung`](https://github.com/meva-gebaeudereinigung/meva-gebaeudereinigung)
(owned by the `meva-gebaeudereinigung` GitHub organization; branch `main`, root folder).

- **Live domain:** `mevagebäudereinigung.de` (punycode `xn--mevagebudereinigung-mwb.de`).
  The custom domain is set via the `CNAME` file — **do not delete it**.
- **To update the live site:** edit files, then:
  ```bash
  git add -A && git commit -m "your message" && git push
  ```
  GitHub Pages rebuilds automatically within a minute or two.

### DNS (set once, in GoDaddy)
Apex `@` → four A records: `185.199.108.153`, `.109.153`, `.110.153`, `.111.153`.
`www` → CNAME `meva-gebaeudereinigung.github.io`. After DNS resolves, enable
**Settings → Pages → Enforce HTTPS** in the repo.

## The contact form

The form builds a pre-filled email and opens the visitor's mail app addressed to
`mevagebaeudereinigung@gmail.com` (no server needed). To switch to a service that
delivers submissions without the visitor's mail app (e.g. Formspree), replace the
`mailto:` block near the bottom of `script.js`.

## Replacing the placeholder logo

`assets/logo.svg` is a temporary placeholder. To use the real logo:
1. Export the logo from the brief PDF as **`logo.svg`** (preferred) or `logo.png`.
2. Drop it into the `assets/` folder, overwriting the placeholder.
3. If it's a PNG, change `assets/logo.svg` → `assets/logo.png` in `index.html`
   (two spots: header and footer).

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
