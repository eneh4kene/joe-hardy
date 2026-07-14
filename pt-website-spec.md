# Joe Hardy Fitness — Website Build Spec
> Hand this file to Claude Code. Build a single-page static site. No frameworks, no CMS, no backend.

---

## Brand

- **Name:** Joe Hardy Fitness
- **Tagline:** Get Fit, Stronger & Motivated!
- **Email:** fitflexcity@gmail.com
- **Phone / WhatsApp:** +44 7432 846353
- **Referral offer:** Refer a friend & get 75% off your next monthly subscription

---

## Palette & typography

| Token | Value |
|---|---|
| `--bg` | `#0A0A0A` |
| `--surface` | `#111111` |
| `--card` | `#181818` |
| `--gold` | `#F5C518` |
| `--gold-dim` | `#C49A10` |
| `--white` | `#FFFFFF` |
| `--muted` | `#999999` |

Display font: **Bebas Neue** (Google Fonts) — section headings, package names, big prices  
Body font: **Inter** (Google Fonts) — all other text  
Both loaded via `<link>` in `<head>`. No other external dependencies.

---

## Layout — single page, six sections, anchor nav

```
[ NAV ]
[ HERO ]
[ ABOUT ]
[ PRICING — two tabs: In Person / Online ]
[ MERCH ]
[ CONTACT + REFERRAL STRIP ]
[ FOOTER ]
```

---

## Section specs

### NAV
- Fixed top, transparent over hero, solid `--bg` on scroll (IntersectionObserver or scroll event)
- Left: "JOE HARDY FITNESS" wordmark in Bebas Neue, `--gold`
- Right links: About · Pricing · Shop · Contact
- Far right: pill CTA button "Book Now" → scrolls to #contact, `--gold` bg, black text
- Mobile: hamburger, slides down nav links, closes on link click
- No JS libraries — pure vanilla

---

### HERO
- Full-viewport-height dark section
- Background: `<!-- REPLACE: add hero image as CSS background-image on .hero --> `  
  Fallback until image is added: deep dark gradient `#0A0A0A → #1a1a00`
- Centred content:
  - Eyebrow chip: "Personal Training · Online & In Person"
  - H1: "JOE HARDY" in Bebas Neue ~96px, `--gold`; "FITNESS" in white same size
  - Subheading: "Get Fit, Stronger & Motivated!" in Inter 22px, `--muted`
  - Two CTA buttons side by side: "View Packages" (gold, anchor #pricing) + "Shop Merch" (outline white, anchor #merch)
- Subtle gold horizontal rule below CTAs

---

### ABOUT
- Two-column on desktop (image left, text right), stacked on mobile
- Image: placeholder `https://placehold.co/500x600/111111/F5C518?text=Joe+Hardy`  
  `<!-- REPLACE: swap src with Joe's photo -->`
- Text:
  - H2: "YOUR COACH"
  - Body: "Joe Hardy is a certified personal trainer dedicated to helping you build muscle, burn fat, and stay motivated — whether you train online or face to face."  
    `<!-- REPLACE: Joe to personalise this bio -->`
- Certification chips (pill style, `--gold` border, dark bg):
  - ✓ Tailored Workout Plans
  - ✓ Nutrition Guidance
  - ✓ Accountability & Motivation
  - `<!-- ADD more certs here -->`

---

### PRICING  `id="pricing"`

Two tab buttons at the top: **"In Person"** | **"Online"**  
Default active tab: In Person. Tab switching is pure JS, no library.  
Active tab button: `--gold` bg, black text. Inactive: outline.

#### TAB 1 — In Person Packages

**1:1 In Person Personal Training**  
Includes: Tailored Workout Plans · Nutrition Guidance · Accountability & Motivation

| Label | Price | Badge |
|---|---|---|
| Per Session | £40 | |
| Monthly | £150/mo | |
| 3 Months | £400 | Most Popular ★ |
| Yearly Package | £1,400 | Best Value |

**Group Sessions**  
| Label | Price |
|---|---|
| Per Session | £10 |
| Monthly | £35/mo |

Callout chip below group table: "+ FREE group session for all registered members"

**Couple Package**
| Label | Price |
|---|---|
| Per Session | £70 |
| Monthly | £25/mo (per person — `<!-- REPLACE: confirm this -->`) |
| 3 Months | £650 |
| Yearly Package | £2,400 |

Each pricing tier is a card (`--card` bg, `--gold` left border, Bebas Neue for price).  
"Most Popular" card gets a `--gold` top border + badge.  
Every card has a "Book Now" CTA button → `mailto:fitflexcity@gmail.com?subject=In%20Person%20Training%20Enquiry`

---

#### TAB 2 — Online Packages

**1:1 Online Personal Training**  
Includes: Tailored Workout Plans · Nutrition Guidance · Accountability & Motivation

| Label | Price | Badge |
|---|---|---|
| Per Session | £25 | |
| Monthly | £90/mo | |
| 3 Months | £250 | Most Popular ★ |
| Yearly Package | £800 | Best Value |

**Online Group Sessions**
| Label | Price |
|---|---|
| Per Session | £10 |
| Monthly | £35/mo |

Callout chip: "+ FREE group session for all registered members"

**Couple Online Package**
| Label | Price |
|---|---|
| Per Session | £40 |
| Monthly | £150/mo |
| 3 Months | £400 |
| Yearly Package | £1,400 |

Same card treatment as In Person tab. CTA mailto subject: `Online%20Training%20Enquiry`

---

### MERCH  `id="merch"`

- Section H2: "GEAR"
- Subheading: "Rep the brand. All items available in multiple sizes."
- Grid: 2 cols mobile, 3 cols tablet, 5 cols desktop
- Each product card:
  - Placeholder image: `https://placehold.co/300x300/181818/F5C518?text=[ProductName]`  
    `<!-- REPLACE: swap with real product photo -->`
  - Product name (Bebas Neue, white)
  - Price: `£--` placeholder `<!-- REPLACE: add price -->`
  - "Order Now" button → `mailto:fitflexcity@gmail.com?subject=Merch%20Enquiry%20–%20[ProductName]`

Products (one card each):
1. T-Shirt
2. Shorts
3. Tracksuit
4. Cap
5. Socks

Below grid, small note in `--muted`: "Message us to check availability and sizes. Orders fulfilled directly."

`<!-- FUTURE: replace mailto buttons with Shopify Buy Button or Stripe Payment Links -->`

---

### CONTACT + REFERRAL  `id="contact"`

Two-column strip on desktop, stacked on mobile.

**Left — Contact**
- H2: "READY TO START?"
- Two buttons:
  - "Email Joe" → `mailto:fitflexcity@gmail.com`
  - "WhatsApp" → `https://wa.me/447432846353`
- Social row (icon + label, link to `#` with replace comment):
  - Instagram `<!-- REPLACE: instagram URL -->`
  - TikTok `<!-- REPLACE: tiktok URL -->`
  - Facebook `<!-- REPLACE: facebook URL -->`

**Right — Referral callout card**
- Gold background card (`--gold` bg, black text)
- Heading: "REFER A FRIEND"
- Body: "Get 75% off your next monthly subscription when you refer a friend who signs up."
- CTA: "Share the link" → `mailto:fitflexcity@gmail.com?subject=Referral`

---

### FOOTER

- Dark `--bg`, centred
- Wordmark: "JOE HARDY FITNESS" in Bebas Neue, `--gold`
- Tagline: "Get Fit, Stronger & Motivated!"
- Repeat nav links inline
- Copyright: `© <span id="year"></span> Joe Hardy Fitness. All rights reserved.`
- JS at bottom: `document.getElementById('year').textContent = new Date().getFullYear();`

---

## Interactions & motion

- Section fade-in on scroll: `IntersectionObserver`, `opacity: 0 → 1`, `transform: translateY(20px) → 0`, 400ms ease
- Respect `@media (prefers-reduced-motion: reduce)` — skip all transitions
- Pricing tab switch: instant show/hide, no animation needed
- Hover on cards: `--gold` border brightens, subtle `translateY(-2px)`, 150ms
- Nav CTA button: gold fill on hover, 150ms

---

## Tech constraints

- Single `index.html` — CSS in `<style>` block in `<head>`, JS in `<script>` before `</body>`
- No npm, no build step, no frameworks
- Google Fonts only external dependency
- All images via `<img>` with meaningful `alt` text
- Fully responsive 375px → 1440px
- Zero console errors on load
- `<!-- REPLACE: ... -->` comments wherever Joe needs to swap in real content

---

## Acceptance criteria

- [ ] Nav becomes solid on scroll past hero
- [ ] "In Person" and "Online" tabs switch correctly, show/hide right cards
- [ ] "Most Popular" badge visible on correct cards in both tabs
- [ ] All 5 merch items render with placeholder image, name, price placeholder, Order button
- [ ] All mailto links correctly formed with pre-filled subjects
- [ ] WhatsApp link opens `wa.me/447432846353`
- [ ] Footer year auto-updates
- [ ] Referral callout visible in contact section
- [ ] Zero broken links (all unknown URLs set to `#`)
- [ ] Renders cleanly on iPhone SE (375px) and 1440px desktop

---

## Checklist of things Joe needs to replace before going live

```
<!-- REPLACE: hero background image -->
<!-- REPLACE: Joe's photo in About section -->
<!-- REPLACE: bio text in About section -->
<!-- REPLACE: add any extra certifications -->
<!-- REPLACE: Instagram URL -->
<!-- REPLACE: TikTok URL -->
<!-- REPLACE: Facebook URL -->
<!-- REPLACE: merch prices -->
<!-- REPLACE: merch product photos -->
<!-- FUTURE: swap mailto merch buttons for Shopify/Stripe -->
<!-- FUTURE: add Calendly embed for bookings -->
```

---

## Deployment — Netlify via MCP

Claude Code must handle the full deployment using the Netlify MCP server. No manual config work.

### Steps Claude Code must execute in order

1. Build all site files locally
2. Use the Netlify MCP to create a new Netlify project named `joe-hardy-fitness`
3. Deploy the site to Netlify
4. Output the live URL when done

### Netlify config file

Create `netlify.toml` in the project root:

```toml
[build]
  publish = "."

[[redirects]]
  from = "/admin"
  to = "/admin/index.html"
  status = 200
```

---

## Admin panel — Decap CMS (formerly Netlify CMS)

Joe needs a `/admin` login on his own site to update prices, packages, and merch without touching code.

Claude Code must generate all of the following. Zero manual config from the developer.

### Files to create

#### `public/admin/index.html`
```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Joe Hardy Fitness — Admin</title>
  </head>
  <body>
    <script src="https://unpkg.com/decap-cms@^3.0.0/dist/decap-cms.js"></script>
  </body>
</html>
```

#### `public/admin/config.yml`

Define the full CMS schema so Joe can edit everything via the UI:

```yaml
backend:
  name: git-gateway
  branch: main

media_folder: "images/uploads"
public_folder: "/images/uploads"

collections:

  - name: "pricing_in_person"
    label: "Pricing — In Person"
    files:
      - label: "1:1 In Person"
        name: "one_to_one"
        file: "_data/pricing_in_person_1to1.json"
        fields:
          - { label: "Per Session", name: "per_session", widget: "string" }
          - { label: "Monthly", name: "monthly", widget: "string" }
          - { label: "3 Months", name: "three_months", widget: "string" }
          - { label: "Yearly Package", name: "yearly", widget: "string" }
      - label: "Group Sessions (In Person)"
        name: "group"
        file: "_data/pricing_in_person_group.json"
        fields:
          - { label: "Per Session", name: "per_session", widget: "string" }
          - { label: "Monthly", name: "monthly", widget: "string" }
      - label: "Couple Package (In Person)"
        name: "couple"
        file: "_data/pricing_in_person_couple.json"
        fields:
          - { label: "Per Session", name: "per_session", widget: "string" }
          - { label: "Monthly", name: "monthly", widget: "string" }
          - { label: "3 Months", name: "three_months", widget: "string" }
          - { label: "Yearly Package", name: "yearly", widget: "string" }

  - name: "pricing_online"
    label: "Pricing — Online"
    files:
      - label: "1:1 Online"
        name: "one_to_one"
        file: "_data/pricing_online_1to1.json"
        fields:
          - { label: "Per Session", name: "per_session", widget: "string" }
          - { label: "Monthly", name: "monthly", widget: "string" }
          - { label: "3 Months", name: "three_months", widget: "string" }
          - { label: "Yearly Package", name: "yearly", widget: "string" }
      - label: "Online Group Sessions"
        name: "group"
        file: "_data/pricing_online_group.json"
        fields:
          - { label: "Per Session", name: "per_session", widget: "string" }
          - { label: "Monthly", name: "monthly", widget: "string" }
      - label: "Couple Online Package"
        name: "couple"
        file: "_data/pricing_online_couple.json"
        fields:
          - { label: "Per Session", name: "per_session", widget: "string" }
          - { label: "Monthly", name: "monthly", widget: "string" }
          - { label: "3 Months", name: "three_months", widget: "string" }
          - { label: "Yearly Package", name: "yearly", widget: "string" }

  - name: "merch"
    label: "Merchandise"
    folder: "_data/merch"
    create: true
    slug: "{{name}}"
    fields:
      - { label: "Product Name", name: "name", widget: "string" }
      - { label: "Price", name: "price", widget: "string", hint: "e.g. £25" }
      - { label: "Product Image", name: "image", widget: "image", required: false }
      - { label: "Available", name: "available", widget: "boolean", default: true }

  - name: "settings"
    label: "Site Settings"
    files:
      - label: "Contact & General"
        name: "contact"
        file: "_data/settings.json"
        fields:
          - { label: "Phone / WhatsApp", name: "phone", widget: "string" }
          - { label: "Email", name: "email", widget: "string" }
          - { label: "Instagram URL", name: "instagram", widget: "string" }
          - { label: "TikTok URL", name: "tiktok", widget: "string" }
          - { label: "Facebook URL", name: "facebook", widget: "string" }
          - { label: "Referral Offer Text", name: "referral", widget: "text" }
```

### `_data/` — seed files

Create all JSON files referenced above pre-filled with Joe's current prices so the site works on first deploy and the CMS shows real data immediately.

Example `_data/pricing_in_person_1to1.json`:
```json
{
  "per_session": "£40",
  "monthly": "£150/mo",
  "three_months": "£400",
  "yearly": "£1,400"
}
```

Repeat for all other `_data/` files using the prices in the Pricing section of this spec.

`_data/settings.json`:
```json
{
  "phone": "+44 7432 846353",
  "email": "fitflexcity@gmail.com",
  "instagram": "#",
  "tiktok": "#",
  "facebook": "#",
  "referral": "Refer a friend & get 75% off your next monthly subscription!"
}
```

### JavaScript — load from `_data/` at runtime

The `index.html` must fetch all `_data/*.json` files on page load using `fetch()` and populate the pricing cards and merch grid dynamically. This means when Joe saves a price change in `/admin`, the live site reflects it on next page load with no code change and no redeploy needed.

```js
// Example pattern — Claude Code to implement fully
async function loadPricing() {
  const res = await fetch('/_data/pricing_in_person_1to1.json');
  const data = await res.json();
  document.getElementById('ip-per-session').textContent = data.per_session;
  // ... etc for all fields
}
```

Use `Promise.all()` to fetch all data files in parallel before rendering.
Show a minimal loading state (skeleton or blank cards) while data fetches.
Handle fetch errors gracefully — fall back to the hardcoded prices in the HTML.

### Enable Netlify Identity + Git Gateway

After deploying, Claude Code must use the Netlify MCP to:
1. Enable Netlify Identity on the site
2. Enable Git Gateway (required for Decap CMS to commit changes)

Then output these exact instructions for Joe (plain English, in the terminal):

```
SETUP COMPLETE — Two things Joe needs to do once:

1. Go to: [your-netlify-url]/admin
2. Click "Sign up" — use your email (fitflexcity@gmail.com)
3. Check your email and confirm
4. You're in. Edit prices, merch, and contact details anytime.

To update a price:
  Admin → Pricing — In Person → 1:1 In Person → change the number → Save
  The website updates immediately.
```

---

## Final file structure

```
joe-hardy-fitness/
├── index.html
├── styles.css
├── netlify.toml
├── public/
│   └── admin/
│       ├── index.html
│       └── config.yml
├── _data/
│   ├── settings.json
│   ├── pricing_in_person_1to1.json
│   ├── pricing_in_person_group.json
│   ├── pricing_in_person_couple.json
│   ├── pricing_online_1to1.json
│   ├── pricing_online_group.json
│   ├── pricing_online_couple.json
│   └── merch/
│       ├── t-shirt.json
│       ├── shorts.json
│       ├── tracksuit.json
│       ├── cap.json
│       └── socks.json
└── images/
    └── uploads/   ← Decap CMS drops merch photos here
```

---

## Updated acceptance criteria

- [ ] `netlify.toml` present and correctly configured
- [ ] `/admin` loads Decap CMS login screen
- [ ] All `_data/` JSON files present and pre-filled with Joe's real prices
- [ ] `index.html` fetches and renders prices from `_data/` on load
- [ ] Merch grid renders from `_data/merch/*.json`
- [ ] Netlify Identity enabled via MCP
- [ ] Git Gateway enabled via MCP
- [ ] Live URL output to terminal on deploy
- [ ] Plain-English setup instructions printed to terminal for Joe
