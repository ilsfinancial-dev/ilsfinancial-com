# ILS Financial — Claude Code Build Setup
## Step-by-Step Walkthrough

---

## OVERVIEW

This guide sets up a Claude Code project that has full context of the ILS Financial build at every session, connects the best available design tools, and gives you a repeatable workflow for each build session. Read it once fully before starting.

**What you're building:** A Webflow site, built and managed using Claude Code for all technical work, Google Stitch for visual design references, and Figma MCP (already connected) for component-level design review.

**Time to complete setup:** 2–3 hours. Actual build begins after setup is done.

---

## PHASE 0 — PREREQUISITES

Confirm you have these before starting:

- [ ] Claude Code installed and active (pro/max subscription)
- [ ] Webflow account created (webflow.com — start with CMS plan, ~$23/month)
- [ ] Cloudflare account (already exists per prior conversation)
- [ ] Google account (for Google Stitch access)
- [ ] GitHub account (free)
- [ ] Figma account (MCP already connected in Claude.ai — confirm it works in Claude Code too)
- [ ] Microsoft Bookings or Calendly link for the "Book A Fit Meeting" CTA

---

## PHASE 1 — SET UP THE CLAUDE CODE PROJECT

### Step 1.1 — Create the project directory

On your Mac, open Terminal and run:
```bash
mkdir ~/ils-financial-website
cd ~/ils-financial-website
```

### Step 1.2 — Initialize Git repository
```bash
git init
```

### Step 1.3 — Add your foundation files

Copy these files into `~/ils-financial-website/`:
- `CLAUDE.md` (the project prompt — download from this session)
- `ILS_Schema_GTM_Implementation_v6.md`
- `ILS_STRATEGIC_VISION.md`
- `ILS_Financial_Website_RFP.docx`
- `THD-2026-04-28-Schema-GTM-Platform.md`

Your directory should look like:
```
ils-financial-website/
├── CLAUDE.md
├── ILS_Schema_GTM_Implementation_v6.md
├── ILS_STRATEGIC_VISION.md
├── ILS_Financial_Website_RFP.docx
└── THD-2026-04-28-Schema-GTM-Platform.md
```

### Step 1.4 — Push to GitHub

Go to github.com → New repository → Name it `ils-financial-website` → Private → Create.

Then in Terminal:
```bash
git add .
git commit -m "Initial project setup — foundation files"
git remote add origin https://github.com/[your-username]/ils-financial-website.git
git branch -M main
git push -u origin main
```

**Why GitHub:** Claude Code tracks your project across sessions via the directory. GitHub backs it up and gives you version history. If you ever need to roll back a change, you have it.

### Step 1.5 — Open in Claude Code

In Terminal from the project directory:
```bash
claude
```

Claude Code reads `CLAUDE.md` automatically on startup. Every session starts with full project context — no re-explaining needed.

**First session test:** Type "What is this project?" — Claude Code should give you a summary drawn from CLAUDE.md without you providing any background.

---

## PHASE 2 — SET UP WEBFLOW

### Step 2.1 — Create the Webflow project

1. Log into webflow.com
2. New Project → Blank Site → Name: "ILS Financial"
3. Do NOT use a template — start blank

### Step 2.2 — Configure the design system immediately (before building pages)

In Webflow → Style Manager → set global variables:
- Colors: Navy `#1B2A4A`, Gold `#C9A84C`, Off-white `#F8F8F6`, Text `#1A1A1A`
- Fonts: Add Inter via Google Fonts in Project Settings → Fonts

Ask Claude Code to generate the full CSS variable block for you:
```
Generate the Webflow global CSS variable setup for the ILS Financial design system 
as defined in CLAUDE.md. Output as CSS custom properties I can paste into 
Webflow's Custom CSS field.
```

### Step 2.3 — Install GTM container

1. Webflow → Project Settings → Custom Code
2. `<head>` section: paste the GTM `<head>` snippet
   ```html
   <!-- Google Tag Manager -->
   <script>(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':
   new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0],
   j=d.createElement(s),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src=
   'https://www.googletagmanager.com/gtm.js?id='+i+dl;f.parentBefore(j,f);
   })(window,document,'script','dataLayer','GTM-PBX979GN');</script>
   <!-- End Google Tag Manager -->
   ```
3. `<body>` section: paste the GTM `<body>` noscript snippet
   ```html
   <!-- Google Tag Manager (noscript) -->
   <noscript><iframe src="https://www.googletagmanager.com/ns.html?id=GTM-PBX979GN"
   height="0" width="0" style="display:none;visibility:hidden"></iframe></noscript>
   <!-- End Google Tag Manager (noscript) -->
   ```
4. Save

**Ask Claude Code for exact snippets if needed:** "Give me the exact GTM head and body snippets for container GTM-PBX979GN."

### Step 2.4 — Set up CMS Collections

Before building any pages, create the three CMS Collections (see CLAUDE.md — CMS Structure section).

In Webflow → CMS → Add Collection:

**Collection 1: Insights Articles**
Fields: Name (title), Slug, Short Description (Plain Text), Body (Rich Text), Author (Plain Text), Published Date, ICP Tags (Multi-Reference → ICP Tags collection), Featured Image

**Collection 2: Case Studies**  
Fields: Name, Slug, Short Description, Body (Rich Text), Author, Published Date, ICP Tags, Featured Image

**Collection 3: ICP Tags**
Fields: Name, Slug

After creating collections, add these ICP Tag items:
- Military-to-Airline
- Fractional Aviators
- Senior Military Officers
- Airline Pilots
- Veteran Business Owners

### Step 2.5 — Configure page slugs

For every static page, go to Page Settings and set the slug exactly as shown in the URL map in CLAUDE.md. Do this before adding any content.

**Critical:** Webflow may not support `.htm` extensions natively in slugs for static pages. Test this:
1. Create a test page, set slug to `test-page.htm`
2. Publish to staging
3. Check if the URL resolves as `yoursite.webflow.io/test-page.htm`

If `.htm` doesn't work in Webflow static pages, you have two options:
- Set up 301 redirects from `.htm` URLs to clean slugs (Webflow supports this in Project Settings → Redirects)
- Or export Webflow HTML and host on Cloudflare Pages where you have full URL control

**Bring this question to Claude Code:** "Test whether Webflow supports .htm extensions in page slugs and document the finding."

---

## PHASE 3 — CONNECT DESIGN TOOLS

### Tool A: Google Stitch (Component Generation)

**What it does:** You describe a UI component in natural language, Stitch generates HTML/CSS/React code. Use it to generate design references for ICP page layouts, article card designs, and the sticky nav — then give the output to Claude Code to adapt for ILS Financial's brand.

**Access:** stitch.withgoogle.com (Google account required, free)

**Workflow:**
1. Open Stitch
2. Describe a component: *"A sticky navigation bar with a dark navy background, company logo on the left, navigation links in the center, and a prominent 'Book A Fit Meeting' button on the right. Clean, authoritative, not generic. For a financial planning firm serving military professionals."*
3. Stitch generates code
4. Copy the generated HTML/CSS
5. In Claude Code: *"Here is a Stitch-generated nav component: [paste code]. Adapt this for the ILS Financial design system as defined in CLAUDE.md — apply our exact colors, fonts, and CTA language. Output Webflow-compatible HTML and CSS."*
6. Implement the adapted output in Webflow's custom code or designer

**Best Stitch prompts for this project:**
- Sticky nav with CTA button
- ICP page hero section (typographic, no card-over-image)
- Article card grid (3-column)
- Mid-page CTA section (dark background, single centered button)
- Author attribution bar (small, credentialed, below H1)

### Tool B: Figma MCP (Already Connected)

**What it does:** Claude Code can read your Figma designs directly through the MCP connection. You design in Figma, Claude Code reads the design and generates implementation code.

**Confirm the connection works in Claude Code:**
In Claude Code, type: *"Use the Figma MCP to list my recent Figma files."*
If it returns your files, the connection is live.

**Workflow:**
1. Create a Figma file named "ILS Financial Design System"
2. Design your component (sticky nav, ICP page layout, article card, etc.)
3. In Claude Code: *"Read my Figma file 'ILS Financial Design System' and generate Webflow-compatible HTML and CSS for the [component name] frame. Apply the ILS Financial design system from CLAUDE.md."*
4. Claude Code reads the Figma design and generates implementation code
5. Paste into Webflow

**Why this matters:** Figma gives you precise visual control before code is written. You can iterate the design visually in Figma, then regenerate implementation code without re-explaining the design each time.

**Recommended Figma file structure:**
```
ILS Financial Design System
├── Colors & Typography
├── Components
│   ├── Nav (sticky)
│   ├── Hero — Homepage
│   ├── Hero — ICP Page (typographic)
│   ├── Article Card
│   ├── Mid-Page CTA
│   ├── Author Attribution
│   └── Footer
├── Pages
│   ├── Homepage
│   ├── ICP Page — Mil-to-Airline
│   └── ICP Page — Fractional Aviators
```

### Tool C: Claude Code + Webflow Custom Code (Core Workflow)

For elements Webflow's designer handles natively (layout, sections, typography), use the Webflow designer directly.

For elements that require custom code, use Claude Code:

| Task | Where to use Claude Code |
|------|--------------------------|
| Schema JSON-LD blocks | Write → paste into Webflow Page Settings → Custom Code (per-page head) |
| Custom CSS | Write → paste into Page or Global CSS |
| Sticky nav behavior | Write JS → paste into Webflow Embed block or Custom Code |
| GTM container | Already installed — confirm firing via GTM Preview |
| Mid-page CTA HTML | Write → paste into Webflow Embed block |
| Author attribution component | Write → paste into Embed block or build in Webflow designer |

---

## PHASE 4 — BUILD SEQUENCE

Work through pages in this exact order. Do not start a new page until the current one is approved.

### 4.1 — Design system first (Session 1)
Before any page: sticky nav, typography scale, color system, button styles, article card component. Get these right once. Everything inherits from them.

**Session 1 prompt for Claude Code:**
```
Today we are building the ILS Financial design system before touching any pages.

Tasks in order:
1. Generate the global CSS custom properties for the ILS Financial color and 
   typography system as defined in CLAUDE.md
2. Generate the sticky nav HTML/CSS — navy background, ILS Financial logo left, 
   navigation links center, "Book A Fit Meeting" button right. Fixed position, 
   travels with scroll. Adapts to mobile (hamburger menu).
3. Generate the article card component HTML/CSS — image top, title, 2-line 
   description, "Read More" link. 3-column desktop grid, 1-column mobile.
4. Generate the mid-page CTA section HTML/CSS — dark navy background, 
   one-line question, one centered button linking to:
   https://bookings.cloud.microsoft/bookwithme/user/da262d113e15478f864bbafa2dd484b9%40ilsfinancial.com/meetingtype/lXkSJ1V9HEiEMVma8DNIpg2?anonymous&ismsaljsauthenabled
   Opens in new tab (target="_blank").

Output each as a separate code block. I will implement each in Webflow.
```

### 4.2 — Military-to-Airline page (Sessions 2–3)
This is the #1 priority page. Build it to the highest standard. Everything else follows its template.

**Session 2 prompt:**
```
Today we are building the Military-to-Airline ICP page.
URL slug: /financial-planning-military-to-airline-transition.htm

Tasks:
1. Confirm the slug is set correctly in Webflow before we touch content
2. Set up the page structure: eyebrow + H1 + author attribution + body sections + 
   mid-page CTA + article card cluster
3. I will paste the source content from the live site. Your job is to identify 
   every heading-candidate line and mark it as H1, H2, or H3. Do not rewrite. 
   Identify every inline list and flag it for conversion to <ul><li>.
4. After I approve the heading map, we implement the structured page in Webflow.
```

### 4.3 — Schema for Mil-to-Airline (same session or next)
```
Open ILS_Schema_GTM_Implementation_v6.md.
We are implementing Block 4 — Military-to-Airline schema.
Copy the exact JSON-LD from Block 4 and format it as a Webflow 
Page Settings → Custom Code block for the head section of 
/financial-planning-military-to-airline-transition.htm.
Do not modify the schema. Output the exact <script> block ready to paste.
```

### 4.4 — Fractional Aviators page (Sessions 4–5)
Same workflow as Mil-to-Airline. Reference Block 6 in the schema library.

### 4.5 — How We Work page (Session after ICP pages approved)
```
Today we are building the How We Work page.
URL slug: /how-we-work

This is a process transparency page — not a sales page. 
Structure: eyebrow + H1 + subhead + author attribution + 6-phase 
sequential flow + CTA.

Reference CLAUDE.md — HOW WE WORK PAGE section for the exact 
phase names, deliverable descriptions, and design notes before 
building. Do not deviate from the phase structure or add content 
not specified there.
```

### 4.6 — Remaining ICP pages, static pages, articles
Continue in priority order from CLAUDE.md.

### 4.7 — Pre-launch validation (Final session before DNS)
```
Pre-launch checklist — run through each item:
1. Verify every URL slug against the URL map in CLAUDE.md
2. Test GTM firing on all pages via GTM Preview mode
3. Run Rich Results Test on all 25 pages from the schema library
4. Check mobile layout on all ICP pages
5. Confirm sticky nav appears and "Book A Fit Meeting" is tappable on mobile
6. Confirm mid-page CTA calendar link works on all ICP pages
7. Run Lighthouse on Mil-to-Airline and Fractional pages — target 90+ Performance
8. Generate the 301 redirect map for any URLs that changed
```

---

## PHASE 5 — DOMAIN TRANSFER AND LAUNCH

### Step 5.1 — Request domain release from Broadridge
Email Broadridge support: request domain unlock and EPP/authorization code for ilsfinancial.com. Cite ICANN 5-day requirement. Do this early — Broadridge may be slow.

### Step 5.2 — Transfer to Cloudflare
1. In Cloudflare dashboard → Domain Registration → Transfer
2. Enter EPP code from Broadridge
3. Confirm transfer (5–7 days)

### Step 5.3 — Point DNS to Webflow
In Cloudflare DNS, after transfer completes:
- Add CNAME record: `www` → `proxy-ssl.webflow.com`
- Add A record: `@` (root) → Webflow's IP (get from Webflow publishing settings)
- Webflow handles SSL automatically

### Step 5.4 — Do NOT cancel Broadridge until domain clears
Keep Broadridge active until Cloudflare transfer is confirmed complete and DNS is propagated. Verify the live site loads at ilsfinancial.com via Webflow before cancelling.

---

## REFERENCE: COMMON CLAUDE CODE PROMPTS FOR THIS PROJECT

Save these — use them verbatim to start specific work sessions.

**Schema implementation:**
```
Open ILS_Schema_GTM_Implementation_v6.md.
Implement Block [NUMBER] — [PAGE NAME].
Copy the exact JSON-LD and output it as a ready-to-paste <script type="application/ld+json"> 
block for Webflow's Page Settings → Custom Code head section.
URL for this page: [URL from CLAUDE.md URL map]
Do not modify the schema content.
```

**Content structure audit:**
```
I am pasting the source content from [PAGE NAME].
Review it and:
1. Identify every line that should be H2 or H3 (currently runs as paragraph text)
2. Identify every inline list that should be <ul><li> formatted
3. Output a structured outline showing the heading hierarchy
Do not rewrite any text. Formatting only.
[paste content]
```

**Responsive check:**
```
Review the HTML/CSS we built for [PAGE NAME].
Identify any elements that will break or look wrong on mobile (375px width).
Output specific fixes.
```

**Image placeholder:**
```
We need an image for [LOCATION ON PAGE].
Describe what the ideal image would show, consistent with ILS Financial brand guidelines 
(F/A-18 A/B/C/D legacy variant, no generic stock, no AI military imagery).
Output a brief for Matthew to review and source the image.
Do not select or add an image — flag for approval.
```

---

## TOOLS SUMMARY

| Tool | Purpose | Access | Cost |
|------|---------|--------|------|
| Claude Code | All technical implementation, schema, CSS, JS | claude.ai/code | Included in Pro |
| Webflow | Site builder, CMS, hosting | webflow.com | ~$23–39/month |
| Google Stitch | Component design generation | stitch.withgoogle.com | Free |
| Figma MCP | Design-to-code via connected MCP | Already connected | Free (existing) |
| Cloudflare | DNS, domain registrar | Already have account | ~$10/year (domain) |
| GitHub | Project version control | github.com | Free (private repo) |
| GTM | Tag and schema management | Already built — GTM-PBX979GN | Free |
| Google Rich Results Test | Schema validation | search.google.com/test/rich-results | Free |
| Lighthouse | Performance audit | Built into Chrome DevTools | Free |

---

*This document is a working guide — update it as decisions are made during the build.*
