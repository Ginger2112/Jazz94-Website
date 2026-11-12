# CLAUDE.md: Jazz94 store

This repo holds the **signed-off design** for the Jazz94 online store (sunglasses, watches, shoes; fun but premium) and will hold the store's code.
Your job: build the real store so it matches the design exactly.

## Source of truth (read before writing code)
1. `03-design-spec/DESIGN-SPEC.md`: brand rules, every page's sections, components, interactions, motion, accessibility, placeholders.
2. `03-design-spec/tokens.css`: all colours, fonts, sizes, radii, motion. Use these variables; do not hard-code new values.
3. `01-prototype/index.html`: clickable reference of every page at L1, L2 and **L3 (build L3)**. Lift exact CSS values and behaviour from it. It is a reference, not production code: rebuild cleanly.
4. `05-screens/`: full-page screenshots (desktop 1440 px, mobile 390 px). Finished pages must match these.
5. `SKILLS.md`: skills, learning links, suggested build order.

When the spec and prototype disagree, the prototype wins. When something is not covered, ask the project owner rather than inventing.

## Before scaffolding anything
- **Ask which platform to use** if it has not been decided in this repo yet: Shopify custom theme (Online Store 2.0, recommended) or a custom stack (e.g. Next.js + headless commerce). Record the decision in this file under "Decisions".
- Put store code in its own folder (e.g. `theme/` for Shopify or `web/` for Next.js). Leave the design folders `01`–`06` unchanged.

## Non-negotiable design rules
- **Hero images fill the entire hero section edge to edge, including behind the navigation.** Header is transparent over the photo (light logo, white menu) with the hero overlay gradient, and turns **solid** (blush, blurred, dark logo) after ~40 px of scroll. Product, Bag and Checkout have no hero and use the solid header.
- Logo: Maison Monogram (files in `04-assets/logo/`). Colours: Bordeaux `#9E1F45` (primary buttons, links), Champagne `#E9D3A6`, Cellar `#1C0B12`, Blush `#FFFBFA`; Rose `#FF7A9C` only on dark. Fonts: DM Serif Display (headlines), DM Sans (body, menus), JetBrains Mono (prices).
- Two-tone headlines ("Wear the / *groove.*": second line italic, 1.18×, Bordeaux on light or Champagne on images) with the slanted **speed-line** underneath.
- Footer ends with the **giant fading JAZZ94 wordmark**.
- Mobile (below 760 px): hamburger menu sliding in from the left; **cart drawer** slides in from the right on the bag icon and after every Add to bag.
- L3 motion as listed in the spec, all disabled under `prefers-reduced-motion`.

## Content rules
- Products, prices, contact details (`[WhatsApp number]` etc.), shipping and returns policy, countdown, order numbers and coupon `GROOVE10` are **placeholders or drafts** (spec section 8). Keep them clearly marked; never present them as real.
- Photos in `04-assets/photos/` are Unsplash placeholders (see `SOURCES.md`). Never add photos with third-party brand logos.
- Do not invent reviews, ratings, stats or testimonials.

## Quality bar
- Semantic HTML, real buttons and links, labels on inputs, `aria-label` on icon buttons, dialogs that trap and return focus, visible focus, text contrast ≥ 4.5:1, alt text on images, touch targets ≥ 44 px.
- Responsive images (WebP/AVIF), lazy-load below the fold, preload the hero image and fonts.
- After building or changing a page, **check it visually** at 1440 px and 390 px (e.g. Playwright screenshots) against the matching file in `05-screens/`, and fix differences before calling it done.

## Workflow
- One branch per page or feature (e.g. `feat/home-hero`, `feat/cart-drawer`). Small commits with clear messages.
- Open a pull request for every branch, with screenshots, so the project owner can review before merging to `main`.
- Never force-push `main`. Never commit secrets (API keys, store tokens); use environment variables.
- Suggested order: tokens + fonts + logo → header and footer → Home → New In (collection) + product card → Product → cart drawer → Bag → Checkout styling → About, Contact, Returns, Shipping → mobile polish → motion → performance and accessibility pass.

## Decisions
- Platform: _not decided yet: ask the project owner._
- Store / hosting: _not decided yet._
