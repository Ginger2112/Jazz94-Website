# Jazz94 website: design spec for development

**Brand:** Jazz94 sells sunglasses, watches and shoes. Fun but premium.
**Direction:** Bordeaux + energy, with Bordeaux Champagne colours, Editorial Luxe type and the Maison Monogram logo.
**Status:** design signed off. Build from this spec, the prototype (`01-prototype`) and the screenshots (`05-screens`).

> The prototype is a **design reference**, not production code. It is one HTML file with vanilla JS so every screen and interaction can be clicked through. Rebuild it properly in the chosen stack, and lift exact CSS values from it whenever this spec is unclear.

---

## 1. Brand basics

### Logo: Maison Monogram
- A Champagne rounded tile (radius 26 on a 100 px tile) with a thin rose inner border. A big **J** in DM Serif Display (Cellar) and a small **94** top-right in Bordeaux.
- Wordmark **JAZZ94** in DM Sans 500, letter-spacing 9/40 (≈ .22em), with the tagline **SHADES · WATCHES · KICKS** underneath (DM Sans 500, 10 px, wide spacing).
- Files are in `04-assets/logo/`: `jazz94-logo-on-light.svg`, `jazz94-logo-on-dark.svg`, `jazz94-monogram.svg` (app icon and favicon).
- The SVGs use live text. **Convert the text to outlines** (Illustrator or Figma) before using them as production logo files, so they render the same everywhere.
- Light backgrounds take the dark wordmark; images and dark bands take the light wordmark (blush wordmark, Champagne tagline). The tile stays Champagne in both.

### Colour (see `tokens.css`)
| Token | Hex | Use |
|---|---|---|
| Bordeaux | `#9E1F45` | Buy buttons, links, sale, active states, prices in highlights |
| Champagne | `#E9D3A6` | Monogram tile, accent words on dark ("*groove.*"), buttons on dark |
| Champagne light | `#F6EDDC` | Soft panels: lookbook, delivery bar, value cards |
| Rose | `#FF7A9C` | Small accents **on dark only**: live dots, band stars, "Sale" over images |
| Cellar | `#1C0B12` | Text, footer, dark bands, countdown |
| Blush | `#FFFBFA` | Page background |

Rules:
- Never put Rose or Champagne text on a light background (too low contrast).
- White text on Bordeaux is about 7.5:1. Muted `#6B5560` on Blush passes AA.
- Bordeaux is the **only** colour for primary buttons on light pages. On images and dark bands, primary stays Bordeaux and secondary is a white outline.

### Type
| Role | Font | Size | Notes |
|---|---|---|---|
| Hero headline | DM Serif Display | clamp(72px, 9.4cqi, 146px), 68 px mobile | line-height .88, letter-spacing -.035em; second line italic at 1.18× |
| Page hero | DM Serif Display | clamp(60px, 7cqi, 112px), 58 px mobile | Same two-tone pattern |
| Section heading | DM Serif Display | clamp(34px, 4cqi, 56px) | One word or phrase in *italic Bordeaux* |
| Product name | DM Serif Display | 20 px (cards), 40–60 px (product page) | |
| Body | DM Sans | 16 px / 1.55 | Lead paragraph 19 px (16 px mobile) |
| Kicker / label | DM Sans 500–700 | 13 px, uppercase, .24em | Bordeaux on light, Champagne on dark |
| Nav | DM Sans 500 | 13 px, uppercase, .14em | |
| Prices, counts, order numbers | JetBrains Mono | 13–24 px | `font-variant-numeric: tabular-nums` |

All three fonts are free on Google Fonts (SIL Open Font License).

### The two-tone headline (signature pattern)
First line in Cellar on light pages, or Blush on images. Second line in **italic**, 1.18× bigger, in Bordeaux on light pages or Champagne on images.
Examples: "Wear the / *groove.*", "New / *in.*", "Shades / *on.*", "Keep / *time.*", "Kicks that / *move.*", "Your *bag.*", "Talk to / *us.*", "Changed your / *mind?*", "Delivered / *with care.*", "You're in the / *groove.*".

### Speed-line (signature detail)
A 300 × 5 px bar skewed −24°, placed under each hero headline. It has three segments: ink (64%), Bordeaux (68–88%) and Champagne (91–100%). On images the ink segment becomes Blush and the Bordeaux segment becomes Rose. Smaller version (200 × 4 px) on the product page.

---

## 2. Layout and responsive
- Container max 1320 px, side gutter 20 px. Sections are separated by 96 px (64 px on mobile).
- One breakpoint at **760 px**. The prototype uses container queries; media queries are fine in production.
- Grids: products 4 per row on desktop, 2 on mobile; category tiles 3, then 1; New In grid 3 next to a filter panel, then 2.
- Radii: pills 999 px; cards 22 px; tiles 28 px; big panels 36 px; arch photos `999px 999px 32px 32px`; inputs 12 px.

### Hero rule (client requirement)
**Every hero image fills its whole section edge to edge, including behind the navigation.** The header floats transparently on top of the photo, with a light logo and white menu text. A dark gradient (`--j94-hero-overlay`) keeps text readable. When the page scrolls past about 40 px, the header turns **solid** (Blush at 94% opacity with blur, dark logo and text).
- Home hero: min-height 900 px desktop and 760 px mobile. Other pages use a short hero (620 / 560 px).
- On mobile the overlay runs bottom-up and the text sits at the bottom of the photo.
- The product, bag and checkout pages have no hero image. They use the solid header.

---

## 3. Global components
| Component | Spec |
|---|---|
| Announcement ticker | Cellar band, Champagne 12 px uppercase text, rose ✦ separators; scrolls continuously (32 s loop) |
| Header | Two tiers: Search (left), centred logo (186 px wide), Account / Wishlist / Bag with count badge (right); menu row underneath. Mobile: hamburger, search icon, logo, bag |
| Mobile menu | Slides in from the left (86% width, max 340 px). Big serif category links with hints, utility links (sign in, wishlist, track order, help, about, contact) and a "Join the Club" card. Closes on tap outside, the close icon or Escape |
| Cart drawer | Slides in from the right (440 px, full width on mobile). Opens when the bag icon is tapped and **after every Add to bag**. Contains: free-delivery progress, items with quantity and remove, one "Pairs well with" suggestion, subtotal, **Checkout** and **View bag** |
| Brand band | Bordeaux band with large italic Champagne serif text (40 px, 28 px mobile) and rose ✦, scrolling slowly. Used under heroes |
| Product card | 4:5 image, radius 22, badge top-left (New drop / Bestseller / Limited), heart top-right, category label, serif name, colour dots, mono price, "Add +" button. Hover: card lifts 6 px, image zooms 1.07 |
| Buttons | Pill, 15 px bold. Primary Bordeaux; secondary 1.5 px ink outline; on dark: Champagne fill or white outline. Hover: lift 2 px, Bordeaux shadow, light shine sweep |
| Live label | 9 px pulsing dot (Bordeaux, or Rose on images) and a kicker, e.g. "Drop 07 · The Summer '94 Edit" |
| Footer | Cellar; brand column, Shop / Help / About / The Club links; bottom row with © and payment marks; then a **giant JAZZ94 wordmark** (DM Sans 500, 21.5% of the width, "JAZZ" Champagne and "94" rose, fading into the background, slightly cropped at the bottom) |

---

## 4. Pages (section order)
Screens are in `05-screens`, numbered as below. L1 wireframe notes are inside the prototype (Level → L1 Wireframe).

1. **Home:** ticker · header over the hero · full-bleed hero (live label, "Wear the *groove.*", speed-line, Shop the drop and Explore watches, trust line, 01/02/03 slide counter, rotating "New drop every Friday" badge, floating product tag) · brand band · Shop by category (3 tiles) · New this Friday (tabs: All, Sunglasses, Watches, Shoes) · Friday drop countdown (days, hours, minutes; Notify me) · Lookbook "Dressed for the *late set.*" with 3 linked products · Watch banner "Time keeps *the beat.*" · #WearTheGroove social grid (5) · service promises (4) · Join the Club newsletter · footer.
2. **New In / Category:** full-bleed hero (photo and headline change per category; breadcrumb on the image; live item count) · band · category chips with counts and Sort · filter panel (price, colour, shoe size; a Filters button on mobile) · grid with 2 editorial tiles · end-of-list message.
3. **Product:** breadcrumb · square gallery with 4 thumbnails (packshot + 3 lifestyle) · live label, name, speed-line, price "Inclusive of all taxes", description · variants by category (sunglasses: frame + lens; watches: case + strap; shoes: colour + UK size) · quantity, **Add to bag · price**, wishlist (sticky at the bottom on mobile) · pincode check · accordion (Details, Size and fit, Care, Shipping and returns) · band · Complete the look (4) · Reviews (empty state for launch).
4. **Bag:** "Your *bag.*" with "Reserved for 30 minutes" · free-delivery progress (₹999 threshold) · line items (quantity, Move to wishlist, Remove) · summary (subtotal, delivery, coupon, gift wrap ₹99, total, Checkout securely) · You may also like.
5. **Checkout:** minimal header (logo + "Secure checkout") · steps (Address, Delivery, Payment) · address form with pincode autofill note and WhatsApp updates opt-in · delivery speed cards (Standard free / Express ₹149) · payment (UPI first and marked fastest, then card, netbanking, cash on delivery; a UPI ID field appears for UPI) · **Place order · total** · order summary (moves above the form on mobile). **Confirmation:** full-bleed photo with the nav over it, check mark, order number, "You're in the *groove.*".
6. **About:** hero "Made for the *late set.*" · band · "Why we started" arch photo and story · 3 values · 3 category tiles · manifesto block with 2 CTAs.
7. **Contact:** hero "Talk to *us.*" · band · 4 contact cards (WhatsApp, email, phone, studio) · contact form (name, email or phone, order number, topic, message) with a thank-you state · Quick answers FAQ.
8. **Returns:** hero "Changed your *mind?*" · band · 4-step process · Start a return (order number + phone → choose items and reason → schedule pickup → confirmation) · policy accordion.
9. **Shipping:** hero "Delivered *with care.*" · band · 3 delivery options · delivery-times table by region · pincode checker · order tracking with a status timeline · keepsake-box packaging story.
10. **Cart drawer** and 11. **Mobile menu:** see Global components.

---

## 5. Interactions to build
- Add to bag (cards, product page, drawer suggestion) updates the bag count and opens the cart drawer.
- Wishlist hearts toggle with a pop animation.
- Home tabs and category chips filter the products; Sort reorders them (featured, price low to high, price high to low).
- Product page: thumbnails swap the main image; variant pickers and quantity update the Add to bag price; pincode check validates 6 digits and shows a delivery estimate.
- Bag: quantity, remove and move to wishlist update totals live. Free delivery at ₹999 or more, otherwise ₹79. Coupon `GROOVE10` = 10% off (demo code). Gift wrap adds ₹99.
- Checkout: delivery and payment selection updates the total; Place order shows the confirmation.
- Contact form, return request, pincode and tracking show their success states (the prototype simulates them; connect them to real services).
- Header turns solid on scroll; Escape closes the menu and drawer.

## 6. Motion (L3)
Ease `cubic-bezier(.2,.7,.2,1)` everywhere.
| What | How |
|---|---|
| Hero headline | Each line slides in from −70 px with a slight skew, 0.9 s; the second line is 0.16 s later |
| Speed-line | Draws from the left (scaleX 0 → 1), 1 s, 0.4 s delay |
| Hero photo | Slow zoom out, 1.14 → 1, 1.8 s |
| Text and blocks on load | Fade up 28 px, 0.9 s, staggered 0.12 s |
| Live dot | Pulse ring, 1.6 s loop |
| Ticker and brand band | Continuous scroll, 32 s and 40 s loops |
| Rotating badge | 18 s per turn; floating product tag bobs 10 px over 4.5 s |
| Hover | Images zoom 1.07 (0.8 s); cards lift 6 px; buttons lift 2 px with a shine sweep; menu links underline from the left |
| Drawers, toasts | Slide in 0.45 s |
| Footer wordmark | Rises in, 1.4 s |
Respect `prefers-reduced-motion`: turn all of these off.

## 7. Accessibility
- Real `<button>`, `<a>`, `<label>` and `<input>` elements; icon buttons have `aria-label`; drawers are `role="dialog"` with focus moved inside and returned on close.
- Visible focus ring on every control. Touch targets at least 44 px.
- Alt text on every product and lifestyle image.
- Keep text contrast at 4.5:1 or above; check new combinations against the colour rules above.

---

## 8. Sample content and items to confirm before launch
These are **placeholders or proposals** in the design. Do not ship them as real.
- **Products and prices** (sample catalogue):

| Product | Category | Price (₹) |
|---|---|---|
| Bebop Round Sunglasses | Sunglasses | 2,499 |
| Riviera Tortoise Sunglasses | Sunglasses | 2,899 |
| Midnight Set Watch | Watches | 6,999 |
| Rose Rhapsody Chrono | Watches | 5,499 |
| Minimal Swing Watch | Watches | 3,999 |
| Night Shift Steel | Watches | 7,499 |
| Bordeaux Skate Sneakers | Shoes | 3,299 |
| Ballad Monk Straps | Shoes | 6,499 |
| Peach Bossa Brogues | Shoes | 5,999 |
| Floral Scat Heels | Shoes | 4,299 |

- **Contact details:** `[WhatsApp number]`, `[support email]`, `[phone number]`, `[studio address]`.
- **Policies (draft, client to approve):** free delivery over ₹999 (₹79 below); Express ₹149, 1–2 days in metros; delivery times by region; same-day dispatch before 2 pm; cash on delivery with no fee; 15-day returns with free pickup; refund timings (UPI and card 5–7 working days, COD 7 working days, store credit instantly); free size swap once per order; damaged items reported within 48 hours; exclusions (engraved watches, worn shoes, sunglasses with lens film removed); free engraving up to 12 characters.
- **Demo-only values:** Friday drop countdown, order number J94-10482, the tracking timeline, coupon GROOVE10, "Up to 30% off" sale hint.
- **Photography:** Unsplash placeholders (`04-assets/photos/SOURCES.md`). Replace with real Jazz94 shoots.

## 9. Build recommendation
- **Platform:** decide between **Shopify** (fastest: payments, UPI, COD, inventory and India shipping apps built in; build a custom Online Store 2.0 theme where each section here becomes a theme section) and a **custom stack** (for example Next.js with a headless commerce back end). Confirm with the project owner before starting.
- Use `tokens.css` as the single source of truth for colours, type, radii and motion.
- Serve images as responsive WebP or AVIF with lazy loading below the fold. Preload the hero image and the three fonts.
- Use the Git workflow: one branch per page or feature, pull requests for review.
