# scarpettamom

Link-in-bio page for [@scarpettamom](https://instagram.com/scarpettamom) — Italian comfort food, mom + toddler.

**Live:** https://giorgia.github.io/scarpettamom/

## How it works

Single self-contained `index.html` — the logo is inlined as base64, so there are no
local asset dependencies. Only external requests are Google Fonts (Fredoka, Nunito).

Links are stored in the browser under `localStorage` key `scarpettamom_links_v1`.
Tap **Edit ✎** on the page to add, edit or remove them; **Copy JSON** exports the
current set. Because it's localStorage, edits live in your browser — to change the
defaults for every visitor, edit the `DEFAULTS` object in `index.html`.

## Amazon Associates

`affiliateUrl()` appends `?tag=scarpettamom2-20` to every product link.
The disclosure in the footer is required by the Associates programme and must stay:

> As an Amazon Associate I earn from qualifying purchases.

## Files

- `index.html` — the whole site
- `logo.jpg` — source logo (already inlined into `index.html`; kept as the original)
- `.nojekyll` — serve the file as-is, skip Jekyll processing
