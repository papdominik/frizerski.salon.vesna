# Frizerski salon Vesna — Salon The Beauty Room

A one-page site for a hair salon in Slavonski Brod, in Croatian.

**This is a single self-contained file.** `index.html` holds the markup, all the
CSS in one `<style>` block, the small amount of behaviour, and the three
photographs embedded directly as base64. No framework, no `package.json`, no
build step, no separate image files. Double-click it and it works, and it can be
sent as one attachment.

## Run it locally

Double-click `index.html`, or serve the folder:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

## Publishing it

Nothing to build, and only one file to upload:

- **Netlify**: drag the folder onto netlify.com/drop
- **Cloudflare Pages**: create a project and upload the folder
- **GitHub Pages**: commit `index.html` and enable Pages
- **Any shared host or cPanel**: copy `index.html` into the public folder

## What is on the page

Seven sections plus the hero: "Mirno mjesto za tvoju kosu" (about), **Tim**,
services, gallery, **Prati nas** (Instagram and Facebook), reviews, contact. The
rating strip shows 4,8 from 318 Google reviews.

Contact details: `+385 35 411 019`, Ul. Nikole Zrinskog 67, Slavonski Brod,
per-day opening hours and a Google Maps embed.

## Social links

Instagram and Facebook appear in four places: the "Prati nas" section, the footer,
the mobile menu, and the `sameAs` field of the structured data, which is what
search engines read.

```
Instagram  https://www.instagram.com/salon_the_beautyroom/
Facebook   https://www.facebook.com/frizerskisalonvesna.gmail/
```

**Confirm both addresses with the salon before this goes live.** They came from
search results, and both platforms refuse automated checks, so I could not verify
them directly. One wrong letter sends customers to a stranger's profile. The
Facebook handle is unusual, ending in `.gmail`, so check that one first.

There is deliberately **no live feed embed**. A real Instagram or Facebook feed
means third-party scripts and cookies, which for an EU business means a consent
banner, plus a plugin that breaks whenever Meta changes something. Links always
work.

## The trade-off of one file

Because the photographs live inside the HTML, the file is about 1.6 MB. That is
fine when it arrives as an email attachment or a single upload, and it is a bit
heavier for a phone on a weak connection than three separate image files would be.
If it ever needs to be lighter, the photos can be moved out into an `images/`
folder and the page drops to about 30 KB.

One real limitation: **`og:image` is now a base64 string, and social networks
cannot read those.** Pasting the link into WhatsApp or Facebook will show the
title and description but no picture. Fixing that requires at least that one file
to be a real image on the server with an absolute URL, for example
`https://salonvesna.hr/images/og.jpg`. Everything else on the page works fine
inline.

## Two things deliberately left open

**The team has no names or photographs.** The `Tim` section
(`<section id="tim">`) describes how the work is done, with a "Naša ekipa" block.
No stylist names and no staff photos were invented, because none could be verified
from public sources. When the salon sends them, add a card per person inside that
section: a portrait at about 4:5, every head at the same height, plus a name and a
one-line speciality.

**Prices are not on the page.** No public price list exists that I could find, so
nothing was guessed. When they supply one, add a price table inside the services
section or as its own section, grouped the way they quote it: šišanje, bojanje,
balayage, svečane frizure.

## Before this goes live

1. **Confirm the facts**: phone number, address, and the per-day opening hours,
   line by line.
2. **Confirm the photographs are theirs to use.** Both current photos came from
   their Google listing, which means compressed files and unclear licensing for a
   website. Ask for the originals; the hero is the one place where a soft photo
   shows.
3. **Check the guest quotes** in the reviews section. If any were written for the
   page rather than copied from real reviews, replace them or drop them.
4. **Add `noindex`** if the demo stays publicly reachable before the salon signs
   off, so a half-finished page does not compete with their Google listing.

## Editing it

Everything is in `index.html`.

- **Text**: search for the Croatian sentence. Plain markup, no templating.
- **Colours and type**: the `<style>` block at the top. Headings are Bricolage
  Grotesque, body text is Manrope, both from Google Fonts.
- **Photos**: they are embedded, so replacing one means swapping a long base64
  string. The practical route is to export the image to a file, reference it as
  `images/name.jpg`, and use the split version. Ask me and I will do it.
- **Map**: the `<iframe>` pointing at `maps.google.com`.
