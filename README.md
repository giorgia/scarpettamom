# scarpettamom

Link-in-bio page for [@scarpettamom](https://instagram.com/scarpettamom) — Italian comfort food, mom + toddler.

**Live:** https://giorgia.github.io/scarpettamom/

## How it works

Single self-contained `index.html` — the logo is inlined as base64, so there are no
local asset dependencies. Only external requests are Google Fonts (Fredoka, Nunito).

Links are stored in the browser under `localStorage` key `scarpettamom_links_v1`.

Edit mode is hidden unless the URL carries `?edit=8941`:

    https://giorgia.github.io/scarpettamom/?edit=8941

That flag keeps the button away from visitors arriving from the bio link. It is
**not** a security control — the page is static and the value is visible to anyone
who views source. It doesn't need to be: editing only writes to the visitor's own
browser, so nobody can change what others see.

### Product images

Each item takes an optional `img` — paste an image URL in the Add/Edit form, or set
it in `DEFAULTS`:

    {id:'k5', title:'Instant Pot Duo 7-in-1', url:'https://www.amazon.com/dp/B0F9BD5M2K',
     img:'https://instantpot.com/cdn/shop/files/140-8004-01Silo.png'},

Leave it out and the card shows the little plate, exactly as before. Only `http`/`https`
URLs are accepted; anything else is dropped. If an image 404s or is blocked it is
removed at runtime and the plate shows through, so a bad URL never leaves an empty box.

Note that images are **not** fetched from the Amazon link — Amazon's product images
require their Product Advertising API (signed requests, impossible on a static site)
or a SiteStripe image link. Hotlinking a manufacturer's CDN works but breaks whenever
they change the URL; committing the file to this repo is more durable.

**Edits are local to your browser.** To change what visitors see you must edit the
`DEFAULTS` object in `index.html` and push. Handy workflow: open with `?edit=8941`,
build the list, hit **Copy JSON** (its shape matches `DEFAULTS` exactly), paste it
over the object, commit.

Note that once you've used edit mode, your own browser prefers its saved copy over
`DEFAULTS` — hit **Reset to defaults**, or use a private window, to see what
visitors actually get.

## Amazon Associates

`affiliateUrl()` appends `?tag=scarpettamom2-20` to every product link.
The disclosure in the footer is required by the Associates programme and must stay:

> As an Amazon Associate I earn from qualifying purchases.

## Files

- `index.html` — the whole site
- `logo.jpg` — source logo (already inlined into `index.html`; kept as the original)
- `.nojekyll` — serve the file as-is, skip Jekyll processing
