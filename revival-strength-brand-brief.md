# Revival Strength — Brand & Website Brief
> For handoff to Claude Code or any developer. This document covers brand identity, site architecture, design system, copy direction, offerings, and ideal customer profile.

---

## 1. Executive Summary

**Revival Strength** is a peak performance coaching brand founded by **Josh Lee**, a Denver-based coach with 7+ years of experience. The brand exists to help driven individuals master the four pillars of peak performance — movement, nutrition, sleep, and community — through habit-based systems that compound over time.

Josh's philosophy is rooted in **functional strength for life**: building bodies and minds that perform under the real demands of everyday living. His approach is not about quick fixes or extreme programs — it's about small, consistent actions that create extraordinary long-term results.

The website serves two primary functions:
1. **Attract and convert** ideal coaching clients through a high-trust, premium landing experience
2. **Capture leads** via a free PDF offer (The Peak Performance Blueprint) and nurture them toward applying for coaching

---

## 2. Brand Identity

### Brand Name
**Revival Strength**

### Coach
**Josh Lee** — Peak Performance Coach, Revival Strength

### Tagline / Hero Headline
> MASTER *Yourself.*

### Brand Voice
- Confident, direct, and motivating — never arrogant
- Warm and human — Josh leads with humility and connection
- Educational — positions Josh as a coach AND an educator
- Action-oriented — every section pushes toward a next step
- Avoids: hype language, bro-culture fitness tropes, vague promises

### Brand Values
- Real food. Real results.
- Consistency over intensity
- Community over competition
- Function over aesthetics
- Long game over shortcuts

---

## 3. Design System

### Color Palette
| Name | Hex | Usage |
|------|-----|-------|
| Gold (Primary Accent) | `#C8853A` | CTAs, highlights, logo, borders, icons |
| Gold Light | `#E8A055` | Hover states, gradients |
| Darker (Page BG) | `#091520` | Primary background |
| Dark | `#0D1F2D` | Section backgrounds, cards |
| Mid | `#1A3345` | Card backgrounds, feature sections |
| White (Cream) | `#F5F0E8` | Body text, headlines |
| Muted | `#8FA5B4` | Subtext, descriptions, placeholders |

### Typography
| Role | Font | Weight |
|------|------|--------|
| Display / Headlines | Bebas Neue | Regular (400) |
| Italic / Accent | DM Serif Display | Italic |
| Body / UI | DM Sans | 300, 400, 500, 600 |

**Google Fonts import:**
```
https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Serif+Display:ital@0;1&family=DM+Sans:wght@300;400;500;600&display=swap
```

### Logo
- SVG inline barbell mark with M/V chevron shape
- Text: "REVIVAL STRENGTH" in Bebas Neue, letter-spacing: 5
- Color: `#C8853A` (gold only — transparent background)
- Used in: nav bar, footer (slightly reduced opacity in footer)

```svg
<svg viewBox="0 0 240 90" fill="none" xmlns="http://www.w3.org/2000/svg">
  <circle cx="18" cy="45" r="16" fill="none" stroke="#C8853A" stroke-width="7"/>
  <rect x="34" y="38" width="8" height="14" rx="2" fill="#C8853A"/>
  <rect x="42" y="42" width="32" height="6" rx="2" fill="#C8853A"/>
  <rect x="166" y="42" width="32" height="6" rx="2" fill="#C8853A"/>
  <rect x="198" y="38" width="8" height="14" rx="2" fill="#C8853A"/>
  <circle cx="222" cy="45" r="16" fill="none" stroke="#C8853A" stroke-width="7"/>
  <path d="M74 36 L97 28 L120 50 L143 28 L166 36 L120 68 Z" fill="#C8853A"/>
  <text x="120" y="84" font-family="'Bebas Neue', sans-serif" font-size="12" fill="#C8853A" text-anchor="middle" letter-spacing="5">REVIVAL STRENGTH</text>
</svg>
```

### Design Aesthetic
- Dark, cinematic, premium gym aesthetic
- Heavy use of deep navy/slate backgrounds with gold accents
- Generous whitespace, clean grid layouts
- Subtle radial gradients used for depth (gold glow effects)
- Animations: fade-up on scroll via IntersectionObserver
- Border style: `1px solid rgba(200,133,58,0.15–0.4)` for card outlines
- Border radius: `2–4px` (minimal rounding, sharp/confident feel)

---

## 4. Landing Page Architecture (`index.html`)

### Page Sections (in order)

| # | Section | Purpose |
|---|---------|---------|
| 1 | **Fixed Nav** | Logo + nav links + "Apply For Coaching" CTA → offerings page |
| 2 | **Hero** | Two-column: headline + copy left, full-bleed gym photo right |
| 3 | **Marquee Strip** | Gold bar scrolling: Movement · Nutrition · Sleep · Community |
| 4 | **Four Pillars** | 4-column card grid: Nutrition, Movement, Sleep, Community |
| 5 | **About Josh** | Two-column: portrait photo left, bio + quote right |
| 6 | **The System** | 3-step process: Start Small → Build Systems → Compound Gains |
| 7 | **Nutrition Callout** | Real food philosophy + grocery rules |
| 8 | **Testimonials** | 3-card grid with real client reviews |
| 9 | **Final CTA** | "Your Future Self is Waiting" + Apply For Coaching button |
| 10 | **Footer** | Logo + copyright |
| 11 | **Lead Magnet Popup** | Fires 2.5s after load, email capture for free Blueprint PDF |

### Hero Section Details
- **Left:** Eyebrow label, headline "MASTER *Yourself.*", subheadline, two CTA buttons
- **Right:** Full-bleed photo with gradient overlay (fades left and bottom into page bg)
- **Stats bar** (bottom left overlay): 500+ Lives Transformed · 4 Core Pillars · 100% Real Food

### Lead Magnet Popup
- Fires: 2.5 seconds after page load
- Session storage key: `popupDismissed` — shows once per session
- Left panel: Actual PDF cover image (base64 embedded)
- Right panel: Form with first name + email inputs
- On submit: Shows success state (connect to email platform)
- Closes via: ✕ button, overlay click, Escape key
- **TODO:** Connect form `handlePopupSubmit()` to Mailchimp / ConvertKit / Kit API

### Key CTAs
- **"Apply For Coaching"** → links to `offerings.html`
- **"Start Your Journey"** → links to `offerings.html`
- **"Book a Free Consultation"** → `mailto:` (replace with Calendly link)
- **Popup form submit** → connect to email platform

---

## 5. Offerings Page Architecture (`offerings.html`)

### Page Sections (in order)

| # | Section | Purpose |
|---|---------|---------|
| 1 | **Nav** | Logo + "← Back to Home" + "Apply For Coaching" |
| 2 | **Page Header** | "CHOOSE YOUR *Path Forward.*" + subheadline |
| 3 | **3 Offering Cards** | Side-by-side pricing cards |
| 4 | **How It Works** | 4-step process: Apply → Connect → Build → Execute |
| 5 | **FAQ** | 5 accordion questions |
| 6 | **Final CTA** | "LET'S GET TO *Work.*" + Apply button |
| 7 | **Footer** | Logo + copyright |

### Offerings

#### 1. 1-on-1 Personal Coaching
- **Badge:** Limited Spots
- **Price:** $150 / session
- **Format:** In-person, private 1-on-1, Denver area
- **Commitment:** 12 or 24 session packs
- **Includes:**
  - 1-on-1 sessions with Josh
  - Individualized Programming
  - Real-time coaching & cueing
  - Functional strength focus
  - Nutrition guidance included

#### 2. Remote Coaching *(Most Popular)*
- **Price:** $450 / month
- **Format:** App-based (TrueCoach / Trainerize)
- **Includes:**
  - Individualized programming via coaching app
  - Nutrition coaching & meal guidance
  - Bi-weekly check-ins & progress tracking
  - Direct messaging access to Josh *(Available during normal business hours)*
  - Program adjustments around travel & work
  - Video form reviews

#### 3. The Revival System *(Ultimate Package)*
- **Badge:** Limited Spots
- **Price:** $2,000 / month
- **Commitment:** 6-month commitment
- **Description:** Most elite, all-in offering. Training, nutrition, lifestyle, and mindset — all covered. A complete system designed to revive the best version of you.
- **Includes:**
  - Individualized Programming
  - Personalized real-food eating strategy & meal plan build out
  - Lifestyle Coaching — habit-based approach that lasts
  - Weekly check-ins & progress tracking
  - Program adjustments around travel & work
  - Video form reviews
  - Exclusive Access to Josh

---

## 6. Ideal Customer Profile

### Primary Audience
**Driven professionals, 28–45, who are serious about their health but struggling to make it stick.**

### Demographics
- Age: 28–45
- Location: Denver metro area (in-person) / Anywhere (remote)
- Income: $80K+ household
- Occupation: Professionals, entrepreneurs, executives, creatives
- Gender: All

### Psychographics
- High achievers in their career, want the same results in fitness
- Frustrated with generic programs that don't fit their lifestyle
- Busy — travel frequently, demanding schedules
- Value quality over price — willing to invest in the right coach
- Want to feel strong, energetic, and confident — not just look good
- Respond to education, not just motivation

### Pain Points
- "I know what to do, I just can't stay consistent"
- "Every program I try doesn't fit my schedule"
- "I travel too much to stick to a routine"
- "I don't know if I'm eating right"
- "I've plateaued and don't know how to break through"

### What They Want
- A coach who actually listens and customizes
- A plan that works around their real life
- To feel like themselves again — strong, capable, energized
- Results they can sustain long-term

---

## 7. Lead Magnet

**Name:** The Peak Performance Blueprint
**Author:** Josh Lee, Revival Strength
**Format:** PDF (18 pages)
**Topics Covered:**
- Real food philosophy & grocery guide
- Movement principles & functional fitness
- Sleep optimization tips
- Community & accountability

**Delivery:** Email capture popup → connect to email platform (Mailchimp / ConvertKit / Kit)
**Goal:** Build email list, nurture leads toward coaching application

---

## 8. Social Proof

### Testimonials
| Client | Location | Key Theme |
|--------|----------|-----------|
| Walker B. | Georgia | Josh as educator, not just trainer |
| Dawson B. | Boulder, CO | PRs, first competition win, travel-friendly |
| Deon A. | Boulder, CO | Trains whole family, expert with energy |

---

## 9. Technical Notes for Claude Code

### File Structure
```
revival-strength/
├── index.html          (landing page — rename josh-lee-landing.html)
├── offerings.html      (offerings page — rename josh-lee-offerings.html)
└── assets/             (move photos here when refactoring)
    ├── josh-portrait.jpg
    ├── josh-gym.jpg
    └── blueprint-cover.jpg
```

### Current Implementation
- Pure HTML/CSS/JS — no frameworks
- All images are base64 embedded (refactor to external files for production)
- Fonts loaded via Google Fonts CDN
- Animations via `IntersectionObserver` with `.fade-up` / `.visible` classes
- FAQ accordion: vanilla JS toggle with `max-height` CSS transition
- Popup: session storage to prevent repeat display

### TODOs for Production
- [ ] Replace `mailto:` links with Calendly booking URL
- [ ] Connect popup form to email platform (Mailchimp / ConvertKit API)
- [ ] Extract base64 images to external files in `/assets/`
- [ ] Add meta tags (OG, Twitter card, description) for SEO
- [ ] Add Google Analytics or Plausible tracking
- [ ] Connect Stripe Payment Links to offering CTA buttons
- [ ] Add mobile responsive breakpoints (currently desktop-optimized)
- [ ] Set up custom domain (revivalstrength.com recommended)
- [ ] Host on Netlify, Framer, or Webflow

### Stripe Integration Path
- Create Stripe account at stripe.com
- Use **Stripe Payment Links** (no backend needed)
- Replace "Apply For Coaching" buttons with Stripe Payment Link URLs per offering
- For subscriptions: set up recurring billing in Stripe dashboard

---

## 10. Instagram
**Handle:** @josh.rlee

---

*Document prepared by Claude · Revival Strength Brand Brief · 2026*
