# ILS Financial — Website Build Project
## Claude Code Project Instructions (CLAUDE.md)
*Load this file at every session start. This is the single source of truth for this build.*

---

## PROJECT IDENTITY

**Firm:** ILS Financial LLC — ilsfinancial.com
**Owner:** Matthew Samson — Marine Corps veteran (20+ years), MBA, CPWA®, Yale Certificate in Wealth Management Theory and Practice, RIA, Nebraska
**What this is:** Shadow build of ilsfinancial.com on Webflow. Content migration is verbatim. Layout and visual presentation are open to improvement. Complete technical backend (schema, GTM, GA4) deploys from a pre-built package — do not design it, implement it.
**Goal:** Top 3 national rankings for military-to-airline and fractional aviator financial planning. 2–5 inbound 90%-sold contacts per month. Not a volume lead gen site.

---

## NON-NEGOTIABLES — READ BEFORE EVERY SESSION

1. **URL slugs are sacred.** Every URL must match exactly, including `.htm` extensions. Do not change a single character. A wrong slug breaks SEO equity that is already generating clients.
2. **Content is verbatim.** Migrate all text exactly as written. Do not rewrite, rephrase, condense, or improve wording unless Matthew explicitly instructs otherwise.
3. **F/A-18 legacy variant only.** A/B/C/D — not the Super Hornet (E/F/G). Matches the logo. Applies to any aviation imagery decisions.
4. **No generic military stock photography.** No posed handshakes, no generic flags, no stock "military transition" imagery.
5. **No AI-generated military imagery** without explicit approval from Matthew.
6. **No gated content.** No email capture, no lead magnet gates, no forms blocking access to any content.
7. **Schema library is v6 — final.** Do not write schema from scratch. Reference ILS_Schema_GTM_Implementation_v6.md for every block. All 25 blocks are complete and validated. Implementation only.
8. **GTM container GTM-PBX979GN is complete.** Install the container snippet in `<head>` and `<body>`. All tags and schema deploy through it. Do not rebuild it.
9. **Content width is sacred on ICP pages.** Do not add sidebars to ICP landing pages. Full-width content column, reading width max ~750px.
10. **Image approval gate.** No image goes live without Matthew approval. Flag image decisions, don't make them.

---

## PLATFORM

- **Target:** Webflow
- **Staging domain:** [set when Webflow project is created — format: ilsfinancial.webflow.io]
- **Production domain:** ilsfinancial.com (transferring from Broadridge → Cloudflare registrar → pointed to Webflow)
- **DNS:** Cloudflare (account exists)
- **Do not touch DNS until staging is fully validated.**

---

## TECHNICAL SPECS — DEPLOY AS-IS

```
GTM Container ID:    GTM-PBX979GN
GA4 Measurement ID:  G-PL68N04MQ7
Schema Library:      ILS_Schema_GTM_Implementation_v6.md (25 blocks, all complete)
Firm CRD:            331725
Individual CRD:      6540931
```

**GTM installation in Webflow:**
- Project Settings → Custom Code → `<head>` section: paste GTM `<head>` snippet
- Project Settings → Custom Code → `<body>` section: paste GTM `<body>` (noscript) snippet
- All schema and analytics tags fire through GTM triggers — do not add individual tags manually

**Schema installation:**
- Each schema block from v6 deploys as a GTM Custom HTML tag
- Tag names, triggers, and JSON-LD blocks are all pre-written in the v6 document
- After GTM publishes: validate all pages at search.google.com/test/rich-results

---

## COMPLETE URL MAP (SACRED)

Preserve every slug exactly. These are the URLs that carry existing SEO equity.

| Page | URL Slug |
|------|----------|
| Homepage | `/` |
| About | `/about` |
| Senior Military Officers | `/financial-planning-for-senior-military-officers.htm` |
| Military-to-Airline | `/financial-planning-military-to-airline-transition.htm` |
| Airline Pilots | `/financial-planning-for-airline-pilots.htm` |
| Fractional Aviators | `/financial-planning-for-fractional-aviators.htm` |
| Compensation and Fees | `/Fees.htm` |
| Briefing Room | `/Briefing-Room.htm` |
| High Income Blind Spots | `/high-income-blind-spots.htm` |
| Allocation vs Design | `/allocation-vs-design.htm` |
| What You Are Paying For | `/what-you-are-paying-for.htm` |
| How to Choose a Financial Advisor | `/how-to-choose-a-financial-advisor.htm` |
| Military Retirement Tax Strategy | `/military-retirement-tax-strategy.htm` |
| Survivor Benefit Plan | `/survivor-benefit-plan.htm` |
| Airline Pilot Career Fragility | `/airline-pilot-career-fragility-risk-planning.htm` |
| Pilot Retirement Plan Stack | `/pilot-retirement-plan-stack-integration.htm` |
| Pay Compression Window | `/military-to-airline-pay-compression-window.htm` |
| Domicile for Fractional Pilots | `/Domicile-for-Fractional-Pilots.htm` |
| NetJets 401k Benefits Guide | `/netjets-401k-benefits-guide-fractional-pilots.htm` |
| Fractional Pilot Variable Income | `/fractional-pilot-variable-income-schedule-volatility.htm` |
| Military Officer Case Studies | `/military-officer-retirement-case-studies.htm` |
| Career Fragility Case Study | `/career-fragility-planning-veteran-airline-pilots.htm` |
| Veteran Business Owner Case Study | `/veteran-business-owner-exit-risk-case-study.htm` |
| 100% P&T Veterans | `/100-Disability.htm` |
| TSP Rollover | `/TSP-Rollover-Decisions-For-Military-Pilots.htm` |
| How We Work | `/how-we-work` |
| Contact | `/contact` |
| Account Access | `/account-access` |

**Webflow slug configuration:** In Webflow, set each page's slug manually in Page Settings. Webflow supports `.htm` extensions — confirm this in slug field. If Webflow strips the extension, test with and without and confirm redirect behavior before launch.

---

## HUB-AND-SPOKE INTERLINKING ARCHITECTURE

ICP pages are hubs. Supporting articles and resource pages are spokes. Every hub links to its spokes via two mechanisms: (1) contextual in-text links within the body, and (2) article card clusters at the bottom. Spokes link back to their hub(s). Cross-hub links connect ICP pages where the audience overlaps.

### Interlinking rules
- Add contextual in-text links wherever a topic has a dedicated page — wrap the relevant phrase, do not add new text
- Do not stack multiple links in the same sentence
- Article cards handle bottom-of-page spoke links — do not duplicate card links as in-text links in the same section
- Cross-hub links belong in the body text, not the card cluster
- How We Work appears as a secondary path near (but not competing with) the mid-page CTA on all ICP pages
- **Every ICP page must link to:** The Briefing Room, the case study most relevant to that ICP's audience, and the other ICP pages that are closely aligned to that audience (see cross-hub map below)
- ICP cross-links use a dedicated "Also from ILS Financial" section below the article card cluster — 4-column grid, not mixed into article cards
- **Briefing Room is always first** in the ICP cross-links section, followed by the aligned ICP pages
- **Military-to-Airline page note:** Opening duplicate paragraphs ("Most officers approaching an airline hire date…" and second "That is where the problems compound.") have been removed per Matthew's instruction. The verbatim-content rule does not protect known source errors.

### Hub: Military-to-Airline (`/financial-planning-military-to-airline-transition.htm`)
**In-text contextual links:**
| Phrase in body | Links to |
|----------------|----------|
| "SBP election" | `/survivor-benefit-plan.htm` ✓ |
| "VA disability compensation" | `/100-Disability.htm` ✓ |
| "Thrift Savings Plan assets" | `/TSP-Rollover-Decisions-For-Military-Pilots.htm` ✓ |
| "Tax layering decisions" | `/military-retirement-tax-strategy.htm` ✓ |
| "Financial Planning for Senior Military Officers" | `/financial-planning-for-senior-military-officers.htm` ✓ |
| "Financial Planning for Airline Pilots" (bottom of body) | `/financial-planning-for-airline-pilots.htm` ✓ |

**Article card cluster spokes:**
- TSP Rollover Decisions ✓
- Career Fragility & Early-Career Risk ✓
- Retirement Plan Stack Integration ✓
- Pay Compression Window ✓
- Career Fragility Case Study (veteran airline pilots) ✓
- Military Retirement Tax Strategy ✓

**ICP cross-links section ("Also from ILS Financial"):**
- Financial Planning for Airline Pilots ✓
- Financial Planning for Fractional Aviators ✓
- Financial Planning for Senior Military Officers ✓
- Briefing Room ✓

---

### Hub: Fractional Aviators (`/financial-planning-for-fractional-aviators.htm`)
**In-text contextual links (when built):**
| Phrase | Links to |
|--------|----------|
| Gateway domicile / domicile decisions | `/Domicile-for-Fractional-Pilots.htm` |
| NetJets 401(k) / fractional 401(k) | `/netjets-401k-benefits-guide-fractional-pilots.htm` |
| Variable income / schedule volatility | `/fractional-pilot-variable-income-schedule-volatility.htm` |
| Transitioning from military | `/financial-planning-military-to-airline-transition.htm` |

**Article card cluster spokes:**
- Domicile for Fractional Pilots
- NetJets 401k Benefits Guide
- Fractional Pilot Variable Income
- Relevant case study (TBD on content review)

**ICP cross-links section:**
- Financial Planning for Military-to-Airline (closely aligned — many fractional pilots are transitioning veterans)
- Financial Planning for Airline Pilots
- Financial Planning for Senior Military Officers
- Briefing Room

---

### Hub: Senior Military Officers (`/financial-planning-for-senior-military-officers.htm`)
**In-text contextual links (when built):**
| Phrase | Links to |
|--------|----------|
| SBP election | `/survivor-benefit-plan.htm` |
| TSP / Thrift Savings Plan | `/TSP-Rollover-Decisions-For-Military-Pilots.htm` |
| Tax strategy / tax sequencing | `/military-retirement-tax-strategy.htm` |
| VA disability / 100% P&T | `/100-Disability.htm` |
| Transitioning to the airlines | `/financial-planning-military-to-airline-transition.htm` |

**Article card cluster spokes:**
- Survivor Benefit Plan
- TSP Rollover Decisions
- Military Retirement Tax Strategy
- Military Officer Case Studies (`/military-officer-retirement-case-studies.htm`)

**ICP cross-links section:**
- Financial Planning for Military-to-Airline (primary next-stage link — many senior officers transition)
- Financial Planning for Airline Pilots
- Financial Planning for Fractional Aviators
- Briefing Room

---

### Hub: Airline Pilots (`/financial-planning-for-airline-pilots.htm`)
**In-text contextual links (when built):**
| Phrase | Links to |
|--------|----------|
| Career fragility / medical risk | `/airline-pilot-career-fragility-risk-planning.htm` |
| Retirement plan / 401(k) stack | `/pilot-retirement-plan-stack-integration.htm` |
| First-year compression / probationary year | `/military-to-airline-pay-compression-window.htm` |
| Transitioning from military | `/financial-planning-military-to-airline-transition.htm` |

**Article card cluster spokes:**
- Career Fragility & Early-Career Risk
- Retirement Plan Stack Integration
- Pay Compression Window
- Career Fragility Case Study (`/career-fragility-planning-veteran-airline-pilots.htm`)

**ICP cross-links section:**
- Financial Planning for Military-to-Airline (many airline pilots are veterans)
- Financial Planning for Fractional Aviators (career path overlap)
- Financial Planning for Senior Military Officers
- Briefing Room

---

### Spoke pages → link back to hub
Every spoke page includes a contextual link back to its primary hub ICP page in the body text — not as a footer note.

---

## DESIGN SYSTEM

### Colors
```
Navy (primary):      #1B2A4A  (Broadridge nav — match or refine slightly darker)
White:               #FFFFFF
Off-white (bg):      #F8F8F6  (subtle warm background for content sections)
Gold accent:         #C9A84C  (use sparingly — call-to-action, credential callouts)
Text primary:        #1A1A1A
Text secondary:      #4A4A4A
Border/divider:      #E0DDD6
```

*Confirm exact hex values against live site before finalizing. The navy should feel authoritative, not corporate-generic.*

### Typography
```
Heading font:     Inter or IBM Plex Sans (clean, modern, authoritative — not serif)
Body font:        Same family, regular weight
Mono/data:        IBM Plex Mono (for any structured data displays)
H1:               36–48px, weight 700
H2:               24–28px, weight 600
H3:               18–20px, weight 600
Body:             16–17px, weight 400, line-height 1.65
Max content width: 750px (ICP pages, articles)
Max site width:    1280px
```

*Avoid: serif fonts, script fonts, anything that reads as "financial advisor template."*

### Spacing
```
Section padding vertical:  80–100px desktop, 48px mobile
Content block gap:          40px
Component gap:              24px
```

---

## UX RULES — NON-NEGOTIABLE

### Sticky Navigation
- Nav is fixed/sticky — travels with scroll on all pages
- "Book A Fit Meeting" button always visible in top-right of nav
- Nav background: navy, slightly transparent with backdrop blur on scroll
- Sticky behavior activates immediately on scroll (not after threshold)
- Mobile: hamburger menu, CTA button preserved below hamburger

### CTA Architecture — ICP Pages
Every ICP page gets:
1. **Sticky nav** (persistent throughout scroll)
2. **Mid-page CTA** — appears after the main content argument, before the article card cluster
   - One line: "Ready to talk through your transition?"
   - One button: "Schedule a Fit Meeting" → direct calendar link (Microsoft Bookings):
     `https://bookings.cloud.microsoft/bookwithme/user/da262d113e15478f864bbafa2dd484b9%40ilsfinancial.com/meetingtype/lXkSJ1V9HEiEMVma8DNIpg2?anonymous&ismsaljsauthenabled`
   - No form. Direct calendar link only. Opens in new tab.
   - Style: contained section, dark background (navy or near-black), single centered CTA
3. **Article cards** below the mid-page CTA

### Booking URL (use everywhere a CTA button appears)
```
https://bookings.cloud.microsoft/bookwithme/user/da262d113e15478f864bbafa2dd484b9%40ilsfinancial.com/meetingtype/lXkSJ1V9HEiEMVma8DNIpg2?anonymous&ismsaljsauthenabled
```
Opens in new tab (`target="_blank"`). Use on: sticky nav button, mid-page CTA, homepage Next Steps section, any page-level CTA. Do not use a contact form anywhere.

### General CTA Rules
- Calendar link everywhere, not contact forms
- One primary action per page — do not stack multiple CTAs
- No popups, no exit-intent overlays, no slide-in widgets
- No persistent chat widgets
- No countdown timers, urgency language, or pressure tactics

---

## CONTENT STRUCTURE RULES FOR ICP PAGES

When migrating ICP page content, apply this structure:

### Heading Hierarchy
All ICP pages currently have subheadings running as plain paragraph text. Apply proper structure:
- `H1`: Page title (e.g., "Financial Planning for Military Pilots Transitioning to the Airlines")
- `H2`: Major sections (e.g., "The Compression Window", "Two Systems. One Transition.", "If You Are Separating Short of 20 Years")
- `H3`: Subsections within major sections

This is formatting the existing text — not rewriting it. Every H2 candidate is already identifiable as a bolded or standalone line in the source content.

### Lists
All inline lists currently run as consecutive paragraph sentences. Convert to proper `<ul><li>` structure:
- Identify any section that begins with an introductory statement followed by sequential items
- Format as bulleted list
- Do not add, remove, or reword list items

### Author Attribution
Every ICP page and article page displays:
```
Matthew Samson, MBA, CPWA® | Marine Corps Veteran | ILS Financial
```
Position: below H1, before body content begins. Style: small, muted — credential signal, not a banner.

### Eyebrow Labels
ICP pages get eyebrow text above the H1:
- Military-to-Airline: `FOR MILITARY PILOTS TRANSITIONING TO THE AIRLINES`
- Fractional Aviators: `FOR NETJETS, FLEXJET, AND OTHER FRACTIONAL PILOTS` (already exists — preserve)
- Senior Military Officers: `FOR SENIOR MILITARY OFFICERS APPROACHING RETIREMENT`
- Airline Pilots: `FOR VETERAN AIRLINE PILOTS IN PEAK EARNING YEARS`

Style: small caps, tracked out, muted navy or gold — not dominant

---

## ICP PAGE PRIORITY ORDER

Build in this sequence. Do not proceed to next until current page is approved.

1. **Military-to-Airline** (`/financial-planning-military-to-airline-transition.htm`) — #1 national niche target
2. **Fractional Aviators** (`/financial-planning-for-fractional-aviators.htm`) — blue ocean, uncontested
3. **Senior Military Officers** (`/financial-planning-for-senior-military-officers.htm`)
4. **Airline Pilots** (`/financial-planning-for-airline-pilots.htm`)
5. **How We Work** (`/how-we-work`) — process transparency page. Build after ICP pages are approved. Links from mid-page CTA area on ICP pages as secondary path for high-intent prospects who want process detail before booking.

---

## ARTICLE CARD CLUSTER (BOTTOM OF ICP PAGES)

Each ICP page has a cluster of supporting article cards below the mid-page CTA. Rules:

- Cards display: title, 1–2 sentence description, link
- Images: aviation/military relevant — flag or cockpit or formation imagery appropriate to ICP. No chess pieces, no compass stock art, no generic meeting photos.
- Layout: 3-column grid desktop, 1-column mobile
- Card CTA text: "Read More" or "Download" (for PDFs) — not "Learn More", "Click Here", "Read More Here"
- All cards link to their respective article pages (full URL from URL map above)

---

## WEBFLOW CMS STRUCTURE

Set up these Collections before building ICP pages:

| Collection | Fields |
|------------|--------|
| Insights Articles | Title, Slug, Description, Body (Rich Text), Author, Date, ICP Tags (multi-ref), Featured Image, Schema Type |
| Case Studies | Title, Slug, Description, Body (Rich Text), Author, Date, ICP Tags, Featured Image |
| ICP Tags | Name, Slug | (reference collection — allows filtering articles by ICP) |

**ICP Tags to create:** Military-to-Airline, Fractional Aviators, Senior Military Officers, Airline Pilots, Veteran Business Owners

All existing Insights articles and case studies migrate into CMS Collections. ICP pages display related articles by filtering on ICP Tag. This builds the internal linking structure automatically.

---

## HOW WE WORK PAGE (`/how-we-work`)

This page communicates the client onboarding process in simplified, client-facing terms. It is not a marketing page — it is a process transparency page. Purpose: a prospect who has read the ICP content and is ready to engage wants to know exactly what happens next. This page answers that question in structured, accountable terms that resonate with the military mindset.

**Do not expose Meridian architecture.** The 6-phase structure below is the client-facing skin. The 46-step internal process map is a Meridian operational document — none of that detail belongs here.

**Page structure:**

- Eyebrow: `THE ILS ONBOARDING PROCESS`
- H1: `A Defined Process. No Guesswork.`
- Subhead (1–2 sentences): Brief framing statement — this is an engineered sequence, not an improvised one. Each phase has a defined deliverable. You always know where you are and what comes next.
- Author attribution: standard (Matthew Samson, MBA, CPWA® | Marine Corps Veteran | ILS Financial)

**6-Phase sequence — display as numbered vertical steps or horizontal stage flow:**

| Phase | Name | Client Deliverable |
|-------|------|--------------------|
| 1 | Fit Meeting | Mutual confirmation this is the right relationship. No commitment required. |
| 2 | Document Preparation | Secure document vault opened. Checklist sent. Data gathered before the first planning meeting. |
| 3 | Strategy Development Meeting | Personal Financial Overview priorities set. Statement of Financial Purpose drafted. Service tier confirmed. |
| 4 | Account Setup and Transfers | Accounts opened. Agreements signed. Transfers initiated. Client updated at every step. |
| 5 | Implementation Meeting | Complete financial plan presented. PFO delivered. All strategies reviewed and confirmed. |
| 6 | Ongoing Service | Review cadence begins based on service tier. You know your next meeting date before you leave the implementation meeting. |

**Design notes:**
- Each phase: phase number (large, gold), phase name (H3), one-sentence deliverable description
- Visual divider between phases — not a checklist, not a bullet list. Sequential flow.
- No sidebar. Full-width reading column, 750px max.
- CTA at bottom of phase sequence (before footer): "Ready to start at Phase 1?" → Book A Fit Meeting button

**What this page is NOT:**
- Not a sales page — no benefit claims, no testimonials, no urgency language
- Not an FAQ — no accordion, no toggle sections
- Not a pricing page — fees are on `/Fees.htm`

---

## HOMEPAGE STRUCTURE

Section order (top to bottom):
1. Sticky nav
2. Hero — F/A-18 image, H1 headline, subhead, "Book A Fit Meeting" CTA
3. Who We Serve — ICP grid (4 cards linking to ICP pages)
4. How We Help — 5 service areas (Transition Planning, Investment Strategy, Retirement/Pension, Tax-Aware, Military Benefits)
5. About Matthew — credential-forward section, Marine Corps background, CPWA, decision sequencing philosophy
6. Additional Resources — ICP quick links + Briefing Room
7. Next Steps — final CTA section
8. Footer

**Hero note:** The F/A-18 image is strong. Use it as a full-bleed background with a dark overlay, H1 and subhead centered or left-aligned over it. The white card floating in front of the current hero is a Broadridge template artifact — eliminate it. Text reads directly over the image.

---

## META TITLES AND DESCRIPTIONS

Do not preserve Broadridge meta titles. Rewrite as follows:

| Page | Meta Title | Meta Description |
|------|------------|------------------|
| Homepage | Financial Planning for Military Officers and Pilots \| ILS Financial | ILS Financial helps retiring military officers, airline pilots, and fractional aviators navigate high-stakes financial transitions with precision. |
| Mil-to-Airline | Financial Planning for Military Pilots Transitioning to Airlines \| ILS Financial | Specialized financial planning for military pilots entering commercial aviation — TSP, SBP, military pension, airline pay compression, and irreversible decision sequencing. |
| Fractional Aviators | Financial Planning for NetJets, Flexjet, and Fractional Pilots \| ILS Financial | Purpose-built financial planning for fractional aviation pilots — variable income, gateway domicile, 401(k) contract specifics, and career transition planning. |
| Senior Military Officers | Financial Planning for Senior Military Officers \| ILS Financial | Planning for O-5 and above approaching military retirement — SBP elections, TSP optimization, TRICARE coordination, and transition decision sequencing. |
| Airline Pilots | Financial Planning for Veteran Airline Pilots \| ILS Financial | Financial planning for veteran airline pilots navigating career fragility, retirement plan complexity, and income planning through peak earnings years. |

*Remove geographic qualifiers (Omaha, NE) from all nationally-targeted pages. ILS serves clients nationally.*

---

## WHAT NOT TO DO

- Do not add sidebars to ICP or article pages
- Do not add pop-up forms, live chat widgets, or exit-intent overlays
- Do not add social proof widgets, review carousels, or testimonial sliders
- Do not add newsletter signup forms or email capture anywhere
- Do not add "You might also like" content recommendation widgets
- Do not change any URL slug
- Do not rewrite any content
- Do not use the Super Hornet (F/A-18 E/F/G) in imagery
- Do not use generic financial advisor stock imagery
- Do not add animations that distract from content (subtle fade-in on scroll is acceptable)
- Do not add a footer CTA that competes with the sticky nav CTA

---

## SESSION STARTUP PROTOCOL

At the start of every session:

1. State which page or component we are working on today
2. Confirm the exact URL slug against the URL map above before touching any page settings
3. If working on schema: open ILS_Schema_GTM_Implementation_v6.md and reference the exact block — do not write new schema
4. If working on a new page type not yet built: confirm the structure with Matthew before starting
5. After any significant change: screenshot and confirm before proceeding

---

## FOUNDATION FILES IN THIS PROJECT

| File | Purpose |
|------|---------|
| CLAUDE.md | This file — session instructions |
| ILS_Schema_GTM_Implementation_v6.md | Complete schema library — 25 blocks, GTM specs, all URLs |
| ILS_STRATEGIC_VISION.md | Firm strategy, ICP definitions, founder background |
| ILS_Financial_Website_RFP.docx | Full technical requirements, brand guidelines, page map |
| THD-2026-04-28-Schema-GTM-Platform.md | Previous thread decisions — platform, schema build status |

## Visual Reference
Quality benchmark: thomaskopelman.com
Reference screenshots in /design-references/ folder.
Key elements to match: monogram treatment, white space 
discipline, typography confidence, cut-out photography, 
minimal nav.
What ILS is NOT: a personal content brand. ILS is a 
technical authority site for a specific professional 
community.
---

*Last updated: May 2026 | Version 1.0*
