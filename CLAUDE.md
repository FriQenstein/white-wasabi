# White-Wasabi Sushi Restaurant Web Page Project

A website for a sushi restaurant (owned by a friend of the user) that is opening soon.

## Hosting

- Hosted locally on this laptop using **apache2** (installed and configured).
- Site files live in `public/` — this is the Apache **DocumentRoot**. Anything outside `public/` (CLAUDE.md, `.claude/`, etc.) is not web-accessible.
- Local dev URL: **http://white-wasabi.local** (mapped to 127.0.0.1 in `/etc/hosts`).
- VirtualHost config: `/etc/apache2/sites-available/white-wasabi.conf`.
- `www-data` was added to the `steve` group so Apache can traverse into the home directory to reach the project (home dir is `750`).
- After editing the Apache config: `sudo systemctl reload apache2`.

## Design Direction

- Base the initial layout on a popular, visually appealing restaurant site pattern rather than designing from scratch.
- Keep the layout simple and uncluttered — the priority is making the menu easy to browse and information easy to find.
- Building multiple full homepage mockups (`index1.html`, `index2.html`, `index3.html`, ...) based on real restaurant sites, so the owner can pick a direction before we commit to one. Each is a self-contained page (own inline `<style>`, no shared stylesheet yet).
- Owner feedback: she liked **index1's wasabi-green/coral color scheme** specifically (it matches the color of wasabi) — index2 was recolored from its original maroon/gold to the same wasabi-green/coral palette to match.
- Mockups so far:
  - `public/index1.html` — based on **Bondi Sushi**. Bold/casual: wasabi-green + coral palette, Bebas Neue display type, sticky nav, rounded cards, animated hero blobs.
  - `public/index2.html` — based on **Ottavio's**. Elegant/heritage structure (announcement bar, segmented service-path grid for Dine In / Pickup / UberEats / GrubHub, photo gallery strip, itemized menu list, "Our Story" section, newsletter signup), Playfair Display serif headlines, recolored to the wasabi-green/coral palette (was originally maroon/gold).
  - `public/index3.html` — moody/editorial style inspired by upscale omakase sites (Nobu, Sushi Zo). Full-height hero with the circular logo mark blended into a near-black background as a watermark (`background-blend-mode`), nav that solidifies on scroll, sparse large-type editorial menu list, wasabi-green/coral accents kept consistent with the other two.
- Logo assets live in `public/images/`: `logo-mark.jpg` (tight crop of just the circular Hokusai-wave-and-sushi emblem, no text — used as the small nav/footer badge and as the hero watermark in index3) and `logo-full.jpg` (full lockup with the "WHITE WASABI SUSHI" wordmark and tagline, not yet used — candidate for a future About page or bigger hero treatment).
- Logo tagline currently reads "Test the art of sushi" — likely a typo for "Taste"; owner is confirming with the restaurant owner.
- Once a direction is chosen, consolidate into a single real `index.html` (or extract shared CSS) rather than keeping the numbered mockups.

## Core Features / Pages

- **Menu** — the primary focus; must be easy to browse online.
- **Ordering** — eventually support online ordering via:
  - GrubHub
  - UberEats
  - Direct ordering from the restaurant for pickup
- **Dine-in** — the restaurant offers a relaxed dine-in atmosphere; the site should reflect that experience (not just takeout/delivery).
- **Logo** — placeholder for now; a logo will be added later.
- **Info page** — brief description of the restaurant and the owners (to be written later).
- **Location/contact section** — should include:
  - Restaurant address: **6825 S. Fry Road, Katy, TX 77494**
  - Phone number — not yet provided (still a `[Phone Number]` placeholder in mockups)
  - Hours of operation:
    - Mon–Thu: 10am–9pm
    - Fri–Sat: 10am–10pm
    - Sun: 12pm–8pm
  - Small embedded Google Map showing the location — implemented via a no-API-key `google.com/maps?q=...&output=embed` iframe in each mockup; swap for a proper API embed later if needed.

## Status

Apache2 hosting is set up and serving mockups from `public/`. Real address and hours are in place; phone number, logo, real menu content, food/dining-room photography, and owner bio text are still placeholders (marked `[Placeholder]` inline in the HTML) and need to be swapped in once available.
