# Jazz94 website: developer handoff

Jazz94 sells **sunglasses, watches and shoes**: fun, but premium.
The design is signed off. Your job is to build the real store from it.

## Start here (15 minutes)
1. Open **`01-prototype/index.html`** in Chrome (double-click it; it needs internet only for Google Fonts).
   Use the top bar to switch **Level** (L1 wireframe, L2 visual, L3 final), **Page** and **Device** (desktop or mobile).
   Click around: everything works, including add to bag, the cart drawer, filters, variants, coupon `GROOVE10`, checkout and forms.
   **Build L3 Final.** L1 and L2 are there to show structure and the visual layer separately.
2. Read **`03-design-spec/DESIGN-SPEC.md`**: brand rules, every page section, components, interactions, motion, and what still needs confirming.
3. Keep **`05-screens/`** open next to your editor as pixel references (full-page, desktop and mobile).
4. Check **`SKILLS.md`**: the skills this build needs, learning links, and a suggested first-two-weeks plan.
5. Building with **Claude Code**? `CLAUDE.md` gives Claude the project brief, rules and workflow automatically when you open this repo.

## What's in the folder
| Folder | Contents |
|---|---|
| `01-prototype/` | Clickable prototype of all 9 pages + cart drawer + mobile menu (single HTML file, vanilla JS) with its images |
| `02-canvas/` | Every screen on one pan-and-zoom board (drag to move, pinch or Ctrl/⌘ + scroll to zoom, buttons to jump between L1, L2 and L3) |
| `03-design-spec/` | `DESIGN-SPEC.md` (read this), `tokens.css` and `tokens.json` (colours, fonts, sizes, radii, motion) |
| `04-assets/logo/` | Logo on light, logo on dark, monogram/app icon (SVG; convert text to outlines for production) |
| `04-assets/photos/` | All 14 photos used, plus `SOURCES.md` with Unsplash links and licence (placeholders, to be replaced by real shoots) |
| `05-screens/` | Full-page screenshots: 01 Home, 02 New In, 03 Product, 04 Bag, 05 Checkout, 06 About, 07 Contact, 08 Returns, 09 Shipping, 10 Cart drawer, 11 Mobile menu |
| `06-reference/` | Background only: final brand board (logo, colours, type), logo explorations, and the three home directions that were compared |

## Pages to build
Home · New In / category (Sunglasses, Watches, Shoes) · Product · Bag · Checkout + order confirmation · About · Contact · Returns · Shipping · Cart drawer · Mobile menu.

## Non-negotiables from the client
- **Hero images fill the whole hero section edge to edge, including behind the navigation.** The header is transparent over the photo and turns solid on scroll.
- Brand: Maison Monogram logo, Bordeaux `#9E1F45` + Champagne `#E9D3A6`, DM Serif Display + DM Sans (prices in JetBrains Mono).
- The two-tone headline ("Wear the / *groove.*") and the slanted speed-line under hero headlines.
- Giant fading **JAZZ94** wordmark at the bottom of the footer.
- Mobile: hamburger menu that slides in from the left; the cart drawer slides in from the right after every Add to bag.

## Before you start coding, confirm with the project owner
1. **Platform:** Shopify custom theme or a custom stack (for example Next.js with headless commerce)?
2. **Repository and hosting:** which GitHub repo, which Shopify store or hosting account?
3. **Real content:** products and prices, contact details, final shipping and returns policy, real photography. Everything listed in section 8 of the spec is placeholder.

## Notes
- The prototype code is a reference for values and behaviour, not production code. Rebuild it cleanly with reusable components.
- Fonts: Google Fonts, SIL Open Font License. Photos: Unsplash License (see `04-assets/photos/SOURCES.md`).
- Questions about design intent go to the project owner. When in doubt, match the prototype.
