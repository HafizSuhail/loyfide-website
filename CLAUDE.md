# LOYFIDE website (loyfide.com)

Brand website for LOYFIDE™, a brand of WAFIYA ENTERPRISES (Kurnool, Andhra Pradesh, India).
The site is a brand showroom, NOT a shop. All purchases happen on Amazon.in via "Buy on Amazon" buttons.
Single developer and owner.

## Role
Expert frontend engineer for a static Astro site using semantic HTML, SCSS and minimal vanilla JS.
Frontend only: there is no backend. Implement directly in the project files rather than only describing changes.

## Audience and tone
- The owner is fluent in HTML, SCSS/BEM and frontend work. Skip beginner explanations.
- Astro is new to the owner: explain an Astro-specific concept briefly the FIRST time it appears
  (e.g. components, layouts, content collections, image component, `<script>` handling), then don't repeat it.

## Response format, scoped by task type
- UI/styling work (default): 1–3 lines of explanation max, then make the edit. No summaries after the edit,
  no restating what the code shows.
- Bugs or build/deploy errors (exception): find the root cause, explain why it happened and why the fix works,
  and check for similar issues elsewhere. No filler, but don't compress a real root cause into one line.
- If anything is unclear (spacing, breakpoint behaviour, missing state, copy, brand detail), ask a short
  clarifying question instead of guessing. Never invent product facts or marketing claims; ask.

## Tech stack (do not change without asking)
- Astro, static output only (no SSR, no server code, no database, no API routes)
- Styling: SCSS via the `sass` package (the only styling dependency). No Tailwind, no UI kits, no CSS frameworks.
- JavaScript: minimal vanilla JS in Astro `<script>` tags, only where needed (e.g. mobile menu, gallery).
  No jQuery, no React/Vue/other frameworks.
- Hosting: Cloudflare Pages, auto-deployed from the `main` branch on GitHub. Pushing to `main` = live on loyfide.com.
- No cookies, no tracking pixels, no third-party scripts, no forms (contact is a mailto: link)
- English only

## Git (solo project, main branch only)
- Work directly on `main`. No feature branches unless the owner asks for one.
- Commit in small, logical steps with short, clear messages (e.g. "Add coming-soon hero section").
- NEVER run `git push` without explicit confirmation. Pushing to `main` deploys to the live site.
- Before asking for push approval:
  1. run `npm run build` and confirm it passes with no errors or warnings
  2. ask the owner to check it with `npm run preview`
  3. show a short list of what changed
- If changes are committed but not pushed, remind the owner that they are local only.

## Project structure
- src/layouts/        BaseLayout.astro (html/head/meta/OG, header, footer). Every page uses it.
- src/components/     Reusable UI (Header, Footer, Button, ProductCard, BuyOnAmazonButton, etc.)
- src/pages/          Routes
- src/content/products/  One file per product (see Content structure)
- src/styles/
  - abstracts/_tokens.scss       Brand tokens as CSS custom properties (colours, fonts, spacing, radius, shadows)
  - abstracts/_breakpoints.scss  Breakpoint variables + `mq()` media-query mixin (mobile-first, min-width)
  - abstracts/_mixins.scss       Shared mixins (container, section spacing, focus ring, visually-hidden)
  - base/_reset.scss, base/_base.scss, base/_typography.scss
  - main.scss                    Imports the above; loaded once in BaseLayout
- public/brand/        Logo files and favicon (supplied by the designer; never edited)
- Component-specific styles live in the component's own `<style lang="scss">` block, using shared tokens and mixins.

## Reuse before writing
- Before writing new markup, styles or scripts, check and reuse what already exists in src/layouts/,
  src/components/, src/styles/abstracts/ and src/styles/base/.
- Treat these as live folders; check their current contents rather than relying on this list.
- Only genuinely shared code goes into shared locations; page-specific styles stay with the page/component.

## Mobile standard
- Mobile-first: base styles target phones; enhance upward with the `mq()` mixin.
- Breakpoints only from abstracts/_breakpoints.scss. Never hard-code media-query values in components.
- Test widths: 360, 390, 768, 1024, 1440 px. No horizontal scroll at any width.
- Tap targets at least 44 × 44 px.

## Code style
- BEM-like naming: .block, .block__element, .block--modifier.
- Flexbox and CSS Grid; no floats.
- SCSS nesting 1–3 levels max.
- Colours, fonts, spacing, radius and shadows come from tokens only. No raw HEX or px values for these in components.
- Vanilla JS only, kept small and scoped to its component.
- LF line endings, 2-space indent, final newline (enforce with .editorconfig).
- No external UI libraries unless explicitly requested.

## Workflow
1. Infer structure first: from a design (image, PDF, designer file or written brief), list the sections and
   components before writing code.
2. Implement directly in the correct files.
3. Run it locally and give the preview URL.
4. Ask when anything is ambiguous.

## Brand rules
- Brand name: LOYFIDE (all caps in logo). Use ™ after the brand name/logo, NEVER ®.
- Logo: use only the supplied logo files in /public/brand/. Never redraw, recolour, stretch or recreate the logo.
- Palette (matches the Instagram palette; defined only in abstracts/_tokens.scss):
  Charcoal #1F1E1C, Off-white #EAE3D8, Stone #D3C8B7, Graphite #5E5852 (grey text).
  Product 1 accent, dusty rose: #C9A39E (shapes/lines), #7E544F (text on light).
  Usage: ~70% off-white/stone, ~25% charcoal/graphite, ≤5% accent. Rose never as a full background.
  Never put small graphite text on stone (fails AA contrast).
- Fonts: TO BE CONFIRMED by the designer. Until then use free Google Fonts (one elegant serif for headings,
  one clean sans-serif for body), loaded with font-display: swap. No script/handwritten fonts.
- Look and feel: premium and minimal. Generous white space, large imagery, restrained motion.
- Contact: support@loyfide.com only. No phone numbers.
- Instagram: https://instagram.com/loyfide
- Footer line: "LOYFIDE™ is a brand of WAFIYA ENTERPRISES, Kurnool, Andhra Pradesh, India."
  Second, smaller footer line: "© 2026 WAFIYA ENTERPRISES"
- Full address, where needed (Contact/legal pages only), exactly:
  45/85-A2, Narasimha Reddy Nagar, Revenue Ward No. 45, Kurnool, Andhra Pradesh – 518001

## Product 1
- Name (use exactly): 4-in-1 Microcurrent Facial Toning Device
- Slug: microcurrent-facial-toning-device
- Benefits (use exactly): Firmer-Looking Skin, Even-Looking Skin Tone, Serum Boost, Refreshed-Looking Skin
- Modes: Booster, Air Shot, MC, Derma Shot
- Features: microcurrent, EMS, multi-colour LED, LCD display (mode, intensity, time, battery), voice guidance,
  skin-contact sensor, 2600 mAh battery, USB Type-C charging, stand-up design, 180 × 34 mm, 149 g
- In the box: Device, USB Type-C Charging Cable, User Manual
- Warranty: 6 months
- Amazon link: not live yet. Each product's data file has an `amazonUrl` field; when empty, the button shows
  "Coming soon to Amazon India" and links to Instagram.

## NEVER do these
- Never mention Bluetooth, an app, or app connectivity anywhere (text, alt text, metadata, images).
- No medical or result claims: no "anti-ageing", "removes wrinkles", "lifts", "heals", "treats", "clinically proven",
  "FDA approved", "dermatologist recommended". Use appearance-based wording ("-looking") only.
- No selling price or discounts on the site. Use "See price on Amazon".
- No fake urgency (countdowns, "only X left", strike-through prices).
- No testimonials, ratings, star widgets, or copied Amazon reviews.
- No competitor names or comparisons.
- No CE/RoHS/FCC or other certification logos.
- No Amazon logo images; a plain text "Buy on Amazon" button is fine.
- No stock or AI-generated images unless the owner supplies them with a licence.
- No pop-ups, autoplay video or audio.

## Content structure (for scaling to more products)
- Products live in an Astro content collection: src/content/products/<slug>.md (or .json), with fields:
  name, slug, status ("coming-soon" | "live"), amazonUrl, heroImage, gallery, benefits, modes, specs, inTheBox,
  warrantyMonths, manualPdf, faqs, seoTitle, seoDescription.
- Product pages and the /products grid are generated from this collection. Adding a product = adding one file.

## Planned pages
/ (home), /products, /products/[slug], /about, /support, /warranty, /privacy, /terms, 404.
Phase 1 (now): a single coming-soon page at / only.

## Quality bar
- Lighthouse 90+ on mobile; images in WebP/AVIF via Astro's image component, with width/height set.
- Semantic HTML, alt text on every image, visible focus states, colour contrast AA.
- Meta title/description and Open Graph tags on every page; sitemap.xml and robots.txt.

## Safety
- Do not touch DNS, domains, email records, or Cloudflare/GitHub account settings. The owner does those manually.
- Do not commit secrets or .env files. Ask before installing any npm package other than `sass`.
