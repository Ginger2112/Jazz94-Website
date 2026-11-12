# Skills needed to build the Jazz94 website

This is what the developer needs to turn the design in this repo into a live store.
Check yourself against each list. Anything you are unsure of has a learning link.

---

## 1. Core skills (needed whatever the platform)

| Skill | What it is used for in Jazz94 | Level |
|---|---|---|
| **HTML** (semantic) | Every page; real `<button>`, `<a>`, `<label>` and `<input>` for accessibility | Strong |
| **CSS** | Flexbox, grid, responsive layout (desktop and mobile at the 760 px breakpoint), CSS variables from `03-design-spec/tokens.css`, full-bleed hero overlays | Strong |
| **CSS animation** | L3 motion: headline slide-ins, speed-line, scrolling bands, hover zoom and lift, drawer slides, `prefers-reduced-motion` | Comfortable |
| **JavaScript (ES6+)** | Mobile menu, cart drawer, filters and sort, variant pickers, quantity, header turning solid on scroll, form states | Comfortable |
| **Git and GitHub** | Branches, commits, pull requests and reviews in this repository | Comfortable |
| **Reading a design spec** | Matching `05-screens/` closely: spacing, type sizes, colours, states | Strong |

## 2. Platform skills

Pick one with the project owner first.

### Option A: Shopify custom theme (recommended)
Checkout, payments, UPI, cash on delivery, inventory and security come built in. The work is turning the design into a theme.

| Skill | Used for |
|---|---|
| **Liquid** (Shopify's template language) | Rendering products, collections, cart and pages |
| **Online Store 2.0 sections and blocks** | Each home section (hero, band, categories, drop countdown, lookbook…) becomes an editable section in the Shopify admin |
| **Shopify CLI** | Local preview, theme check, pushing the theme to the store |
| **Cart AJAX API** | The slide-out cart drawer, live bag count, quantity changes without a page reload |
| **Metafields and metaobjects** | Frame/lens, case/strap and size options; engraving; product badges (New drop, Limited) |
| **Store setup and apps** | Indian payment gateway (e.g. Razorpay or PayU with UPI), cash on delivery, shipping and tracking (e.g. Shiprocket or Delhivery), WhatsApp order updates |

### Option B: Custom build (harder; mid-level developer)
| Skill | Used for |
|---|---|
| **React and Next.js** | Pages, components, routing, server rendering |
| **TypeScript** | Safer components and data models |
| **Headless commerce** | Products, cart and checkout from a back end (e.g. Shopify Storefront API, Medusa or Saleor) |
| **Payment integration** | Razorpay (UPI, cards, netbanking) and cash on delivery |
| **Deployment** | Hosting (e.g. Vercel), environment variables, domains, basic security |

## 3. Launch-quality skills (good to have)
| Skill | Why it matters |
|---|---|
| **Performance** | WebP/AVIF images, lazy loading, preloading the hero and fonts, Core Web Vitals |
| **Accessibility** | Keyboard use, visible focus, 4.5:1 text contrast, alt text, dialogs that move focus |
| **SEO basics** | Page titles, meta descriptions, product structured data, clean URLs |
| **Analytics** | Google Analytics 4, Meta Pixel for ads, conversion events (add to bag, checkout, purchase) |
| **Testing** | Real Android and iPhone devices, Chrome, Safari and Firefox |

---

## 4. Official learning links
- HTML, CSS, JavaScript: MDN Web Docs: <https://developer.mozilla.org/>
- CSS layout guides (flexbox, grid): <https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout>
- Git and GitHub: <https://docs.github.com/en/get-started>
- Shopify theme development: <https://shopify.dev/docs/storefronts/themes>
- Liquid reference: <https://shopify.dev/docs/api/liquid>
- Shopify CLI for themes: <https://shopify.dev/docs/storefronts/themes/tools/cli>
- Dawn, Shopify's reference theme (good starting point): <https://github.com/Shopify/dawn>
- Shopify Cart AJAX API: <https://shopify.dev/docs/api/ajax/reference/cart>
- Next.js: <https://nextjs.org/docs>
- Web accessibility (WCAG quick reference): <https://www.w3.org/WAI/WCAG22/quickref/>
- Web performance (Core Web Vitals): <https://web.dev/articles/vitals>

## 5. Suggested first two weeks (Shopify route)
| Days | Focus | Done when |
|---|---|---|
| 1 | Read `README.md` and `03-design-spec/DESIGN-SPEC.md`; click through `01-prototype/` at L3 on desktop and mobile | You can explain every page and interaction |
| 2–3 | Set up a Shopify development store and Shopify CLI; run Dawn locally; learn Liquid basics | A local theme preview runs |
| 4 | Add `tokens.css`, the fonts and the logo; build the header (transparent over hero, solid on scroll) and footer (with the giant JAZZ94 wordmark) | Header and footer match the screenshots |
| 5–6 | Home page sections: full-bleed hero, brand band, categories, new arrivals, Friday drop, lookbook, watch banner, social grid, services, newsletter | Home matches `05-screens/01-home-*` |
| 7–8 | Collection (New In) page with filters and sort; product card component | Matches `02-new-in-*` |
| 9–10 | Product page with variants, gallery and accordion; cart drawer with the Cart AJAX API | Add to bag opens the drawer with live totals |

Then: Bag page, checkout styling, About, Contact, Returns, Shipping, mobile polish, motion, performance and accessibility pass.
Open one pull request per page or feature so it can be reviewed.
