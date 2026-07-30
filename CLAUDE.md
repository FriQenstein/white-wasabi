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
  - `public/index4.html` — **owner's current favorite; treat as the "main" page for now.** Duplicate of index3's moody/editorial layout, recolored to the 3 brand colors picked from the logo art (navy `#031D36` background, orange `#D0631E` primary accent, teal `#6A99A3` secondary/label accent — navy is used only as a background, never as text on a dark surface, per owner's contrast concern). Also has a horizontally-scrollable "From the Chef" photo gallery (between "Our Approach" and "The Menu") currently filled with temporary CC-licensed stock photos from Wikimedia Commons (credited on-page; swap for real chef photos when available and remove the credit line + attribution comment above the gallery markup). Hours on this page only are 11am opening Mon–Sat (see note below) — an intentional one-off, not yet synced to the other mockups.
- Logo assets live in `public/images/`: `logo-mark.jpg` (tight crop of just the circular Hokusai-wave-and-sushi emblem, no text — used as the small nav/footer badge and as the hero watermark in index3/index4) and `logo-full.jpg` (full lockup with the "WHITE WASABI SUSHI" wordmark and tagline, not yet used — candidate for a future About page or bigger hero treatment).
- Logo tagline currently reads "Test the art of sushi" — likely a typo for "Taste"; owner is confirming with the restaurant owner. Confirmed as a typo (should be "Taste") — but it's baked into the image pixels of `logo-full.jpg`, so it needs a corrected export from whoever made the logo, not a text edit. Page copy that spells out the tagline (e.g. index3's hero) already uses the correct "Taste" spelling.
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
  - Hours of operation (index1–3; index4 intentionally shows 11am opening Mon–Sat instead, see Design Direction note above):
    - Mon–Thu: 10am–9pm
    - Fri–Sat: 10am–10pm
    - Sun: 12pm–8pm
  - Small embedded Google Map showing the location — implemented via a no-API-key `google.com/maps?q=...&output=embed` iframe in each mockup; swap for a proper API embed later if needed.

## Status

Apache2 hosting is set up and serving mockups from `public/`, which is also pushed to a public GitHub repo (`FriQenstein/white-wasabi`) with GitHub Pages auto-deploying `public/` on every push to `main` (via `.github/workflows/pages.yml`, since Pages branch-deploy doesn't support arbitrary subfolders) — live at `https://friqenstein.github.io/white-wasabi/`, used to share mockups with the owner. **index4 is the current front-runner** and is where new refinement requests are landing; index1–3 are effectively frozen unless she asks to revisit them. Real address and hours are in place (index4 has an intentional hours variation, see above); phone number, logo tagline fix, real menu content, food/dining-room photography, and owner bio text are still placeholders/pending and need to be swapped in once available.
