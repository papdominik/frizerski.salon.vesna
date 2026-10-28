# Frizerski salon Vesna — Salon The Beauty Room

A one-page site for a hair salon in Slavonski Brod, in Croatian.

**This is a single self-contained file.** `index.html` carries the markup, all the
CSS in one `<style>` block, the small amount of behaviour, and the photographs
embedded directly as base64. No framework, no `package.json`, no build step.
Double-click it and it works.

## Run it locally

Double-click `index.html`, or serve the folder:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

## Publishing it

Nothing to build. Upload the file to any host:

- **Netlify**: drag the folder onto netlify.com/drop
- **Cloudflare Pages**: create a project and upload the folder
- **GitHub Pages**: push it to a repo and enable Pages
- **Any shared host or cPanel**: copy `index.html` into the public folder

Then point the salon's domain at the host. Certificates are automatic above.

## What is on the page

- Hero: "Kosa koja se pamti."
- "Mirno mjesto za tvoju kosu"
- "Od šišanja do svečane frizure"
- "Rad iz salona"
- "Gosti o nama"
- "Dođi po svoj termin" — address, per-day opening hours, phone, map

Contact details in the page: `+385 35 411 019`, Ul. Nikole Zrinskog 67, Slavonski
Brod, plus a Google Maps embed and a map link.

Type is Bricolage Grotesque for headings and Manrope for body text, both loaded
from Google Fonts.

## Why the file is 2.1 MB

Three photographs are embedded in the page as base64, which is what makes one
file carry the whole site. Convenient, but heavy.

To slim it down: put the photos in an `images/` folder, then in `index.html`
replace each `src="data:image/jpeg;base64,..."` value with `images/name.jpg`. The
file drops to about 25 KB and the browser loads photos separately, which is better
for repeat visits and for search engines. I can do this split if you want it.

## Editing it

Everything is in `index.html`.

- **Text**: search for the Croatian sentence and change it. Plain markup, no
  templating.
- **Colours and type**: the `<style>` block at the top.
- **Map**: the `<iframe>` pointing at `maps.google.com`. Change the query to move
  the pin.

## Before this goes live for the salon

1. **Fix the social image.** `og:image` is currently a base64 data URI, and social
   networks cannot read those, so a shared link shows no preview picture. Move
   that photo to a real file and set `og:image` to an absolute URL once the domain
   exists. Add `og:url` at the same time.
2. **Confirm the facts**: phone number, address, and the per-day opening hours.
   The hours table is in the page and should be checked line by line, since a
   wrong closing time is worse than no hours at all.
3. **Confirm the photographs are theirs to use.** The hero image appears to come
   from their Google listing, which is compressed and may not be licensed for
   general use. Ask them for the originals from a phone or camera; a soft photo in
   the hero is the one thing the design cannot fix.
4. **Check the guest quotes** in "Gosti o nama". If they were written for the
   page rather than taken from real reviews, replace them with real ones or drop
   the section.

## A note on the deployment

This file was built in a local workspace and is **not published on any host**:
there is no live address for it, unlike the gym and plumbing sites. This zip is
the only copy of the site, so keep it safe and host it somewhere you control.

There is also a Python generator in the original workspace that rebuilds this page
from source photographs in a local `img` folder. Ask me if you want it included
with the paths made portable.
